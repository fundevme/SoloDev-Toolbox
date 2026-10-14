# SoloDev Toolbox 4.5.0
<img width="2451" height="1425" alt="{105A0AA0-7A45-449A-A1C4-6C08609FC9BF}" src="https://github.com/user-attachments/assets/5feab7e3-1ff1-47cb-b76d-b9ebc574a0fb" />
<img width="2366" height="1239" alt="{03F419F4-48D0-48E8-A685-C4A3370B86E0}" src="https://github.com/user-attachments/assets/1cd028a3-6b6e-405c-8288-89a333878e05" />
<img width="2468" height="811" alt="{A204830D-CD67-409D-BD4A-E49817430B76}" src="https://github.com/user-attachments/assets/3043f2bb-a23a-4ed3-8558-d59569415b0a" />

**An offline creative workspace for planning a game and learning the skills to finish it.**

SoloDev Toolbox brings together Studio (planning, design, market research and launch), Music, 3DFoundry, 2DCanvas and Story, plus Pocket tools for finishing something in a day. Core tools, reference material and learning guides run offline on your device. The AI writing assistant prepares prompts for any online assistant you choose; paste the response back to edit and use it. There are no ads or telemetry and no account is needed for the core app.

This app is avilable in English, Français, Deutsch, 日本語, 简体中文, Português (Brasil), Русский, Українська, Türkçe, हिन्दी, Italiano, Português (Portugal), Español, ไทย, and 한국어. You can change the language in vault - settings.

Available on Windows,Linux MacOS (ARM and x86) and Android. Download the up to date app and source files on the releases page.


## Faster everyday access — 4.5.0

Studio Jump in now includes Learn, Saved lessons and Practice queue. Music, 3DFoundry, 2DCanvas and Story have matching cards in Go straight there, with saved lessons and queues filtered to that tool. These shortcuts also appear on a new Studio profile before a project exists. Every Pocket session home includes Learn, Saved lessons, Practice queue, Session brief, its calculator and Review journal, plus cards for all five main tools and all five Pocket tools. Existing Production links and the cover tool switcher remain available.

Startup reveals Start working as soon as real boot work completes after a short 200 ms minimum. The existing loading and page animations, tool hover/press effects, themes, media, offline operation and v2 storage remain in place. Scripts defer until HTML is parsed. Tool switching presents its page before the optional recent-tools write; pending preferences flush before edits, navigation, backup/export and page exit. Failed preference writes restore the previous state.

Translated incremental updates process only changed regions. Translation caches and diagnostic samples are bounded, previous-language compiled caches are released, and small translated updates no longer rescan the whole document. Sidebar elements are reused when their contents are unchanged. Pocket timer listeners, practice painters and day-plan intervals release discarded pages immediately while running timers continue. Idle rhythm playback suspends its audio context. Desktop/browser viewport polling is removed; Android retains a background-aware fallback.

The bug sweep also makes Home actions native keyboard controls, adds visible card focus and touch handling, restores the previous language after a failed settings write, and makes the requested shortcuts available without a project. No existing tool or animation has been removed. See `docs/UI-4.5-VERIFICATION.md` and `release-validation.json` for measured performance, checks and remaining native-testing limits.

The release includes Windows setup/portable, Android APK, Linux x64 tar.gz/.run, Apple silicon/Intel macOS ZIPs and the complete source ZIP. Android retains `com.solodev.studio`, the signing identity and the v2 storage schema, with versionCode **113**. Older named release packages are removed after package and runtime verification.

## Learning, practice and responsive cover — 4.4.0

The cover's six main tools are single clickable tiles with no smaller buttons inside. Mouse hover lifts each tile and animates its mark; Studio has the stronger response. Keyboard focus and touch/press states are visible, and system/app reduced-motion settings suppress the motion. Favourites are managed from a separate cover control, and the favourites/recent list refreshes immediately.

Studio Learn removes the guide-position dropdown while keeping all four guide choices above the reading. Save individual guide sections or creative-tool lesson sections to Saved lessons. Open a saved entry directly at the matching lesson, filter by tool, remove bookmarks or export the list as Markdown.

