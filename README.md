**Language: English | [Русский](README.ru.md) | [简体中文](README.zh.md)**

# Mental Omega Experience Enhancements

[This project](https://github.com/MagicShiba/MO_ExperienceEnhancements) aims to improve the game experience of [Mental Omega](http://mentalomega.com/) and fix game bugs.  
While adding new features and reducing operational complexity, it always keeps multiplayer functionality intact.  
It does not modify any in-game `.ini` files.  
Supported version: 3.3.6; in theory it is also compatible with other mods that use the same ARES.  
You may use it in online PvE, but not in PvP — that is not what it is intended for. I bear no ill will toward players, but using it in PvP will automatically and repeatedly notify the other players that you are cheating.  
![alt text](docs/imgs/MO_logo_header.png)

## What does this project do?
Brief overview — [see a more detailed feature demo and explanation](docs/1.GUI功能与文本显示.md)  


| Better text display | Building features |
| -- | -- |
| Centered, persistent campaign text you can check at any time — no longer pushed off screen.<br>Operation messages are evicted from the main text and shown separately as radar events; click to jump to the event.<br>Fixes wrong IME position; a better input box with customizable preset texts.<br>Customizable text font and display size. | Build queue, placement preview,<br>expel units while placing<br>polyline rally points (waypoints for production buildings)<br>quick repair (double-click or automatic) |

| Sidebar | Bottom bar |
| -- | -- |
| Customizable superweapon sidebar for a clean defense tab.<br>Hide the sidebar: fullscreen or radar-only (with trigger support).<br>Scrollbar with fast page jumping.<br>Power status display. | Zoom the view for a closer look or a wider field, full map view available.<br>Pause and frame stepping — issue orders frame by frame.<br>Grid display to see unbuildable / impassable cells.<br>UI-free screenshots that work with zoom to capture the whole map. |

| Big upgrades for base screenshots! | The wish list comes true! |
| -- | -- |
| Detailed **environment controls**<br>Cloud and fog shadows, lighting control, rain/snow weather control.<br>You can fix maps that are too dark (legacy work).<br>Zoom, pause, UI-free screenshots (weather included).<br>You can even **zoom** and grab the entire map at native resolution in-game!<br>Adjust your color, even rainbow!<br>UI-free screenshots with the sidebar hidden for a larger area. | **Info panel area**<br>Ammo shown for selected aircraft — no need to switch screens.<br>Unit health, XP and bonus info.<br>Select all units of one type from a mixed group; right-click to remove.<br>Passenger list for selected vehicles.<br>Unload a single crew member instead of all (buildings too).<br>Issue waypoints from inside a vehicle. |
| **Small window**  | **Edge buttons**  |
| Auto-follows radar events (the same events you jump to with Space).<br>Remote orders: view and operate other areas from the small window (e.g. Fatal Trigger).<br>Focus-free following (press F; the target is not lost when you cancel).  | Favorites with arrow indicators — center or edge display.<br>Also shows communication beacon locations.<br>WASD movement for microing individual units.  |

| Game control and UI misc | |
| -- | -- |
| Finer-grained game speed control  | Stores a screenshot with every save for easy identification  |
| Mind-controlled unit filtering  | Lifts the 128 order limit  |
| Aggressive mode: auto-attack enemies in range / alert area  | Lifts the 16/128 waypoint limit  |
| Simplified attack-move with customizable hotkeys  | Lifts the 500-unit box-select display limit  |
| Fixes the T key often not working on units  | Waypoint support for aircraft  |
| Attack command filters out units that cannot attack  | Fixes screen jitter when the map is smaller than the view  |
| Can mute alerts about losing mind-controlled units  | Fixes observer mode breaking after loading, and the game ending after any AI is defeated  |
| View crate types (mostly campaign only;<br>random crates are not supported) | Adds an exit button on the score screen<br>(continuing to the next mission can stall triggers/state in some campaigns)  |
| Lighting blend switching<br>(default lighting vs trigger lighting)  | Fixes jagged edges after lighting changes and lighting issues after loading<br>Supports ore brightness adjustment  |
| Auto-removes old beacons and lifts the single-player beacon limit  | Cheering applies to locally selected units only, not globally  |
| Fixes losing ally-side construction after loading  | Fixes cnc-ddraw causing high CPU usage in the options screen  |

**Fuzzy orders (a.k.a. smart middle mouse — hotkeys are customizable)**
- Middle-click to move: air units scatter to find spots, ground units pack into a spiral — handy for Iron Curtain and similar
- Middle-drag a battle line: quick simple formation, assigns units along the line
- Middle-click patrol circle: Z + middle-click creates a small patrol circle, drag to create one quickly
- Deployment preview for MCV-type units: draw a line to assign positions, auto-deploy; Shift forces a straight line
- Auto tree chopping: Ctrl + Z + middle-click, no need to click on an actual tree
- Quick automatic target selection: Shift + middle-click — mass garrison, mass capture, mass repair, tanks into bunkers, etc.
- Fuzzy-order quick target selection: Ctrl + middle-click, for hard-to-select units like spiders (that niche was mostly taken by Shift+middle-click; it was not meant to be that strong originally...)


To ship the first version as fast as possible, some known minor bugs are temporarily unfixed.  
Some features promised in replies are not implemented yet.  

### Where is auto-load?
See the project: [MO_AutoLoad](https://github.com/MagicShiba/MO_AutoLoad)  
No plans to merge it for now.

## Usage
Put `MOExperience.dll`, `MOExperience.ini` and the `MOExperienceResources` folder into the game root directory.  
**Note**: if the interface is broken, update or use the cnc-ddraw bundled with the release.

### Feature configuration
Press ESC in game to open the extended settings menu (this is not everything).  
`MOExperience.ini` contains detailed usage instructions; edit that file for fine-grained configuration.  
See `Hotkey.md` for hotkey configuration.  
For custom superweapon ordering (put your favorites first), see `超武列表.md` and the examples in the config file; by default Iron Curtain and Force Shield are placed first.

## Development and build

If you want to develop similar projects, take a look at [MO_AutoLoad](https://github.com/MagicShiba/MO_AutoLoad)  
Its documentation briefly explains how to develop plugins like this — start with something simple, and trust in AI.

Environment:
- Toolchain: `mingw-i686`
- Build script: build-fast.bat
- Full build: build-full.bat

Folders not listed in the project:  
`reference` — phobos, yrpp, temporary maps and other references  
`ini` — rulesmo.ini etc., INI lookup docs, unit name tables, map references


## Plans
x-style C&C3 / Generals-style skill selection and unit info display — exact XP/HP values, command indicators, ability slots  
x Beacon extras: beacon menu, quick preset text selection  
x Aide helper features, maybe a new project  
x GPU-side rendering optimizations  
x Replay support and an internal list  

## Sponsor tokens
### -> [Cyber-begging](https://github.com/MagicShiba/MO_ExperienceEnhancements/blob/master/docs/赛博乞讨.md)
![alt text](docs/img_sbqt/h-凝视1.png)

## Notes
Implementation principles, pitfalls and caveats, written by AI.  
This is basically not meant for users — it is for the AI of someone who needs to reference the implementation.

## Reference projects
[phobos](https://github.com/Phobos-developers/Phobos): a powerful extension.  
[yrpp](https://github.com/Ares-Developers/YRpp): provides the ability to interact with the Yuri's Revenge engine from C++ engine patches/extensions.

## Related projects
[Ra2FontEditor](https://github.com/MagicShiba/Ra2FontEditor) — RA2 font editor  
[Improved cnc-ddraw](https://github.com/MagicShiba/cnc-ddraw/releases)
