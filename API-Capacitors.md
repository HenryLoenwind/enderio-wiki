Third party mods can make new capacitors that Ender IO will use just like the built-in ones. There are two ways of doing so: Programmatic and NBT. The programmatic way allows you more control but gives you a compile-time dependency on Ender IO. The NBT way doesn't do either.

## Programmatic

Implement `crazypants.enderio.base.capacitor.ICapacitorDataItem` on your item. It only has one method, `getCapacitorData()`. This will be called to retrieve the data object (`ICapacitorData`) from an ItemStack when it is inserted into a machine. The capacitor data will then be queried every time a value is needed (one notable exception is the machine's energy buffer size, which is only set once).

`ICapacitorData` also is a quite simple interface, virtually everything happens in `float getUnscaledValue(@Nonnull ICapacitorKey key)`. The single parameter is a `ICapacitorKey`, one of the pre-defined keys in Ender IO that represent all the different values Ender IO's machines have. There's a CapacitorKey for the energy buffer size of the Sagmill, one for the stack size limit of the Farming Station, one for cost of copying a coordinate paper in the Dialing Device, etc.

`getUnscaledValue()` then needs to produce a capacitor *level* for the CapacitorKey. This is **not** the final value, but the quality of the capacitor for this specific use. The 3 'normal' capacitors have the levels 1, 2 and 3 for all uses. The level `getUnscaledValue()` produces should stay between 0 and 5. Values outside this range could produce serious malfunctions.

## NBT

NBT-base capacitors work the same way as programmatic ones, just that there is no `getCapacitorData()` on the item. Instead the `ICapacitorData` is created from the NBT tags of the ItemStack. This means that the NBT data has to contain a complete mapping of all possible CapacitorKeys to a capacitor level. To achieve that, the NBT data can contain level data in 4 different ways: LEVEL, TYPE, OWNER+TYPE, NAME. When looking up a value, Ender IO will try to find a value in reverse order.

Note: The examples on this page are incomplete NBT snippets and need to be combined according to what's written in the descriptions. TL;DR: Copy&Paste without reading won't work.

### LEVEL

```
{eiocap:{level:1.111f}}
```

A LEVEL definition is required for all capacitors to be valid. This is the ultimate fallback value.

### DURABILITY

If an item that has durability has a NBT capacitor applied to it, then it will damage the item for 1 point each time the machine it is in completes a task.

### TYPE

```
{eiocap:{amount:2.222f}}
{eiocap:{area:2.222f}}
{eiocap:{energy_buffer:2.222f}}
{eiocap:{energy_gen:2.222f}}
{eiocap:{energy_intake:2.222f}}
{eiocap:{energy_loss:2.222f}}
{eiocap:{energy_use:2.222f}}
{eiocap:{speed:2.222f}}
```

Every CapacitorKey has a TYPE. The type is a rough categorization of the purpose of the key.

### OWNER+TYPE

```
{eiocap:{"enderio:block_simple_alloy_smelter":{energy_buffer:2.222f}}}
{eiocap:{"enderio:block_simple_alloy_smelter":{energy_intake:2.222f}}}
{eiocap:{"enderio:block_simple_alloy_smelter":{energy_use:2.222f}}}
...
```

In addition to a TYPE, capacitor keys are also specific to a machine.

### NAME

```
{eiocap:{"enderio:block_simple_alloy_smelter/intake":2.222f}}
{eiocap:{"enderio:block_simple_alloy_smelter/buffer":2.222f}}
...
```

And the most specific way is to target a specific CapacitorKey by its name.

Note: This list only contains some samples that may even be outdated. Please look up the availables names in the xml recipe files (e.g. capacitor.xml, capacitor_machines.xml).