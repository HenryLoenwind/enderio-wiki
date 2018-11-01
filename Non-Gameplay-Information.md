Server administrators, modpack makers, modders and power users may want to change how Ender IO works on a deeper level than players. This page collects information for them.

* [[Loot Tables]] (modpacks, servers)
* [[API Capacitors]] (modders, modpacks)

### Configuration (modpacks, servers, users)

Ender IO uses the normal Forge config system. You can use Forge's ingame configuration GUI in single player or edit the config files manually. Configuration is generally split up by module, but some settings are in 'base' even so the machines they affect are in other modules.

### Recipes (everyone)

Ender IO uses an XML-based recipe system for all its recipes and some recipe-like configuration. All those recipes can be edited. When the game starts, Ender IO reads recipe data from 3 sources: The files bundled up in the jar (can be disabled with a config flag), snippets sent by other mods using the [IMC](https://github.com/SleepyTrousers/EnderIO/blob/master/enderio-base/src/main/java/crazypants/enderio/api/IMC.java) system, all files in the 'recipes/user' folder. Each stage can modify (change or disable) recipes from the previous stage.

### Farming Tools (modders, modpacks)

To enable your tools to be usable in the [[Farming Station]] you need to:

* Hoe: Either subclass `ItemHoe` or oreDict as "`toolHoe`".
* Axe: Have a harvest level for "`axe`" above 0.
* Treetap: OreDict as "`toolTreetap`".
* Shears: Either subclass `ItemShears` or oreDict as "`toolShears`".

The [[Slice'n'Splice]] uses the same logic for its axe and shears. 