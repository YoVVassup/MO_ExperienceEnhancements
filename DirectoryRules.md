**Language: English | [Русский](DirectoryRules.ru.md) | [简体中文](DirectoryRules.zh.md)**

# Directory Rules
Local rules written for agents.

| Directory | Purpose | What may go here | What is forbidden |
|---|---|---|---|
| `src/` | Source code taking part in the build | `.c`/`.cpp` files referenced by build commands | Probes, experiments, leftover `.inj` files |
| `dist/` | **The only release directory** | Build output DLL, sample ini (hooks are embedded in the DLL as a `.syhks00` section, so no `.inj` deployment is needed — see `src/core/SyringeHooks.cpp`; `dist/*.inj` is kept only as an audit reference) | Intermediate files, experiment files |
| `build/` | Compile/debug intermediates | `.o` files, `.asm` dumps | Leftover DLLs, test source code |
| `test/` | Tests and one-off experiments | Probes, layout experiments, temporary analysis files | Anything taking part in the build, long-term files |
| `notes/` | Notes | Reference material, lessons learned, reference records, probe conclusions, etc. |  |
| `other/` | Other (user) files | This is the user's directory, for images and release files | The agent must not touch this folder |

Rules:

1. Build commands **point directly at `dist/`**; deployment to the outside takes files from `dist/` only.
2. `tools/` holds scripts only; the toolchain may live in `tools/mingw/mingw32/bin` (`/tools` is
   ignored by `.gitignore` and never committed). When it is missing on the machine, build scripts search
   `%MOE_MINGW%` → `tools/` → `../AutoLoadDev/tools`
   → `PATH` in that order, so switching machines or cloning the repo requires no script changes.
   `references/` always uses
   `../AutoLoadDev/references`.
3. The build chain and referenced header paths stay pure ASCII; source comments and documentation may
   be in Chinese.
   **`.bat` files must be pure ASCII + CRLF** (cmd.exe reads them with the OEM code page; Chinese turns
   into mojibake, and LF eats the first character of a line).
4. Third-party projects are recorded as a minimal reference only (URL, calls, conclusions) — no whole
   files committed.
5. `src/` is split into subdirectories by functional domain:
   | Directory | Responsibility | Modules |
   |---|---|---|
   | `core/` | Lifecycle and infrastructure | `MOExperience` (coordination layer), `SyringeHooks`, `Lang`, `MOEVersion.h`, `EngineAddr.h` |
   | `gui/` | Drawing and UI | `VecText`/`MsgText`/`GdiText`/`ToolTip`, `SWPanel`/`PowerDisplay`/`Icon`/`PcxImage`, `FullMap`/`ScaleBar`/`PiP`/`GridView`/`Shot`/`PauseView`/`ChatEdit`/`LineEdit`, `EscMenu`/`PlayerColor`, `icons.rc`/`IconRes.h` |
   | `order/` | Orders and mouse/keyboard interaction | `SmartOrder`/`SmartArea`/`FuzzyAttack`/`AttackMove`/`Aggressive`/`TreeChop`/`TypeSelect`/`MindSelect`/`PatrolCircle`/`RallyPath`/`AirWay`/`OrderThrottle` + shared order utilities in `OrderUtil` |
   | `sidebar/` | Sidebar, production and superweapons | `BuildQueue`/`SWSBar`/`SWSTest`/`RepairAll`/`SideScroll`/`SidebarSkin` |
   | `preview/` | Placement preview and range display | `DeployPreview`/`PlacementPreview`/`PlaceScatter`/`WeaponRange` |
   | `perf/` | Timing and rate limiting | `FrameCap`/`GameSpeed` |
   | `misc/` | Small engine patches and notices | `Observer`/`WaypointCap`/`MegaListCap`/`NoApproach`/`PvpNotice` |

   Module file names match the ini section names; headers include each other by bare name, resolved at
   compile time via
   `-Isrc -Isrc\core -Isrc\gui -Isrc\order -Isrc\sidebar -Isrc\preview -Isrc\perf -Isrc\misc`.
   **When adding/removing a subdirectory, change exactly one place**: `SRCINC` in `build-common.bat`
   (`CXXFLAGS` and the dependency-scan `$inc` are both derived from it). The source file list is no
   longer written by hand — the build scans `src\**\*.cpp`
   and generates `obj\sources.txt`, so adding/renaming/moving a `.cpp` requires no build script changes.
