# PROMPT v004: Generate a matched firmware and lean SD-card web trainer page for a webMCU-AI row

**What changed since v003:** the page must show the **model input view** (the true, low-resolution input the model actually receives) beside every image the user looks at: webcam capture, live inference, the live ESP32 image, the sample inspector and Review. See "Model input view" in Part B. Everything else is unchanged.

Save this file. In a new chat, attach or paste:
1. This prompt.
2. ONE on-device `firmware.ino`, RAW (the row of the "Complete webMCU-AI table" at github.com/webmcu-ai to build). A truncated firmware means a wrong page.
3. The finished reference pair for vision classification: `index-v005.html` and `firmware-v005.ino`. Copy their structure, patterns, wording and level of polish. Where this prompt and the reference pair disagree, tell me, then follow this prompt. (If the reference pair is not attached, say so and follow this prompt alone.)
4. Only for a motion row: the WebBLE dual-board page (v16) for the phone-motion and multi-source dataset patterns.

---

## Your role

You are helping Jeremy Ellis (webmcu-ai, github.com/webmcu-ai) turn one on-device TinyML firmware for the Seeed XIAO ESP32-S3 (XIAO ML Kit) into a **matched pair**:

- `firmware-vNNN.ino`: the same firmware with a small set of additions (below) that make it work with the web page.
- `index-vNNN.html`: a single-file browser companion that makes **adding data, training, analyzing, cleaning the dataset and debugging the device** easy on a desktop, then writes weights back to the SD card so the device loads them unchanged.

Use the same version number on both files so they pair (for example `index-v001.html` and `firmware-v001.ino`). Never change earlier versions.

Project philosophy: single file, no build step, readable end to end, real backprop and real weights, small enough to fit in a context window. **Lean but capable**: every feature either gets data in, trains, analyzes, cleans, debugs, or gets weights out. Nothing else. Code bloat in the firmware is a cost; count and report the lines you add.

## Truthfulness rules (learned the hard way)

- The firmware is the source of truth. Do not invent behavior it does not have. If the code you were given does not say something you need, say so and ask one question.
- Any sentence in the UI or in comments that says what the firmware does must be true of the firmware file you deliver. (In an earlier version the page said the firmware ignored config.json and it did. The firmware only started reading it when we added that code.)
- Say plainly what you could not test (real hardware, real camera, real microphone, real phone).

---

# PART A: FIRMWARE ADDITIONS

Keep the firmware's structure, naming (`my...` prefix), comment banners and math. Mark every change with a version comment like `// v47:`. Do not "improve" the math. If you find a real bug, report it and fix it only if it is small and clearly a bug.

## A1. Make the layout genuinely configurable at compile time
- Every layout value (input size, filter counts, window length, class count, feature counts) must be a `#define` that the rest of the code derives from. **Hunt for hard-coded numbers that secretly depend on a layout value** (the vision firmware had `f*36` in conv2 that only worked with 4 conv1 filters; replace with a derived `#define`). Also fix initialization constants that repeat such numbers.
- Add `static_assert`s for constraints (for example input size even for a 2x2 pool, output size at least 1).
- Layout and class count stay **compile-time**. Do not convert them to runtime allocation. State this in a comment.
- Compute the exact weight file size in bytes as a `#define`.

## A2. Refuse a wrong-size weights file
- In the weight load function, compare the file size with the expected size. On mismatch print what was found and what this sketch needs, print the sketch layout, close the file, return false, and fall back to random or baked weights.

