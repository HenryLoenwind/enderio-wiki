Server administrators, modpack makers, modders and power users may want to change how Ender IO works on a deeper level than players. This page collects information for them.

* [[Loot Tables]] (modpacks, servers)
* [[API Capacitors]] (modders, modpacks)

### Configuration (modpacks, servers, users)

Ender IO uses the normal Forge config system. You can use Forge's ingame configuration GUI in single player or edit the config files manually. Configuration is generally split up by module, but some settings are in 'base' even so the machines they affect are in other modules.

### Recipes (everyone)

Ender IO uses an XML-based recipe system for all its recipes and some recipe-like configuration. All those recipes can be edited. When the game starts, Ender IO reads recipe data from 3 sources: The files bundled up in the jar (can be disabled with a config flag), snippets sent by other mods using the [IMC](https://github.com/SleepyTrousers/EnderIO/blob/master/enderio-base/src/main/java/crazypants/enderio/api/IMC.java) system, all files in the 'recipes/user' folder. Each stage can modify (change or disable) recipes from the previous stage.

### Farming Tools (modders, modpacks)

To enable your tools to be usable in the [[Farming Station]] you need to:

* Hoe: Either subclass `ItemHoe` or oreDict as `toolHoe`.
* Axe: Have a harvest level for `axe` above 0.
* Treetap: OreDict as `toolTreetap`.
* Shears: Either subclass `ItemShears` or oreDict as `toolShears`.

The [[Slice'n'Splice]] uses the same logic for its axe and shears.

### API (modders)

Ender IO has an extensive [API](https://github.com/SleepyTrousers/EnderIO/blob/master/enderio-base/src/main/java/crazypants/enderio/api/) you can use. It includes:

* Interfaces to bind addon mods tightly to the Ender IO base module (`IEnderIOAddon`, `IModObject`, `IModTileEntity`). You only need those if you want to make such a tightly coupled addon mod.
* A capability for code-based capacitors (`CapabilityCapacitorData` etc). You can use those if the NBT-based API (see above) isn't enough for you.
* Interfaces and classes to add farming logic (`IFarmerJoe` etc) and fertilizers (`IFertilizer`) to the Farming Station. Both are Forge-Registry-based, so you register them just like blocks and items.
* Interfaces to make your own Travel Anchors (`ITravelAccessable` etc) or Staff of Travelling (`IItemOfTravel`).
* Interfaces to make a YETA-compatible wrench (`ITool`), an item to see through facades (`IHideFacades`), or selectively hide conduit types (`IConduitControl`).
* Interfaces to make your own "Dark Steel Item" (`IDarkSteelItem`) that can take "Dark Steel Upgrades" (`IDarkSteelUpgrade`). This also includes custom materials (`IEquipmentData`) and rendering on the player model (`IHasPlayerRenderer`, `IRenderUpgrade`).

If you want to add conduits, there's a checklist in the API package on what to do. You will need more than just the API as conduits can be quite complicated.