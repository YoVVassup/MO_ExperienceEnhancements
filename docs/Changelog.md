**Language: English | [Русский](Changelog.ru.md) | [简体中文](Changelog.zh.md)**

## Changelog
## v1.0x tentative — pre-release notes
New features or improvements:
- Aggressive mode ignores invulnerable enemies; optionally ignores key tech buildings
- Added a switch to skip drawing the Phobos version warning; when off, the redraw is skipped too

Fixes:
- When hiding the sidebar with F11, the bottom bar is now filled in, avoiding black areas, ghosting or truncated display
- Added compatibility with vanilla YR: saves no longer interfere with the skirmish UI; improved the load-game page layout at 800x600
- The sidebar no longer affects Phobos text layout calculations, so text no longer overlaps
- Input boxes on the settings page should no longer have input problems

## v1.05
New features or improvements:
- The unit panel can now show some basic info of neutral or enemy units
- Armor multipliers of 0 and above 999 now display as infinity
- Right-click kicks a specific unit or group out of the selection
- Added a switch for volume expansion, off by default in the config; seems to make no difference...
- After loading a save you can build next to allies again (still disallowed if configured otherwise)

Fixes:
- Fixed some leftover icons or frame/line drawings remaining on the bottom bar
- Fixed the communication beacon not showing its direction arrow under the shroud
- Fixed the map edge being immovable in the minimap area
- Fixed uneven target distribution with shift+middle-click when the target is much larger
- Added an IME position fix to the preset texts in the text box

## v1.0
New features or improvements:
- Added the **small window** feature: click the map in the small window to jump, right-click to move the view  
  Enable the alert icon to auto-jump to the latest event; enable the mouse icon for remote control — you can watch the AI or issue orders remotely
  Press F to follow units without focus, including enemies
- Added the unit **info panel** for basic info
  Shows ammo, veterancy, self-heal, ore and other info
  Shows a vehicle's passengers; supports selecting one unit type
  Supports unloading specific passengers, disabled online
  Supports waypoints for members inside a vehicle, with multi-select
- Unit panel sidebar: some features can be turned off or on
  Supports collapsing the panel, or persistently showing veterancy info
  Supports a WASD mode toggle, useful for solo-infantry missions — a niche toy...
  Supports favoriting units and showing arrows; can also mark communication beacon positions
- Added save/load preview thumbnails
- Added many **screenshot** features suited for base-posing
- Added **environment control**, freely change unreasonable in-game lighting
- Added new weather control: texture or particle effects; rain has rain sounds, snow has wind sounds, lightning has thunder
- Added cloud shadows or fog display for atmosphere
- Added a screenshot key on the bottom bar, hidden by default; takes a screenshot at native resolution with the UI hidden, enough to capture the whole game map
- Preliminarily added a settings page, simplifying the configuration flow for many features; the page can also be disabled
- Preliminarily added multi-language support with automatic switching
- Added preset texts for the text input box, recalled with the up/down keys
- Added in-game UI switching with a corresponding trigger; trigger-based changes are temporary (turn off other features when you only need this one)
- Added in-game color switching, including rainbow colors
- Upgraded some feature icons from stick figures to images
- Added an exit button to the campaign end screen (continuing to the next mission could get stuck on triggers/state in some campaigns)
- Added a ghost preview for building placement/deploy, avoiding Phobos
- Added crate type display for campaigns; does not affect random crates in skirmish
- Added local cheering
- Added filtering of loss notices for mind-controlled units
- Improved quick tree chopping: filters out ore pillars, includes street lamps and other clutter; units that can't attack trees are no longer assigned
- Improved shift+middle-click target assignment: can repair or capture empty vehicles sensibly, supports EP power plants and tank bunkers
- Improved alt+a aggressive mode: some siege units have too-small guard ranges, so targeting units is supported; improved units that don't attack by default
- As requested, added a PVP cheat declaration; has no effect on online PVE or spectating