## A3. Read class labels from `/header/config.json`
- After the SD card mounts, read `/header/config.json` (cap size around 4 KB) with a tiny hand-written parser (no JSON library). Use only the `"classes"` string list, and only when its length equals `NUM_CLASSES`; otherwise keep the compiled labels and print why.
- Compare `input_size` and the filter counts (or the row's equivalents) with the compiled values and print a WARNING on mismatch. Never change layout at runtime.
- Class names become folder names, so the page and the firmware must agree.

## A4. Camera and data-source parity (vision rows)
- Put these at the top as `#define`s with comments: hmirror, vflip, brightness (-2..2), AE level (-2..2), number of warm-up frames to discard. Apply them after camera init with null checks, and check the return value of `esp_camera_init`.
- Goal: images saved by the device look like images captured on the page (orientation and brightness). In the reference pair this meant hmirror on, vflip on, brightness +1, AE level +1. Tell me these values need bench tuning.
- Warn in the header comment when a change makes previously collected SD images incompatible (for example upside down) so they must be recaptured.
- For non-vision rows, do the equivalent for the sensor (sample rate, gain, filters, axis order and sign) so the page and the device see the same data.

## A5. Web Serial debug frames (optional, only when the page asks)
Purpose: let the page see exactly what the device saw and compare the device's answer with the browser's answer for the **same input**.

Protocol (keep it line-based ASCII so the page can mix it with normal monitor text):
- The page sends `D` when it connects and every 5 seconds, and `d` when it disconnects. The firmware sets a flag and remembers `millis()` of the last `D`. If 15 seconds pass without a `D`, it turns itself off. Print "Debug frames ON/OFF" only on state changes.
- **Check the firmware for characters it already uses on serial** and pick different ones if `D` or `d` collide. Handle the heartbeat char in every loop that reads serial (menu, collection, inference). Ignoring it in long training loops is fine.
- One frame is one line that starts with `@F`, single spaces between fields, ending in a newline:
  `@F <kind> <n> <pred> <probs|-> <logits|-> <layout> <input-summary|-> <mapSide> <map base64|-> <payload base64>`
  For vision classification: kind `I` = inference (every 10th inference), `C` = sample just saved, `P` = slow live preview while collecting (about 1 per second). Probabilities and logits are comma lists with 4 decimals. The layout field looks like `64x4x8`. The input summary is the centre pixel of the model input (three floats). The map is the last conv layer, max over filters, scaled 0..255. The payload is the raw camera JPEG.
- Guard everything: only send when the flag is on, the data exists, and `Serial` is connected. Send nothing extra otherwise, so the Arduino IDE monitor behaves as before.
- Base64 without a big buffer: encode 384-byte chunks (a multiple of 3) with `mbedtls_base64_encode` into a **520-byte** buffer (512 characters plus the NUL terminator the function requires), writing each chunk immediately.
- Keep payloads small and the rate low. State the bytes per frame and per second, and note that a UART bridge at 115200 baud is about 100 times slower than native USB.
- Adapt the payload to the modality (see Part D) but keep the `@F` framing so one page parser works for all rows.
- Do not add the full model input tensor to the frame. The page rebuilds the model input view from the payload (see "Model input view").

---

# PART B: WEB PAGE HARD CONSTRAINTS

1. **One file `index-vNNN.html`.** Inline CSS and JS. No external dependencies at all if the firmware's math can be reproduced in plain JS (it can for these rows). Plain JS mirrors the firmware line by line, which also makes activations easy to read for the heatmap.
2. **SD card is the data channel** (plus Web Serial for the monitor and debug frames only). No WebBLE, no WebUSB, no flashing. The user physically moves the card between the ESP32 and the desktop.
3. **Byte-compatible with the firmware:** layer order and sizes, activations including any clipping, initialization, normalization, input resolution and channel order, weight file name, float32 little-endian layout and write order, class ordering, label indexing. If the firmware and this prompt disagree, the firmware wins.
4. **Weight file safety check.** Before loading a `.bin`, compare its size with the size computed from the current layout and refuse on mismatch. In the message, say what the file would fit. If exactly one layout fits, adopt it and log that. Never load a file containing NaN or Infinity.
5. **Layout settings** (only those that are `#define`s in the firmware) get controls in the Train section with sensible ranges, a validity check, and a note that they are compile-time. Show the exact `#define` lines and the `myClassLabels[]` line to paste into the sketch. Changing the layout discards the model in memory (confirm if unsaved) and invalidates cached decoded inputs, but never touches data on the card. **It also redraws every model input view at the new resolution** (see "Model input view"). Do not expose anything the firmware loops hard-code (for example a 3x3 kernel).
6. **config.json.** The page writes `header/config.json` with the class names and layout together with the weights, and offers a "Write config.json only" button. On load it takes class order and layout from it. The firmware reads only the class names (A3).

## Storage model
- Primary: File System Access API, `showDirectoryPicker({mode:'readwrite'})` on the SD card root (desktop Chrome or Edge). Read the firmware's data folders and write weights and config back. Feature-detect it; never assume it on mobile.
- Fallback: a zip round trip. Writer: minimal STORE-method zip with CRC32 and folder entries (so empty class folders survive). Reader: STORE and DEFLATE (via `DecompressionStream('deflate-raw')`), tolerant of a top-level folder, `__MACOSX`, backslashes and data descriptors (read sizes from the central directory).
- Only file extensions the firmware counts are loaded (for example `.jpg` and `.JPG`); report how many other files were ignored.
- **Class order:** `config.json` if present, else sort folder names alphabetically and tell the user to keep numeric prefixes.
- **Never silently overwrite.** Auto-save is off. On an explicit Save, copy any existing weights file to a `.bak` next to it first. Delete and remove-class actions always confirm. Warn on tab close while a trained model is unsaved.
- **Do not add a Web Share button.** It failed with a permission error because building a large zip outlasts the click's transient user activation. A normal download link is enough.

## Preprocessing parity (the top cause of "trains fine, infers badly")
- Reproduce the firmware's exact decode and resample path. For vision: decode the 240x240 JPEG, then nearest-pixel sampling at `src = floor((i + 0.5) * 240 / N)` (clamped), RGB order, scaled to 0..1, using `getImageData` and manual indexing. Never use smoothed `drawImage` downscaling for model input.
- Webcam frames used for capture or live inference must be processed like the device: square centre crop, 240x240, mirrored and flipped as the firmware configures the sensor (make hmirror a checkbox defaulting to the firmware's setting), **encoded to JPEG and decoded again** so live frames take the same path as stored images.
- Sound and motion: reproduce the firmware's windowing, sample rate, feature extraction and normalization exactly, read from the code.
- Calibration or baseline constants: if the firmware uses any, compute them the same way, store them where the firmware expects them, and warn loudly when they are missing. (Lesson from the WebBLE page: browser-trained models did not work on-device until the baseline matched.)

## Model input view (see what the model sees)
Purpose: the page works with full-size images (for vision, 240x240) but the model only receives the low-resolution input (for example 64x64). Data problems (thin features that vanish, a subject that is too small, bad framing, wrong brightness, a bad crop) become obvious when the user sees the **true training resolution**. So wherever the user looks at an image or live signal the model will consume, also show what the model actually gets, small, right beside it, for reference.

Where it appears:
1. **Capture:** beside the webcam image in the Classes and data section.
2. **Live inference:** beside the live webcam image (next to the heatmap) in the Infer section.
3. **Device view:** beside the live ESP32 image in the Serial monitor section.
4. **Sample inspector and Review viewer:** beside the large sample, plus a **"Show at model resolution"** toggle that replaces the large image with the model input itself, pixel exact and full size (default off). The heatmap overlay must still line up when it is on. Show a size readout such as `64x64` in both states.

How it is produced:
- Build it with **exactly the same function** that builds the training and inference tensors (decode, centre crop, JPEG round trip for live frames, nearest-pixel resample, channel order). Never make a separate smoothed downscale just for display. Convert the tensor back to 8-bit only for painting.
- Show it **pixel exact**: `image-rendering: pixelated`, an integer upscale (for example 2x to 4x, small enough to sit beside the image), no smoothing, with a caption such as `model input 64x64x3 (what the model sees)`. If the model uses fewer channels than the display (for example grayscale), show what the model gets.
- It updates with its source: every processed live frame, a throttled few frames per second for the capture preview (using the same pipeline, including the JPEG round trip), and on every sample or frame the user opens.
- **It follows the layout.** When the layout settings change (for example INPUT_SIZE), every model input view and cached input is rebuilt at the new resolution immediately, and the captions update. A stale view at the old resolution is a bug.
- **Device view:** the firmware only sends the JPEG and the centre pixel (A5). The page builds the model input from the received JPEG with the same function and labels it "rebuilt by the page from the device JPEG". Browser and device JPEG decoders differ slightly, so say this is a close reference, not a bit-exact copy of the device tensor. The existing centre-pixel comparison tells the user how close it is.
- Keep it lean: a small canvas and a caption per place, one shared drawing helper, no extra controls except the "Show at model resolution" toggle.

## Training loop
- Port the forward and backward passes, optimizer settings and default hyperparameters exactly, including quirks (for example gradients summed over the batch rather than averaged, tie handling in max-pool backward, weight clipping, `clip_value` on activations, the firmware's epsilon chosen for float32). Store weights and optimizer state in `Float32Array` to mimic float32.
- Expose learning rate, batch size and epochs. Also expose **training-only** knobs that do not change the layout (dropout on the flattened layer, augmentation), clearly labeled browser-only.
- **Numerical safety from the start:** treat non-finite gradients as 0, bound every single weight update (0.05 worked), detect a non-finite loss and roll back to the last good epoch snapshot with the learning rate halved (give up after 5 rollbacks), and never save a model with NaN or Infinity.
- Yield to the UI between batches with a `MessageChannel` tick (not `setTimeout`, which clamps to 4 ms). Provide Pause, Resume and STOP. STOP keeps the current model in memory and does not save.
- Validation: mirror the firmware's rule exactly (for example sort by path and hold out the last N per class), and offer "percent of smallest class" as an alternative that always leaves at least one training sample. Show the train/validation counts per class. Warn when a class has no training samples left.
- Risks to say out loud in the UI: near-duplicate burst samples inflate validation accuracy; mixed sources (browser file names versus device file names) can make the "last N by name" hold-out come from one source only.

## Analysis features
1. Live training charts: loss, train accuracy, validation accuracy per epoch.
2. Confusion matrix (counts, diagonal highlighted), computed when training ends and on an Update button, on the validation set or on all samples (all samples finds bad labels).
3. Per-class precision, recall and sample count, with warnings for imbalance (more than 3x) and very few samples (under 10).
4. Activation heatmap of the last conv layer (blue low, red high, max or mean over filters, overlay toggle) for live input and any clicked sample. Use the modality's analogue for other rows (see Part D).
5. Misclassified gallery: click opens an inspector with the large sample, probabilities and heatmap, the model input view with its "Show at model resolution" toggle, and Delete and Move-to-class buttons.
6. Sample browser: collapsible per class, click opens the same inspector.
7. **Review mode:** step through one class at a time in a large viewer (with the model input view and the same toggle); arrow keys move; **X marks a sample as bad and advances**; marking deletes nothing; one "Delete marked (n)" button asks for a single confirmation and lists per-class counts; "Suspicious first" sorts by the lowest probability of the true class when a model exists; show the model's prediction beside each sample.
8. **Parity self-test:** prints the current model's probabilities and raw logits (and the model input summary) for a chosen sample in the firmware's serial format, so it can be compared with the device.
9. Model info: architecture text built from the current layout, parameter count, weight file size, and whether the loaded file matched.

## Data capture (use the modality's natural input)
- Vision: webcam capture button (Space) and **Burst 10 (B)**: the button turns red and shows the count while capturing, the video gets a red REC badge and a flash on each frame, then the samples are saved. A millisecond delay input (default 0) sits beside the button; each frame waits for a fresh camera frame (`requestVideoFrameCallback` with a timeout fallback) so 0 ms does not produce duplicates. Write straight into the SD layout. The model input view sits beside the webcam image.
- Sound: microphone at the firmware's sample rate and window, with a clear recording indicator and countdown only if the firmware's collection does the same.
- Motion: phone `DeviceMotionEvent` (see Part D).

## Page layout (sections in this order, nothing else)
Dark theme, big tap targets, desktop-first, system fonts, no external assets.
1. **Data source:** Pick SD folder, Load .zip, a summary of what was found (classes, counts, weights file result, config present, files ignored).
2. **Classes and data:** class table with images and train/validation counts, add and remove class (confirm), the firmware lines to paste, capture (single and burst) with the **model input view beside the webcam image**, Review images, sample browser.
3. **Train:** model layout, training settings, Train, Pause, STOP, status line, charts.
4. **Analyze:** model info, evaluation set choice, Update evaluation, Parity self-test, confusion matrix, per-class table and warnings, misclassified gallery.
5. **Infer (live):** live prediction banner with per-class bars, the heatmap next to the live view, and the **model input view next to the live view**.
6. **Save:** weights to `header/` (with `.bak`), Write config.json only, Save .zip (with an "include images" checkbox).
7. **Console:** one read-only textarea log.
8. **Serial monitor (Web Serial):** Connect and Disconnect at 115200 baud (the firmware's rate), a read-only output area, one text box and a Send button (a newline is appended; Enter also sends). One checkbox, on by default, asks the device for debug frames. A **Device view** shows the latest frame with the **model input view beside the live ESP32 image**, the device's answer and, when a model with the same layout is in memory, runs the same input through the page's network and reports the largest probability difference and whether the *inputs* differ (preprocessing) or the *weights* differ. No flashing, no file browser, no other serial features. Explain in the UI: close the Arduino IDE monitor first, opening the port can reboot the board, Chrome or Edge only.

Serial parsing rules: buffer text; lines that begin with `@` and end with a newline are frames and are not shown in the monitor; everything else is shown; hold a partial line back only if it starts with `@`; never let one bad frame break the monitor; revoke old object URLs.

## Remove or never add
esptool flashing, ESP32 SD browser, camera streaming, TFJS model save/load, source editors, IndexedDB, localStorage or sessionStorage for user data, per-version changelog inside the page (put the version and a two-line description in the title and header), Web Share, anything not asked for.

---

# PART C: CODE STRUCTURE AND TESTING (do this before delivering)

Structure the page script so the math is testable: put everything that has no DOM use (layout, forward, backward, Adam, weight (de)serialization, resampling, split, training driver, zip writer and reader) between `/* ==CORE START== */` and `/* ==CORE END== */` markers, and the UI below it. Put the firmware's new helper code (config parser, debug sender) between marker comments too (for example `// ==CFG PARSE START==`).

Then actually run these checks and report the results:
1. `node --check` on the extracted page script.
2. Every `$('id')` used in the script exists as an `id=` in the HTML.
3. In Node: finite-difference **gradient check** of the ported backward pass at three different layouts (small epsilon, 1e-3; report the worst relative error per parameter group and explain any outliers such as ReLU or pooling kinks); a **synthetic-data training run** at two layouts that reaches high accuracy; weight serialize/parse round trip and file size; **zip round trip** including folder entries.
4. Unit test the serial frame parser by feeding a frame split across arbitrary chunk boundaries, mixed with normal text and CRLF.
5. Compile the firmware helper code (config parser, debug sender) with `g++` against a small Arduino mock, including a mock of `mbedtls_base64_encode` that enforces the output-length rule, and decode the produced frame in Python to confirm the JPEG round-trips byte for byte and the field count matches what the page expects.
6. **Model input view:** keep the helper that builds the view in the CORE section and test in Node that (a) it returns exactly the same values as the tensor used for training and inference for the same source image, (b) its dimensions follow the layout at three different layouts, and (c) the nearest-pixel indices match the firmware formula. In the UI check, confirm that a layout change redraws every place the view appears.
7. State clearly that hardware, camera, microphone and phone behavior were not tested.

---

# PART D: MODALITY NOTES (adapt to the row you were given)

For every modality the **model input view** (Part B) shows the model's true input, not the raw source: for vision the low-resolution image; for the others the analogue below. It sits beside the raw view in the same places.

**Vision classification** is the reference pair. Follow it.

**Vision regression:** labels are numeric (one or more values per image). Follow the firmware's label convention (file name, sidecar file or folder); if it has none, ask. The page needs a way to enter or edit the value per sample (in the sample inspector and while capturing). Replace the confusion matrix with predicted-versus-true scatter, MAE and RMSE per output, and a residual gallery of the worst errors; Review mode sorts by error. Heatmap as in classification. Debug frame: predicted values instead of probabilities.

**Vision FOMO (object centroids):** reproduce the firmware's output grid, cell-to-image mapping and label format exactly. The page needs a labeling tool (click to place a centroid or drag a box, per class) that writes labels in the firmware's format next to each image. Analysis: per-cell activation grid per class overlaid on the image, precision and recall by centroid matching with a stated distance rule, and a gallery of images with missed or false detections. Debug frame: the output grid (per class, 0..255) plus the JPEG. The model input view also shows the output grid size next to the input size, so the cell-to-pixel mapping is visible.

**Sound / wake word:** desktop microphone. Reproduce window length, sample rate, framing, FFT or MFCC code and normalization from the firmware line by line, and store audio in the firmware's format. Replace the image heatmap with the spectrogram or feature window shown for the live input and any clicked sample. Include a background-noise class if the firmware has one. Debug frame: the raw window (base64 int16) plus the feature matrix summary and probabilities, so the page can recompute the features and compare them with the device's before comparing the network output. The model input view is the feature matrix at its true size (frames x coefficients), pixel exact, beside the waveform or spectrogram.

**Motion (X, Y, Z) and motion anomaly, using the cell phone IMU:** the phone mainly collects. Use `DeviceMotionEvent` (request permission on iOS; works in mobile Safari) at the firmware's sample rate and window. If the firmware expects channels or units a phone lacks or reports differently (gravity, sign, axis order, scale), convert or zero-fill exactly as the firmware and training expect, and say so in the UI. Tag each sample with its source (phone or device) and time. Workflow: phone collects, **Save .zip as a normal download** (no Share button), the desktop page imports the zip, trains and analyzes, exports weights, and the weights or zip return to the phone or the SD card. The phone page can also run live inference from a loaded weights file. Do not depend on an SD card being attached to the phone. Calibration baseline rules from Part B apply. Analysis: per-axis window plot for any clicked sample instead of a heatmap; confusion matrix as usual. The model input view is the window exactly as the network receives it (axis order, units, normalization applied, true window length), drawn small beside the raw plot.

**Anomaly rows (vision or motion):** show the score distribution and a threshold control instead of a confusion matrix.

**Vision + sound (dual core):** one page, both pipelines sharing one data source, with the weight layout the firmware defines; keep the two model sections separate and small. Each pipeline gets its own model input view.

---

# OUTPUT FORMAT

1. **Before writing code**, list in a few lines what you read from the firmware: input shape, layers, weight file name and total float count, class handling, hyperparameter defaults, preprocessing, normalization, serial characters already in use, hard-coded numbers that block layout changes, and anything missing or ambiguous. Ask at most one question if you must; otherwise proceed.
2. Deliver **both complete files** (`firmware-vNNN.ino` and `index-vNNN.html`) as files, not snippets, and present them.
3. A short **firmware change list** (each edit and why, with the number of lines added) so I can diff it against the original.
4. The test results from Part C.
5. A short **hardware verification checklist**: flash and read the serial layout line; capture a sample on the device and on the page and compare orientation and brightness; **compare the page's model input view with what you expect the device to see, then change the layout and confirm every model input view redraws at the new size**; load a real SD card and confirm class and sample counts; train, read the confusion matrix and clean with Review; save weights; put the card back and confirm the device log says the weights loaded; open the Serial monitor, tick debug frames, run inference on the device and compare device and page probabilities in the Device view; then retry with a deliberately wrong class count to see the refusal message.
6. Name the version in both file headers and keep earlier versions untouched.

## Do not

- Add features that were not asked for, or "improve" the firmware's math.
- Guess at firmware details that are not in the code provided.
- Convert compile-time layout to runtime allocation.
- Leave TODOs or placeholder functions in the delivered files.
- Claim anything about the firmware, the browser or the hardware that you did not verify in the code or by running a test.