Practice queue collects lesson sections and individual exercises. Reorder them, keep saved practice notes, open the exact lesson or its Pocket timer, mark exercises done or reopen them, and export the queue. Completing a queued exercise updates the existing tool's exercise progress. Completed items can be shown or hidden. Bookmarks and queue data are additive `settings.learningDesk` in the existing v2 store, survive restart and JSON/full-ZIP backups, and preserve unreadable optional data for recovery. Lists are bounded at 500 saved lessons and 200 practice entries.

The bug sweep fixes failed-save rollback for lesson exercise completion, stale cover favourites, and module section URLs that previously ignored the requested lesson. Queue/order/progress writes also roll back on failure. New UI text is bundled in all fourteen non-English packs; translations remain drafts needing native-speaker review.

Windows setup/portable, Android, Linux, macOS and source packages are rebuilt as 4.4.0. Android versionCode is **112**, using the existing application identity and certificate. Old release packages are removed only after the new packages pass parity, integrity and runtime checks. See `docs/UI-4.4-VERIFICATION.md`, `release-validation.json` and `cleanup-report.json` for actual results and native-testing limits.

## Production tools and Learn layout — 4.3.0

Studio Learn removes the project picker, project filters and learning-path search strip. The practical cards, including First playable prototype and 3D modelling fundamentals, follow the written guides at the bottom. Guide navigation stays above the reading; its former layout selector was removed in 4.4.0. Music, 3DFoundry, 2DCanvas and Story keep lesson navigation beside the reading on wide screens and above it on compact screens, with an independently scrolling lesson list. The lesson-position dropdown is removed; selecting a lesson retains the list position. Their practical introductions follow the curriculum. Header buttons keep their full borders on hover, and keyboard focus remains visible inside the compact controls.

Each main creative tool now has a saved production desk: Studio capacity and contingency, 2DCanvas image sizing and memory, Music beat/bar/delay timing, 3DFoundry texture memory with mipmaps, and Story reading time and scene pacing. Desks include editable deliverable briefs, review checks and Markdown export. Market has a player research brief, Marketing has a launch budget scenario desk, Toolbox/Build have an asset naming and manifest desk, and Vault has a written-data/media inventory. Studio Home includes Production planner, Player research brief, Launch budget desk and Asset naming desk in Jump in. All four creative tool homes and all five Pocket homes include their production shortcuts. Existing workflows link to the relevant tools. Project navigation stays in one scrolling column without clipped labels, Scope totals have separate labels and values, and Scope inputs reject invalid ranges and restore the previous field on failed saves.

All five Pocket tools have three extra pages: Session brief, a tool-specific calculator, and Review journal. Briefs, checks, calculator values and unfinished review drafts survive navigation and restart. Journals retain the latest 100 entries and export Markdown. Asset names handle reserved Windows names, invalid filename characters and case-insensitive collisions without renaming source files. Blank/out-of-range inputs show feedback; failed saves restore stored values and checklist/layout controls. Unreadable optional tool data is preserved and offers backup recovery.

The new desks use additive `settings.v43` under the existing v2 storage schema. Desktop `SoloDevStudio` data and Android `com.solodev.studio` identities remain unchanged. Android versionCode is **111**. See `docs/UI-4.3-VERIFICATION.md` and `release-validation.json` for release checks and native-testing limits. New offline translations are machine drafts requiring human review.

## Familiar homes and focused workspaces — 4.2.0

Studio Home again opens with the greeting, project continuation and practice cards. The expanded Project page contains Today, Tasks, Scope, Playtests, Decisions, Assets, Connections, Release, Accessibility, Game jam, Presentation and Organisation. The game-jam desk adds a playable goal, rules, credits, submission link, deadline status and a saved five-step submission checklist. Repeatedly adding the jam workflow does not duplicate tasks.

