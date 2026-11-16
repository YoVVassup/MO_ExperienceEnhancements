**Language: English | [Русский](Hotkey.ru.md) | [简体中文](Hotkey.zh.md)**

# Hotkey syntax

Applies to: the `Hotkey` entries of `[PatrolCircle]`, `[SmartOrder]`, `[TreeChop]` and
`[FuzzyAttack]` in `MOExperience.ini`, the `MindSelect`/`AttackMove` entries of `[Features]`,
the `ToggleKey` entries of `[SWSidebar]` and `[Sidebar]`, and the
`PauseHotkey` entry of `[BottomBar]`.

## Rules

- Format: modifier(s) + key, joined by `+` or a space. Example: `Shift+P`, `Ctrl+Z+Middle`.
- Case-insensitive: `ctrl+z` = `Ctrl+Z`.
- Spaces/Tab anywhere are ignored: `  ctrl + z  ` = `Ctrl+Z`.
- A trailing `;` starts a comment and is cut off: `Hotkey=Middle ; scatter` keeps only `Middle`.
- With multiple keys, **the last one is the primary key, the preceding ones must be held**:
  `Ctrl+Z+Middle` = hold Ctrl and Z, then press the middle mouse button.
- `None` / `Off` / `Disabled` = the feature is turned off.
- Missing key, empty string or a typo → the default is used; nothing breaks.
- Single-line toggles (`MindSelect`/`AttackMove` in `[Features]`): `0` = disabled,
  a hotkey = enabled with that key, missing entry = enabled with the default hotkey.

## Modifiers

| Syntax | Meaning |
|---|---|
| `Ctrl` (`Control`) | Ctrl key |
| `Shift` | Shift key |
| `Alt` (`Menu`) | Alt key |
| `Win` (`Windows`) | Win key |

## Keys

Single letters/digits are written directly: `A`~`Z` (letter keys), `0`~`9` (digit keys), `F1`~`F24`.

Note: multi-digit pure numbers are interpreted as legacy `TriggerVK` values, e.g. `80`=P,
`90`=Z, `4`=middle mouse button; a single `4` is the digit 4. Write `Middle` for the middle button.

### Function keys

| Syntax | Key |
|---|---|
| `Space` | Space |
| `Tab` | Tab |
| `Enter` (`Return`) | Enter |
| `Backspace` (`Back`) | Backspace |
| `Insert` (`Ins`) | Insert |
| `Delete` (`Del`) | Delete |
| `Home` | Home |
| `End` | End |
| `PageUp` (`PgUp`) | PageUp |
| `PageDown` (`PgDn`) | PageDown |
| `Up` / `Down` / `Left` / `Right` | Arrow keys |
| `Pause` | Pause |
| `Num0`~`Num9` | Numpad 0~9 |

### Mouse

| Syntax | Button |
|---|---|
| `Middle` (`MMB`) | Middle mouse button |
| `LMB` | Left mouse button |
| `RMB` | Right mouse button |
| `X1` | Side button 1 (forward) |
| `X2` | Side button 2 (back) |

## Defaults per feature

| Feature | Default `Hotkey` | Notes |
|---|---|---|
| Patrol circle `[PatrolCircle]` | `Z+Middle` | Hold Z and drag with the middle button to draw a circle; yields to range-smart claiming |
| Smart order `[SmartOrder]` | `Middle` | Bare middle click adapts (move/attack/enter/garrison), drag to scatter; hold Z to yield to patrol, hold Ctrl to yield to fuzzy, middle combos yield to area-adaptive |
| Tree chop `[TreeChop]` | `Ctrl+Z+Middle` | All three keys together |
| Fuzzy attack `[FuzzyAttack]` | `Ctrl+Middle` | Yields to patrol/tree-chop while Z is held; Ctrl+Shift+Middle also counts as fuzzy; while held a red planning line connects to the assigned enemy and disappears on release |
| Attack-move `[Features]` (`AttackMove`, single line) | `X2` | The vanilla Ctrl+Shift+left-click attack-move (Mission=29); a single key (e.g. `X2`/`A`) fires directly at the hovered cell, a left-click combo (e.g. `A+LMB`) issues on left click; hold Z to queue (waypoints); left-click combos also perform one vanilla selection click — use a single key if you mind that |
| Range-smart `[SmartArea]` | `Shift+Middle` (primary must be `Middle`; can be changed to a single key like `X1`) | Click/drag over blocks (each node of the path) to pick targets; while held a thin green line connects to each assigned target (gone on release), each object is ordered by its own cursor rule (no moving); cursor queries use the unit's inherent cursor (ignoreForce=1), physical Shift/Ctrl does not pollute the check; with no order a rule table applies: non-owned vehicles/aircraft/infantry (not buildings) → force-attack, engineers vs buildings/empty vehicles → capture (target-limited to 1), infantry vs own vehicles → enter, other owned units are skipped, non-engineer infantry vs buildings → guard; release to execute; guard re-evaluates after all dirty keys are released; with Ctrl held it counts as fuzzy, Z is not blocked |
| Mind-control filter `[Features]` (`MindSelect`, single line) | `Shift+P` | Keeps only mind-controlled units at the end |
| Superweapon sidebar `[SWSidebar]` | `F4` (`ToggleKey`) | Show/hide the right superweapon sidebar (hidden takes no space) |
| Hide sidebar `[Sidebar]` | `F11` (`ToggleKey`) | Vanilla sidebar three-state cycle: full / minimap+buttons only / fullscreen |
| SP pause `[BottomBar]` | `F5` (`PauseHotkey`) | Pause/resume (skirmish/campaign only, ignored online; `PauseEnable=0` disables it entirely); bottom bar left-click: separate pause/resume and single-frame-step buttons (shown after the first F5 press, then always visible) |