Fixes to game functions
- Lighting fix, jagged-lighting fix, configurable blend ratio between the two lighting types
- Ore can now be tinted by the environment
- Lifted the 500-displayed-units box-select limit and added a query interface
- Fixed the game's own save-load spectating, avoiding the game ending when an AI is defeated
- Fixed cncddraw causing excessive CPU usage on the game menu screen

Fixes and avoidance:
- Middle-click move now has filtering: you can no longer freely control other players' units, but units blocking the way can be moved 2 cells for pathing purposes
- Fixed the building queue being unstable online due to latency
- Fixed range display for air units: now drawn centered on the ground projection
- Fixed anti-air line drawing: starts at the unit, ends at the ground projection; since air units fly at different heights drawing cylinders looks odd, so an assumed height can be set
- Fixed ctrl+repair not taking effect, and becoming gradually unreliable as the game goes on
- Fixed the superweapon panel not displaying fully when there are too many superweapons
- Avoidance and compatibility
  Prevents double-drawn Phobos sidebar hints
  The 500 limit is automatically disabled in a Phobos environment
  Auto-loading got a query capability for the 500 limit; the old version might crash

Other
- To avoid crashes when lifting the 500 cap, the auto-loading extension needs updating
- Fixed cnc-ddraw settings screen having no scaling and excessive CPU usage
  With an old cnc-ddraw, MOE enables its own frame-cap strategy; fixed cncddraw versions provide a query to avoid conflicts
  MOE itself does not provide UI scaling fixes

## v0.99
New features or improvements:
- Left-click attack commands now filter out repair units, preventing them from running to their deaths
- Added a simple aggressive mode: units/engineers auto-attack/auto-capture buildings when idle
- Filtering of units without attack ability is broader: extended from middle-click to other middle-click commands
- Superweapon sidebar supports fill sorting: fill two columns first, then three, then four, then scroll down; toggle by right-clicking the collapse button
- Superweapon sidebar hints can show the cost; you can no longer select one when funds are insufficient
- Fuzzy orders support bulk building repair by engineers, bulk capture of empty vehicles; bulk hijacking, etc.
- Campaign text supports a configurable delay to extend and show full history

Fixes:
- Attempted to fix display coordinate offsets that could occur at various resolutions under different renderers
- Fixed shift being made harmless; it can now be combined with middle-click orders, so fuzzy target assignment returns to shift+middle-click
- Fixed the center unit being kept when buildings auto-scatter units
- The score screen reverted to the game's original drawing due to insufficient text space
- Fixed crashes when setting many rally-point paths; lines changed to dashed
- Can no longer set paths for other players' buildings
- Superweapon icons now support SHP format: in short, custom superweapons without icons went from blank to showing a purple ball; vanilla SHP is supported
- Attempted to fix crashes introduced in 0.98 when coexisting with Phobos; attempted to avoid other modules' hooks

## v0.98
New features or improvements
- Added radar event jumps with configurable event texts. (It's really the space-bar jump plus a list recording history)
- Supports setting factory paths with Z (implemented with waypoints, somewhat niche)
- Fuzzy orders support waypoints

Fixes:
- Fixed the accidentally broken tree-chopping feature: rule — few units, many trees → assign multiple trees per unit; many units, few trees → assign multiple units per tree
- Fixed long text on the right side of the superweapon sidebar being clipped; improved display, added line wrapping
- Fixed being unable to fire superweapons while units are selected; changed to match the game: selecting a superweapon deselects units
- Fixed the building construction list getting stuck due to lost tech or build limits
- Fixed accidentally broken campaign text: some strings like "up/down" were dropped entirely because they were too long

## v0.95
First public release, omitted.


## Download links
github:
https://github.com/MagicShiba/MO_ExperienceEnhancements  

Baidu Netdisk:
https://pan.baidu.com/s/1Lgg7bPCghPIwQYQ-vKUqfg?pwd=ff2k  
Extraction code: ff2k 

Ys100 disk:
https://hxyy.ysepan.com/
In the "Red Alert MOD tools and help" folder