The composition lab, rhythm desk, blockout workshop and Story writing desk now have dedicated pages under each tool’s navigation. Home pages retain learning progress, practice, designs and links to every tool. Each desk has its own illustrated introduction and return links. Story removes Lite/Full throughout its writing desk and keeps scene goals and turns available, with live word/character counts. Studio Home and Learn have no Lite/Full selector.

The cover restores “What are you making today?” and the familiar colourful tool cards, including project/exercise facts, while retaining search, project continuation, favourites, recent tools, backups, settings, the tour, Pocket tools and direct links to the new desks. Logos and workflow illustrations use the warm app palette. Composition and rhythm illustrations load locally, idle “Ready to explore” text and redundant library headings are removed, and the guide reads “Your playable game”. Selecting a learning section returns to the top while ordinary refreshes preserve the reading position.

Compact windows use the drawer without the bottom navigation strip. The top header keeps one row whenever its actual translated content fits; it adds an action row only when necessary, and returns to one row after a resize or language change. All 15 languages were checked at five viewport widths. The sweep also fixes small-text contrast and the selected Project-tab colours in dark mode.

See `docs/UI-4.2-VERIFICATION.md` and `release-validation.json` for checks and remaining native testing. Existing v2 data and desktop/Android application identities are preserved. Android versionCode is **110**. Cloud and integrated AI features remain deferred; manual AI drafting is retained.

## UI and bug-fix release — 4.1.1

The 3.6.30 logos, warm themes and typography are restored while keeping the local suite features. Tool banners/modes stay on home pages; existing tools are visible; Vault is beside AI; the compact header places the bold page label beside the active tool name on one row. Version labels, project-filter context, refresh scrolling, malformed preferences and repeated translations are fixed. See docs/UI-4.1.1-VERIFICATION.md and release-validation.json for actual results and untested native/manual work. Android versionCode is 109.

## Local suite upgrade — 4.1.0

The current source now opens 2DCanvas into a live composition study with PNG export, and Music into an audible sixteen-step drum desk with WAV export. Each has a distinct working layout, remembered Lite/Full visibility, illustrated practical activities and inspectable examples. Existing lessons, designs, practice, references, song maps and tools remain reachable. Mode switches keep editing nodes, notes and advanced settings intact. Saved studies use additive `modules.canvas.workspace` / `modules.music.workspace` metadata under the existing v2 storage key.

See `docs/NEXT-STAGE-PILOTS.md` for the framework comparison, actual checks and remaining work. Run `npm run test:workspaces` in `desktop-src`; `node tools/workspaces-browser-test.js` checks installed Chrome and Edge. All tests use isolated profiles.

The 4.1.0 release includes the Studio, 3DFoundry, Story and Learn redesigns, the local handoff feature backlog, all fourteen offline non-English packs, and fresh Windows setup/portable, Android, Linux and macOS packages. See docs/SUITE-4.1-VERIFICATION.md for the actual evidence and remaining native/manual checks. New translations are machine drafts and require native-speaker review. Cloud sync, collaboration and integrated AI are deferred by user choice.

Version 4 brings a new workspace hub, a consistent design across Studio, Music, 3DFoundry, 2DCanvas, Story, Pocket tools and Vault, guided project creation, searchable tools and project content, and clearer access to advanced features.

## What changed

- A new identity, scalable section icons, local workflow illustrations, readable Paper/Light/Dark themes, consistent controls and restrained transitions.
- A workspace hub with direct project continuation, all creative tools, favourites, recent tools, backups and settings.
- Project creation starts with a working title and optional notes. Choose a two-week prototype, short story game, one-day game or blank project. Price (including free), production category, duration, codename and target month remain under Advanced options.
- Starter projects create editable tasks and real milestones. Blank projects remain empty. Creation opens the saved project and only reports success after persistence succeeds.
- Studio Home adds a guide to pitch, core loop, character and first milestone, an overview and quick task/milestone creation. Existing practice tracking, hours, ideas and planning remain available.
- Search tools, projects, tasks, milestones, characters, design concepts and Vault notes. Open character/design results directly in the relevant document section. Filter results, use arrow keys, or search in your selected language. Results are capped at 50 for responsiveness.
- Ctrl/Cmd+K opens search; Ctrl/Cmd+Shift+N opens a project. Both respect active dialogs and busy operations. The tour can be skipped and replayed at any time.
- Project-list search and active-project filtering. Core design sections appear first; further sections remain under Advanced options. Calculator assumptions are expandable in Settings.
- Accessible form labels, keyboard cards/checks, named dialogs, focus containment, visible focus, larger controls and a readable two-row mobile hours chart. Motion follows the system preference. Browser zoom is enabled.
- Save status acknowledges actual writes. A failed debounced save cannot be followed by a success toast. Pending field edits are flushed before navigation/export/page exit. Failed new operations roll back.
- Unreadable saved metadata is preserved and protected against automatic writes or media pruning until explicit restoration or reset. Valid existing projects use the same storage key and v2 data schema; application version 4.0.0 does not require a schema migration.

