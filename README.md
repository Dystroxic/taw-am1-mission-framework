# taw-am1-mission-framework
A mission framework for creating new TAW AM1 missions easily and consistently.

## Instructions:
1. Download the repository and copy the `Framework.VR` folder to your `mpmissions` folder (on Windows, this will be `C:\Users\{WindowsUser}\Documents\Arma 3 - Other Profiles\{ARMA 3 Profile}\mpmissions`).
2. Rename `Framework.VR` to `{MissionName}.{WorldName}`, where `MissionName` is a descriptive name for your mission (often including a version number, e.g. `EscapeFromBaddies_v01`) and `WorldName` is the Arma 3 name given to each map/world (e.g. `Stratis`, `Altis`), for a complete name such as `EscapeFromBaddies_v01.Altis`.
3. Load the mission in the Eden editor.
4. Select all units present on the map and drag them to wherever you want the FOB to be.
5. Add additional starting assets (such as vehicles, aircraft) as desired.

## Arsenal
By default, the starting Arsenal is configured to allow all assets except for those globally blacklisted via the `taw_am1_arsenal_globalBlacklist` CBA setting. To blacklist additional items, you can add them as blacklisted items on the Arsenal crate itself. If you wish to whitelist items that are globally blacklisted by default, or to add additional globally blacklisted items (applies to all Arsenals), you must edit the CBA setting for it (`Settings` => `Addon Options` => `ADDON: TAW AM1` => `Arsenal` => `Global Blacklist`). This setting is simply an array of class names to blacklist.

## Babel
By default, Babel is configured with WEST speaking English, EAST speaking Russian, INDEPENDENT speaking English and Russian, and CIVILIAN speaking Gibberish. This allows for easy configuration of roleplay missions where INDEPENDENT units can serve as an interpreter between EAST and WEST units. If you wish to adjust these per-side defaults, you must edit the CBA settings for them (`Settings` => `Addon Options` => `ADDON: TAW AM1` => `Babel`). `Babel Languages` is the list of all languages that exist in the mission (an array of key-name pairs, e.g. `[["en","English"],["ar","Arabic"],["ru","Russian"]]`). `{SIDE} Spoken Languages` is a list of language keys that units on that side speak by default (e.g. `["en", "ar"]`).

To set languages spoken by a specific unit, use the `Object: TAW Options` => `Babel Languages` field on the unit. This value should be an array of language keys, e.g. `["en", "ru"]`, that the unit speaks. Note that if this will override the defaults if any value is set, so the unit will *only* be able to speak the languages specified in that array (*not* those languages + the default languages).

To allow a unit to speak *all* languages (e.g. for game masters), check the `Object: TAW Options` => `Speaks All Languages` box on the unit. This is preferred to setting the languages specifically, as it makes it easier to re-use the mission with different language options.

## Crate Filler
To use the KP Crate Filler system (spawning crates and filling them with items, or filling nearby vehicles with items), open the item that you want to have Crate Filler enabled in the editor, and check the `Object: TAW Options` => `Is Crate Filler` box. To have crates spawn at a specific object (e.g. the `Parachute Jump Target` item is commonly used for this), and to have that object be the place where vehicles should be parked for loading:

1. Give the target object a variable name, e.g. `crate_filler_spawn`.
2. On the object on which you enabled the `Is Crate Filler` option, enter the same variable name in the `Object: TAW Options` => `Crate Filler Spawn` box.

If you do not use a spawn target object, the object that has Crate Filler enabled will be the spawn point for crates (and vehicles will need to be close to it to load their inventories). Note that Crate Filler is subject to the same global blacklist of items as the ACE Arsenal.

## Important Notes
- If you copy/paste the units from the framework, either to somewhere else on the map or to a different mission, it will lose their group ordering in the lobby and will reset their in-game callsigns to the default `Alpha 1-1`, `Alpha 2-1`, etc. It is recommended that you re-name the downloaded mission to change the map instead of copying the units to a new map.
- Some items in the editor, such as respawn markers, are only visible while in "map" mode (not in 3D editor mode). Always switch to map mode (default keybind "`M`") to check for any stray items that may not be in the correct location before exporting the mission.