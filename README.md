# taw-am1-mission-framework
A mission framework for creating new TAW AM1 missions easily.

## Instructions:
1. Download the repository and copy the `Framework.VR` folder to your `mpmissions` folder (on Windows, this will be `C:\Users\{WindowsUser}\Documents\Arma 3 - Other Profiles\{ARMA 3 Profile}\mpmissions`).
2. Rename `Framework.VR` to `{MissionName}.{WorldName}`, where `MissionName` is a descriptive name for your mission (often including a version number, e.g. `EscapeFromBaddies_v01`) and `WorldName` is the Arma 3 name given to each map/world (e.g. `Stratis`, `Altis`), for a complete name such as `EscapeFromBaddies_v01.Altis`.
3. Load the mission in the Eden editor.
4. Select all units present on the map and drag them to wherever you want the FOB to be.
5. Add additional starting assets (such as vehicles, aircraft) as desired.

## Arsenal
By default, the starting Arsenal is configured to allow all assets except for those globally blacklisted via the `taw_am1_mechanics_globalArsenalBlacklist` CBA setting. To blacklist additional items, you can add them as blacklisted items on the Arsenal crate itself. If you wish to whitelist items that are globally blacklisted by default, or to add additional globally blacklisted items (applies to all Arsenals), you must edit the CBA setting for it (`Settings` => `Addon Options` => `ADDON: TAW AM1` => `Arsenal` => `Global Blacklist`). This setting is simply an array of class names to blacklist.

## Babel
By default, Babel is configured with WEST speaking English, EAST speaking Russian, INDEPENDENT speaking English and Russian, and CIVILIAN speaking Gibberish. This allows for easy configuration of roleplay missions where INDEPENDENT units can serve as an interpreter between EAST and WEST units. If you wish to adjust these per-side defaults, you must edit the CBA settings for them (`Settings` => `Addon Options` => `ADDON: TAW AM1` => `Babel`). `Babel Languages` is the list of all languages that exist in the mission (an array of key-name pairs, e.g. `[["en","English"],["ar","Arabic"],["ru","Russian"]]`). `{SIDE} Spoken Languages` is a list of language keys that units on that side speak by default (e.g. `["en", "ar"]`).

To set languages spoken by a specific unit, set the array of spoken languages as the `babel_languages` variable on that unit in its initialization box (e.g. `this setVariable ["babel_languages", ["en", "ar"]];`). Note that this will override the defaults, so the unit will *only* be able to speak the languages specified in that variable (*not* those languages + the default languages).

## Crate Filler
To use the KP Crate Filler system (spawning crates and filling them with items, or filling nearby vehicles with items), open the item that you want to have Crate Filler enabled in the editor, and check the `Object: TAW Options` => `Is Crate Filler` box. To have crates spawn at a specific object (e.g. the `Parachute Jump Target` item is commonly used for this), and to have that object be the place where vehicles should be parked for loading:

1. Give the target object a variable name, e.g. `crate_filler_spawn`.
2. On the object on which you enabled the `Is Crate Filler` option, enter the same variable name in the `Object: TAW Options` => `Crate Filler Spawn` box.

If you do not use a spawn target object, the object that has Crate Filler enabled will be the spawn point for crates (and vehicles will need to be close to it to load their inventories). Note that Crate Filler is subject to the same global blacklist of items as the ACE Arsenal.