No useful tool was removed. Advanced GDD sections, calculators, build tools, practice desks, timers, learning resources, media boards, printing, imports and exports remain available. AI drafting keeps the manual copy/paste workflow. There is no account requirement, analytics, advertisement, new cloud dependency or AI API integration.

## Languages and local assets

English plus French, German, Japanese, Simplified Chinese, Brazilian Portuguese, Russian, Ukrainian, Turkish, Hindi, Italian, European Portuguese, Spanish, Thai and Korean remain bundled offline. New text uses the existing catalogue. Native-speaker review remains outstanding; automated checks establish coverage and preservation, not translation quality.

Lucide icons are bundled with their full ISC/MIT notices and source manifest in `app/assets/illustrations/icons`. Original SVG branding and workflow compositions are local. The application does not fetch the new imagery from the internet.

## Data and updates

The desktop data directory remains `SoloDevStudio`; Android keeps application ID `com.solodev.studio` and increments versionCode to **113**. No personal profile was used by the implementation tests. Old release packages are removed after the latest packages pass verification. Export a full Vault ZIP when you want a transferable copy of projects and media; JSON contains the written project data.

The Android release must use the existing private signing key for an in-place update. Source packages exclude private signing material and local SDK configuration. Keep signing keys private. The source ZIP uses environment variables for signing credentials.

## Release verification

See `docs/V4-VERIFICATION.md`, `docs/V4-REQUIREMENT-MATRIX.md` and `release-validation.json` for the actual evidence and limitations. Linux/macOS native launches, a physical Android update/install and human usability/assistive-technology studies require further verification. A successful package build alone does not establish native correctness.

Historical 3.6.30 release notes are preserved in `docs/release-3.6.30.md`.

## Run or rebuild

Web: serve `app/` locally or open `app/index.html`. Desktop: install dependencies in `desktop-src`, then `npm start`. The Windows portable executable is `SoloDevToolbox-4.5.0-portable.exe`.

Before packaging, run `node desktop-src/tools/sync-app.js`; `--check` verifies byte parity without copying. It mirrors canonical `app/` into Windows, Android www/public, Linux and macOS wrappers without opening user profiles.

Windows: `npm run dist` in `desktop-src` (Node 22+). Android: JDK 21 and Android SDK 35/36; run `gradlew :app:testDebugUnitTest :app:assembleRelease` in `mobile-src/android`. Linux/macOS standalone builders are `PortedApps/*/tools/make-standalone.py`; both read version 4.5.0 from their package metadata and use Electron 40.10.2.

Useful checks in `desktop-src`:

```text
npm run test:v4
npm run test:regression
npm run test:files
npm run test:locales
npm run test:drafts
npm run smoke
```

The optional accessibility harness uses axe-core from the path in `SOLODEV_AXE_SOURCE`; it is a development test dependency, not shipped runtime code. `SOLODEV_TEST_OUTPUT` selects an isolated evidence directory. Tests use their own profiles and fixtures. Cross-version backup fixtures were exported by the captured original 3.6.30 code.

macOS packages are unsigned and not notarized. The bundled first-launch helper and existing platform instructions remain in each archive. Linux archives preserve executable permissions; macOS archives preserve framework symlinks.

