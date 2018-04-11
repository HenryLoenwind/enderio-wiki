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
{eiocap:{block_alloy_smelter:{energy_buffer:2.222f}}}
{eiocap:{block_alloy_smelter:{energy_intake:2.222f}}}
{eiocap:{block_alloy_smelter:{energy_use:2.222f}}}
{eiocap:{block_attractor_obelisk:{area:2.222f}}}
{eiocap:{block_attractor_obelisk:{energy_buffer:2.222f}}}
{eiocap:{block_attractor_obelisk:{energy_intake:2.222f}}}
{eiocap:{block_attractor_obelisk:{energy_use:2.222f}}}
{eiocap:{block_aversion_obelisk:{area:2.222f}}}
{eiocap:{block_aversion_obelisk:{energy_buffer:2.222f}}}
{eiocap:{block_aversion_obelisk:{energy_intake:2.222f}}}
{eiocap:{block_aversion_obelisk:{energy_use:2.222f}}}
{eiocap:{block_buffer:{energy_buffer:2.222f}}}
{eiocap:{block_buffer:{energy_intake:2.222f}}}
{eiocap:{block_buffer:{energy_use:2.222f}}}
{eiocap:{block_combustion_generator:{energy_buffer:2.222f}}}
{eiocap:{block_combustion_generator:{energy_gen:2.222f}}}
{eiocap:{block_combustion_generator:{energy_loss:2.222f}}}
{eiocap:{block_dialing_device:{energy_buffer:2.222f}}}
{eiocap:{block_dialing_device:{energy_intake:2.222f}}}
{eiocap:{block_dialing_device:{energy_use:2.222f}}}
{eiocap:{block_enhanced_combustion_generator:{energy_buffer:2.222f}}}
{eiocap:{block_enhanced_combustion_generator:{energy_gen:2.222f}}}
{eiocap:{block_enhanced_combustion_generator:{energy_loss:2.222f}}}
{eiocap:{block_farm_station:{amount:2.222f}}}
{eiocap:{block_farm_station:{area:2.222f}}}
{eiocap:{block_farm_station:{energy_buffer:2.222f}}}
{eiocap:{block_farm_station:{energy_intake:2.222f}}}
{eiocap:{block_farm_station:{energy_use:2.222f}}}
{eiocap:{block_painter:{energy_buffer:2.222f}}}
{eiocap:{block_painter:{energy_intake:2.222f}}}
{eiocap:{block_painter:{energy_use:2.222f}}}
{eiocap:{block_powered_spawner:{energy_buffer:2.222f}}}
{eiocap:{block_powered_spawner:{energy_intake:2.222f}}}
{eiocap:{block_powered_spawner:{energy_use:2.222f}}}
{eiocap:{block_powered_spawner:{speed:2.222f}}}
{eiocap:{block_sag_mill:{energy_buffer:2.222f}}}
{eiocap:{block_sag_mill:{energy_intake:2.222f}}}
{eiocap:{block_sag_mill:{energy_use:2.222f}}}
{eiocap:{block_simple_alloy_smelter:{energy_buffer:2.222f}}}
{eiocap:{block_simple_alloy_smelter:{energy_intake:2.222f}}}
{eiocap:{block_simple_alloy_smelter:{energy_use:2.222f}}}
{eiocap:{block_simple_stirling_generator:{energy_buffer:2.222f}}}
{eiocap:{block_simple_stirling_generator:{energy_gen:2.222f}}}
{eiocap:{block_simple_stirling_generator:{energy_loss:2.222f}}}
{eiocap:{block_slice_and_splice:{energy_buffer:2.222f}}}
{eiocap:{block_slice_and_splice:{energy_intake:2.222f}}}
{eiocap:{block_slice_and_splice:{energy_use:2.222f}}}
{eiocap:{block_soul_binder:{amount:2.222f}}}
{eiocap:{block_soul_binder:{energy_buffer:2.222f}}}
{eiocap:{block_soul_binder:{energy_intake:2.222f}}}
{eiocap:{block_soul_binder:{energy_use:2.222f}}}
{eiocap:{block_stirling_generator:{energy_buffer:2.222f}}}
{eiocap:{block_stirling_generator:{energy_gen:2.222f}}}
{eiocap:{block_stirling_generator:{energy_loss:2.222f}}}
{eiocap:{block_stirling_generator:{speed:2.222f}}}
{eiocap:{block_transceiver:{energy_buffer:2.222f}}}
{eiocap:{block_transceiver:{energy_intake:2.222f}}}
{eiocap:{block_transceiver:{energy_use:2.222f}}}
{eiocap:{block_vat:{energy_buffer:2.222f}}}
{eiocap:{block_vat:{energy_intake:2.222f}}}
{eiocap:{block_vat:{energy_use:2.222f}}}
{eiocap:{block_weather_obelisk:{energy_buffer:2.222f}}}
{eiocap:{block_weather_obelisk:{energy_intake:2.222f}}}
{eiocap:{block_weather_obelisk:{energy_use:2.222f}}}
{eiocap:{block_wired_charger:{energy_buffer:2.222f}}}
{eiocap:{block_wired_charger:{energy_intake:2.222f}}}
{eiocap:{block_wired_charger:{energy_use:2.222f}}}
{eiocap:{block_wireless_charger:{energy_buffer:2.222f}}}
{eiocap:{block_wireless_charger:{energy_intake:2.222f}}}
{eiocap:{block_wireless_charger:{energy_use:2.222f}}}
{eiocap:{block_zombie_generator:{energy_buffer:2.222f}}}
{eiocap:{block_zombie_generator:{energy_gen:2.222f}}}
{eiocap:{block_zombie_generator:{energy_loss:2.222f}}}
```

In addition to a TYPE, capacitor keys are also specific to a machine.

### NAME

```
{eiocap:{alloy_smelter_power_buffer:2.222f}}
{eiocap:{alloy_smelter_power_intake:2.222f}}
{eiocap:{alloy_smelter_power_use:2.222f}}
{eiocap:{attractor_power_buffer:2.222f}}
{eiocap:{attractor_power_intake:2.222f}}
{eiocap:{attractor_power_use:2.222f}}
{eiocap:{attractor_range:2.222f}}
{eiocap:{aversion_power_buffer:2.222f}}
{eiocap:{aversion_power_intake:2.222f}}
{eiocap:{aversion_power_use:2.222f}}
{eiocap:{aversion_range:2.222f}}
{eiocap:{buffer_power_buffer:2.222f}}
{eiocap:{buffer_power_intake:2.222f}}
{eiocap:{buffer_power_use:2.222f}}
{eiocap:{combustion_power_buffer:2.222f}}
{eiocap:{combustion_power_gen:2.222f}}
{eiocap:{combustion_power_loss:2.222f}}
{eiocap:{creative_buffer_power_buffer:2.222f}}
{eiocap:{creative_buffer_power_intake:2.222f}}
{eiocap:{creative_buffer_power_use:2.222f}}
{eiocap:{dialing_device_power_buffer:2.222f}}
{eiocap:{dialing_device_power_intake:2.222f}}
{eiocap:{dialing_device_power_use:2.222f}}
{eiocap:{dialing_device_power_use_paper:2.222f}}
{eiocap:{dialing_device_power_use_teleport:2.222f}}
{eiocap:{enhanced_combustion_power_buffer:2.222f}}
{eiocap:{enhanced_combustion_power_gen:2.222f}}
{eiocap:{enhanced_combustion_power_loss:2.222f}}
{eiocap:{farm_base_size:2.222f}}
{eiocap:{farm_bonus_size:2.222f}}
{eiocap:{farm_power_buffer:2.222f}}
{eiocap:{farm_power_intake:2.222f}}
{eiocap:{farm_power_use:2.222f}}
{eiocap:{farm_stack_limit:2.222f}}
{eiocap:{inhibitor_power_buffer:2.222f}}
{eiocap:{inhibitor_power_intake:2.222f}}
{eiocap:{inhibitor_power_use:2.222f}}
{eiocap:{inhibitor_range:2.222f}}
{eiocap:{painter_power_buffer:2.222f}}
{eiocap:{painter_power_intake:2.222f}}
{eiocap:{painter_power_use:2.222f}}
{eiocap:{relocator_power_buffer:2.222f}}
{eiocap:{relocator_power_intake:2.222f}}
{eiocap:{relocator_power_use:2.222f}}
{eiocap:{relocator_range:2.222f}}
{eiocap:{sag_mill_power_buffer:2.222f}}
{eiocap:{sag_mill_power_intake:2.222f}}
{eiocap:{sag_mill_power_use:2.222f}}
{eiocap:{simple_alloy_smelter_power_buffer:2.222f}}
{eiocap:{simple_alloy_smelter_power_intake:2.222f}}
{eiocap:{simple_alloy_smelter_power_use:2.222f}}
{eiocap:{simple_sag_mill_power_buffer:2.222f}}
{eiocap:{simple_sag_mill_power_intake:2.222f}}
{eiocap:{simple_sag_mill_power_use:2.222f}}
{eiocap:{simple_stirling_power_buffer:2.222f}}
{eiocap:{simple_stirling_power_gen:2.222f}}
{eiocap:{simple_stirling_power_loss:2.222f}}
{eiocap:{slice_power_buffer:2.222f}}
{eiocap:{slice_power_intake:2.222f}}
{eiocap:{slice_power_use:2.222f}}
{eiocap:{soul_binder_power_buffer:2.222f}}
{eiocap:{soul_binder_power_intake:2.222f}}
{eiocap:{soul_binder_power_use:2.222f}}
{eiocap:{soul_binder_sound_pitch:2.222f}}
{eiocap:{spawner_power_buffer:2.222f}}
{eiocap:{spawner_power_intake:2.222f}}
{eiocap:{spawner_power_use:2.222f}}
{eiocap:{spawner_speedup:2.222f}}
{eiocap:{stirling_power_buffer:2.222f}}
{eiocap:{stirling_power_gen:2.222f}}
{eiocap:{stirling_power_loss:2.222f}}
{eiocap:{stirling_power_time:2.222f}}
{eiocap:{transceiver_power_buffer:2.222f}}
{eiocap:{transceiver_power_intake:2.222f}}
{eiocap:{transceiver_power_use:2.222f}}
{eiocap:{vat_power_buffer:2.222f}}
{eiocap:{vat_power_intake:2.222f}}
{eiocap:{vat_power_use:2.222f}}
{eiocap:{weather_power_buffer:2.222f}}
{eiocap:{weather_power_fluid_use:2.222f}}
{eiocap:{weather_power_intake:2.222f}}
{eiocap:{weather_power_use:2.222f}}
{eiocap:{wired_power_buffer:2.222f}}
{eiocap:{wired_power_intake:2.222f}}
{eiocap:{wired_power_output:2.222f}}
{eiocap:{wireless_power_buffer:2.222f}}
{eiocap:{wireless_power_intake:2.222f}}
{eiocap:{wireless_power_output:2.222f}}
{eiocap:{zombie_power_buffer:2.222f}}
{eiocap:{zombie_power_gen:2.222f}}
{eiocap:{zombie_power_loss:2.222f}}
```

And the most specific way is to target a specific CapacitorKey by its name.

Note: This list only contains keys for enderio-machines. Keys for other sub-modules TBD.