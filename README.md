# SoloDev Toolbox 3.6.29


<img width="2463" height="1275" alt="656543751-f2ebf4de-844f-464d-a95d-870940d46d70" src="https://github.com/user-attachments/assets/3176afa1-0bd5-4fe4-9db2-2787c1bc20ff" />
<img width="2324" height="796" alt="{9BD1517C-865A-4E8E-9C9C-A8EE312C8BA9}" src="https://github.com/user-attachments/assets/18d5f553-da65-4adb-855d-f6a2ab6e155d" />
<img width="2313" height="247" alt="{4E77A9DF-C396-4F1A-9F37-24C8D53B78E1}" src="https://github.com/user-attachments/assets/25886e39-9031-435a-8b25-647ef8e35e8c" />

**Plan the game. Then get better at everything it needs.**

SoloDev Toolbox brings together Studio (planning, design, market research and launch), Music, 3DFoundry, 2DCanvas and Story, plus Pocket tools for finishing something in a day. Core tools, reference material and learning guides run offline on your device. The AI writing assistant prepares prompts for any online assistant you choose; paste the response back to edit and use it. There are no ads or telemetry and no account is needed for the core app.

This app is avilable in English, Français, Deutsch, 日本語, 简体中文, Português (Brasil), Русский, Українська, Türkçe, हिन्दी, Italiano, Português (Portugal), Español, ไทย, and 한국어. You can change the language in vault - settings.

Available on Windows,Linux MacOS (ARM and x86) and Android. Download the up to date app and source files on the releases page.

## Release downloads

| File | Platform |
| --- | --- |
| SoloDevToolbox-3.6.29-portable.exe | Windows x64, portable executable |
| SoloDevToolbox-3.6.29.apk | Android 7.0+, signed update, versionCode 105 |
| SoloDevToolbox-3.6.29-source.zip | Web, Electron, Android and port source |
| SoloDevToolbox-3.6.29-linux-x64.tar.gz | Linux x64, portable folder |
| SoloDevToolbox-3.6.29-linux-x64.run | Linux x64, self-extracting launcher|
| SoloDevToolbox-3.6.29-mac-arm64.zip | macOS Apple silicon, standalone app |
| SoloDevToolbox-3.6.29-mac-x64.zip | macOS Intel, standalone app |

