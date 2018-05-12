![](http://loenwind.info/eio/SAG_Mill.png)

Crushes items.  Used for ore doubling and as a crafting process.

Upgrade with [[capacitors]] to increase speed and energy storage.  Speed is directly related to µI/t.

| Capacitor           | µI/t | Buffer (µI) |
| :------------------ | ---: | ----------: |
| Basic               |   20 |     100,000 |
| Double-Layer        |   60 |     300,000 |
| Octadic             |  100 |     500,000 |
| Good Loot Cap (4)   |  160 |     800,000 |
| Theoretical Max (5) |  260 |   1,300,000 |

# Grinding Balls

The slot on the right side of the GUI is for Grinding Balls.  Grinding balls provide bonus outputs and adjust power usage.  The Grinding Ball is consumed when it is first used by an appropriate recipe and must be fully used up before it can be replaced.

| Grinding Ball         | Main Output | Bonus Output | Power Use | Durability (µI) |
| :-------------------- | ----------: | -----------: | --------: | --------------: |
| Flint                 |        120% |         125% |       85% |          24,000 |
| Dark Steel Ball       |        135% |         200% |       70% |         125,000 |
| Electrical Steel Ball |        120% |         165% |       80% |          40,000 |
| Energetic Alloy Ball  |        160% |         110% |      110% |          80,000 |
| Vibrant Alloy Ball    |        175% |         135% |      135% |          80,000 |
| Redstone Alloy Ball   |        100% |         100% |       35% |          30,000 |
| Conductive Iron Ball  |        135% |         100% |      100% |          40,000 |
| Pulsating Iron Ball   |        100% |         185% |      100% |         100,000 |
| Soularium Ball        |        120% |         215% |       90% |          80,000 |
| End Steel Ball        |        140% |         240% |       70% |          75,000 |


Grinding Balls are only used in certain recipes determined by the recipe's bonus type.  If the recipe's bonus type is set to none (like Iron Ingot -> Iron Powder) then the Grinding Ball is not used (no increased output chance, no power reduction, and no durability used by the Grinding Ball).

* Main Output: The recipe output will be produced this many times.  Applies to all outputs.  For example, using dark steel (Main Output: 150%) will produce 1 set of items with a 50% chance of producing a second set.

* Bonus Output: The chances of the different outputs of the recipe are multiplied by this.  Only applies to outputs with a chance of appearing, maxes out at a 100% chance, and is applied before the Main Output multiplier.

* Power Use:  Adjusts energy cost of the recipe by the specified amount.  This indirectly changes the speed of the SAG Mill, and also affects the durability of the Grinding Balls.

* Durability: Specifies how long a Grinding Ball will last.  Measured in µI used by the SAG Mill.  Not visible in the game.

### Add-on Grinding Balls

The following Grinding Balls are added by Ender IO, but are dependent on materials from other mods.

| **Thermal Expansion** | **Main Output** | **Bonus Output** | **Power Use** | **Durability (µI)** |
| :-------------------- | --------------: | ---------------: | ------------: | ------------------: |
| Signalum              |            120% |             165% |           35% |             100,000 |
| Enderium              |            165% |             145% |          125% |             120,000 |
| Lumium                |            110% |             215% |           90% |             100,000 |

## Grinding Ball Example

The SAG Mill will process 1 Diamond Ore at the cost of 3,600 µI.  It will produce 2 Diamonds, has a 25% chance of producing an auxiliary Diamond, a 15% chance of producing Cobblestone, and a 5% chance of producing Coal Powder.

If you use a Dark Steel Ball, then the recipe only needs 70% of the base power, down to 2,520 µI.  If you are using an Octadic Capacitor, then the SAG Mill processes at 100 µI/t, meaning it takes 25.2 ticks (1.26 seconds) to process the ore rather than the previous 36 ticks (1.80 seconds).  The Dark Steel Ball will consume 2,520 points of durability (out of its maximum of 125,000).

The Bonus Output increases chance based outputs by 200%, maxing at 100%.  The first two Diamonds don't benefit from the Bonus Output as they are already at 100%.  The auxiliary Diamond now has a 50% chance of being created.  Cobblestone is increased to a 30% chance, and Coal Powder is increased to a 10% chance.

The Main Output bonus of 135% is applied to all items.  There is a 35% chance of doubling the entire output.

The end result will be an average of 2.7 Diamonds per ore from the primary set, and 0.675 Diamonds per ore from the auxiliary Diamond, resulting in an average of 3.375 Diamonds per ore.  For reference, Fortune III averages out to 2.20 Diamonds per ore, and a SAG Mill with no Grinding Ball would produce an average of 2.25 Diamonds per ore.