The Android, Windows and source releases are in the project root; the retained Linux/macOS 3.6.28 packages sit in their respective PortedApps/*/standalone folders until a Linux/macOS runtime cache is available to rebuild them. Previous releases are retained. Back up your projects in Vault before updating.

## Fixed in 3.6.29

Restoring a written (.json) backup no longer fails with the JSON parser's raw message. An empty or half-written backup file — the case behind the reported "Unexpected end of JSON input" — is now named for what it is: choosing a 0-byte file says "That file is empty — pick a different backup.", pressing Restore with nothing chosen or pasted says "Choose a backup file or paste its text first.", malformed text says it is "not valid JSON", and a valid JSON file that is not a SoloDev Toolbox backup is refused as before. The restore dialog stays open on every one of these, so the reader can pick the right file without reopening it.

Choosing the same file twice now always re-reads it: the file control is cleared after each pick, so a second attempt with the same backup fires the change event again. Reading failures are reported instead of silently doing nothing.

On the desktop app, "Choose file…" now opens the shell's own native open dialog in the Electron main process — the same path the export dialogs already use — instead of the renderer's built-in file control, whose file-chooser pipeline can stop answering on machines where the GPU/utility processes keep crashing. A browser and the Android WebView keep their native file picker. The chosen text still lands in the same editable box, and Restore behaves identically on every platform.

Saving is verified end to end. The desktop shell refuses an export that produced no data before the save dialog even opens, and a save that claims success must leave the whole file on disk: after writing, the byte count is read back and compared, and a short or empty file is removed and reported as a failure instead of being left behind as a damaged "backup". Chunked saves of large zips carry the expected size with them and are checked the same way at the end. The browser/Android save paths are unchanged.

A test-harness bug in the offline locale UI check was also fixed: its screenshot step returned a DOM object over IPC, which failed an otherwise green run. It now exits 0.

Validation for 3.6.29 adds restore-dialog checks to tools/verify.js: the desktop shell picker button (no renderer file control), the empty-restore explanation, malformed JSON and non-backup objects naming their real problem (never the parser's "Unexpected end of JSON input"), the shell picker filling the box, a successful restore closing the dialog and replacing the projects, plus the browser-side path with a 0-byte file, a valid file, and the file control resetting so the same file can be picked again. Save verification is covered by the existing format/dedupe/round-trip and smoke suites.

## Fixed in 3.6.28

Removed the leftover Connect AI button in Language settings and the AI draft button beside the personal/studio name setting. AI drafts remain on project writing and Vault notes.

Scrollbars use a subtle 3-pixel thumb in desktop/Android Chromium. They appear only when their own content scrolls, then disappear 500ms after motion stops. Tracks and corners stay transparent, and arrow buttons are absent. Firefox uses its supported thin scrollbar. Modal scrolling does not reveal a scrollbar on the blurred page behind it. The previous permanently visible thick rail is removed, including the viewer-note exception.

The slim page rail keeps its width during viewer/dialog scroll locks, preventing content reflow and preserving the reader's position.

Dialogs now have an outer rounded frame that clips the inner scroll viewport and its scrollbar. The scrollbar cannot extend below the dialog or past its rounded corners. Long content still scrolls to its final controls, and nested dialogs retain their page lock.

The loading screen is fixed and cannot scroll. Both the splash and underlying document are locked, and the workspace is inert until handover, preventing duplicate scrollbars and accidental background focus. Loading content fits the available viewport and updates after resizing or text/font changes. Compact layouts reduce spacing while keeping the progress, status and Start working button visible. Locks and listeners are removed after handover.

Validation includes five desktop/phone/landscape viewport sizes, loading wheel/key locks and fit, modal frame bounds, transient scrollbar appearance/hiding, final-control reachability and nested dialog locks. Existing manual draft, backup recovery, archive integrity, offline language/guide, renderer and full smoke checks remain included.

## Manual AI writing workflow

AI writing now uses a manual copy-and-paste workflow on every platform. Provider connections, API credentials, OAuth, model settings, automatic generation and desktop AI launch integrations have been removed from the app and distributed source.

1. Open **AI** in the toolbar or **AI draft** beside a field, including character Name, Role and Character arc.
2. Write what you want the assistant to produce. Edit **Project context**, or untick it to leave it out. The read-only **Prompt** shows exactly what will be copied.
3. Press **Copy prompt** and paste it into ChatGPT or any other online assistant yourself.
4. Paste the response into **Generated draft**, directly or with **Paste draft**. Cut, copy, paste and edit normally with keyboard shortcuts or the native text menu. The Paste draft button inserts at the cursor or replaces the selection.
5. **Insert/Replace field** or **Append to field** applies the draft to the field you opened. **Save as quick note** saves the edited draft and its title in Vault → Notes without changing the field. The toolbar assistant saves notes without a field target.

Field insertion protects edits made while the dialog was open and refuses a detached field or changed route. Clipboard permissions denied in a browser fall back to selecting the prompt or focusing the draft for normal keyboard/text-menu editing. A note is reported saved only after storage succeeds; failed saves roll back, and repeated clicks do not create duplicate notes.

Scrollbars are subtle, appear during movement and use the selected theme, with transparent tracks. The blurred page stays locked while a dialog is open, while the active dialog remains scrollable. Backup recovery and strict ZIP/manifest validation from 3.6.25 are retained; damaged IndexedDB storage can use an independent recovery database or OPFS without deleting the originals. Failed imports leave existing project metadata unchanged.

## Writing and offline languages

English plus 14 bundled languages: French, German, Japanese, Simplified Chinese, Brazilian Portuguese, Russian, Ukrainian, Turkish, Hindi, Italian, European Portuguese, Spanish, Thai and Korean. The packs contain 13,225 catalogue entries each, including the new prompt controls. Guides, lessons, templates and descriptions translate offline; user writing and executable code stay unchanged. Translation credits are bundled in app/assets/locales/. Existing translated guide wording may benefit from native-speaker editing.

## Local data

The app makes no AI provider requests and does not manage AI accounts or credentials. Copying a prompt only writes to your clipboard. You choose where to paste and send it. Old local encrypted connection files are no longer read by the app. Project backups contain project data, saved notes and media, excluding former provider credential files.

Project data stays on this device. Use Vault's backup/export tools to move it between devices. Save-as, printing, native fullscreen and the graphics fallback remain available in desktop wrappers.

## Running the releases

Windows: close the existing app, then run the new portable EXE. The desktop app allows one running instance; launching an update while the old version is still open focuses the old window.

Android: install the APK, allowing your file manager to install unknown apps if needed. It uses the existing release certificate and application ID com.solodev.studio so it can update the previous signed APK without changing app data. A device with a differently signed build requires its matching key for an in-place update.

Linux: extract the tar.gz and run "SoloDev Toolbox.sh", or use the single-file launcher:

```sh
chmod +x SoloDevToolbox-3.6.28-linux-x64.run
./SoloDevToolbox-3.6.28-linux-x64.run
```

The .run launcher extracts to a versioned folder under ~/.local/share/solodev-toolbox. The portable folder includes install-desktop-entry.sh for an optional user-level application menu entry. A Linux desktop compatible with Electron 40 and its system libraries is required.

macOS: unzip the archive for your architecture. The app is unsigned and not notarized. Review the bundled first-launch helper before using it: Start SoloDev Toolbox.command removes the quarantine attribute from this app and opens it. You can also use macOS's available Open/Privacy & Security controls for a trusted unsigned app. Once allowed, open SoloDev Toolbox.app normally; it can be moved to Applications. These packages require a macOS version supported by Electron 40 (macOS 12 or later).

Linux and macOS packages were assembled on Windows from the official Electron 40.10.2 runtimes, preserving executable permissions and macOS framework symlinks. Their archive payloads were verified, but native launches on Linux/macOS and physical-device Android testing were not performed during this release.

## Source layout

- app/: canonical vanilla HTML/CSS/JavaScript app; open index.html to run it in a browser.
- desktop-src/: Windows Electron shell, trusted clipboard/text-menu support (editor.js), build settings and tests.
- mobile-src/: Capacitor Android project. www/ and Android public assets mirror app/.
- PortedApps/SoloDevToolbox-ported-linux/: Linux shell and standalone build script.
- PortedApps/SoloDevToolbox-ported-mac/: macOS shell/menu and standalone build script.
- app/assets/locales/: offline language packs, manifest, catalogue and credits.
- app/assets/brand/: editable SVG branding and exported icons.
- pastprompt.txt: current maintainer handover and release notes.

The source ZIP excludes dependencies, generated builds, old release binaries, local SDK paths, credentials, user data and private signing keys. Its Android signing settings use environment variables. The existing private signing key remains in the local project; do not publish it. A fresh signing key produces a separately signed app and cannot update the existing release in place.

## Rebuild

Use Node.js 22+, npm, Python 3.8+ for standalone scripts, and JDK 21 with Android SDK platforms 35/36 and build-tools 35.0.0 for Android. npm install restores dependencies. Keep all platform web copies synchronized with app/ before building.

Windows:

```sh
cd desktop-src
npm install
npm run dist
```

Linux/macOS standalone archives can be assembled on any OS using Python. The scripts download and cache the official Electron runtime on the first run:

```sh
python PortedApps/SoloDevToolbox-ported-linux/tools/make-standalone.py
python PortedApps/SoloDevToolbox-ported-mac/tools/make-standalone.py
```

Outputs go to each port's standalone/ directory. --out DIR and --cache DIR override these locations; the macOS script also accepts --arch arm64 or --arch x64. Native Linux installer targets (AppImage/deb) need a Linux build environment. Signed/notarized macOS DMG releases need macOS and Apple signing credentials.

Android:

```sh
cd mobile-src
npm install
npx cap sync android
cd android
./gradlew assembleRelease
```

On Windows use gradlew.bat. Configure Android's local.properties with sdk.dir pointing at your own SDK, or set ANDROID_HOME. In the source ZIP, set SOLODEV_KEYSTORE to the absolute path to your keystore and set SOLODEV_STORE_PASSWORD, SOLODEV_KEY_ALIAS and SOLODEV_KEY_PASSWORD to sign a release. Without them, Gradle can build an unsigned release or a debug APK. Never commit signing secrets. Increment versionCode for future APK updates; this release uses 105 and versionName 3.6.29.

## Validation

Manual draft tests cover custom prompts/context, clipboard insertion at selection, editable drafts, native cut/copy/paste, persistent Vault notes, duplicate and failed saves, guarded field insertion, themed scrollbars and background scroll locking. A second desktop window is denied clipboard IPC. The renderer suite now also drives the backup restore dialog on both the desktop shell picker and the browser file control (empty text, empty file, malformed JSON, non-backup JSON, successful replace, control reset). Offline locale/guide, backup recovery, malformed archive, renderer regression and full smoke checks also run against isolated data. The locale UI check exits 0 once its screenshot step is done.

```sh
cd desktop-src
npm run test:drafts
npm run test:locales
electron tools/locale-ui-test.js
electron tools/scroll-layout-test.js
electron tools/backup-recovery-test.js
electron tools/archive-integrity-test.js
electron tools/verify.js
npm run smoke
```

On managed Windows hosts Electron tests may require --no-sandbox --disable-gpu --disable-gpu-sandbox --in-process-gpu. Release archive checks compare app/wrapper files with canonical source, Android version/signature metadata, executable modes and macOS symlinks. SHA256SUMS.txt lists release checksums. Native Linux/macOS launches and physical Android-device tests remain outstanding on this Windows host.

The Electron smoke test paints its window off-screen and waits for rendering frames before measuring the reading-position tile, avoiding stale geometry on a never-shown surface.



Viewer opening cancels an in-flight smooth page scroll and corrects its queued compositor frame before the image appears. Automatic scroll anchoring is paused for the viewer and restored on close. tools/viewer-freeze-test.js verifies that the background offset equals the saved reading position.
