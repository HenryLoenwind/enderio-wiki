![](http://loenwind.info/eio/SAG_Mill.png)

Crushes items.  Used for ore doubling and as a crafting process.

Upgrade with capacitors to increase speed and energy storage.  Speed is directly related to RF/t.

| Capacitor           | RF/t | Buffer (RF) |
| :------------------ | ---: | ----------: |
| Basic (none)        |   20 |     100,000 |
| Double-Layer        |   60 |     300,000 |
| Octadic             |  100 |     500,000 |
| Good Loot Cap (4)   |  160 |     800,000 |
| Theoretical Max (5) |  200 |   1,000,000 |

# Grinding Balls

The slot on the right side of the GUI is for Grinding Balls.  Grinding balls provide bonus outputs and reduced power use.  The Grinding Ball is consumed when it is first used by an appropriate recipe and must be fully used up before it can be replaced.

| Grinding Ball       | Main Output | Bonus Output | Power Reduction | Durability (RF) |
| :------------------ | ----------: | -----------: | --------------: | --------------: |
| Flint               |        120% |         125% |             15% |          24,000 |
| [[Dark Steel Ball]] |        150% |         200% |             30% |         100,000 |

Grinding Balls are only used in certain recipes determined by the recipe's bonus type.  If the recipe's bonus type is set to none (like Iron Ingot -> Iron Powder) then the Grinding Ball is not used (no increased output chance, no power reduction, and no durability used by the Grinding Ball).

* Main Output: The recipe output will be produced this many times.  Applies to all outputs.  For example, using dark steel (Main Output: 150%) will produce 1 set of items with a 50% chance of producing a second set.

* Bonus Output: The chances of the different outputs of the recipe are multiplied by this.  Only applies to outputs with a chance of appearing.  maxes out at a 100% chance, and is applied before the Main Output multiplier.

* Power Reduction:  Decreases energy cost of the recipe by the specified amount.  This indirectly speeds up the SAG Mill, and also affects the durability of the Grinding Balls.

* Durability: Specifies how long a Grinding Ball will last.  Measured in RF used by the SAG Mill.  Not visible in the game.

## Grinding Ball Example

The SAG Mill will process 1 Diamond Ore at the cost of 3,000 RF.  It will produce 1 Diamond, has a 25% chance of producing a second Diamond, a 15% chance of producing Cobblestone, and a 5% chance of producing Coal Powder.

If you use a Dark Steel Ball, then the power is reduced by 30%, down to 2,100 RF.  If you are using an Octadic Capacitor, then the SAG Mill processes at 100RF/t, meaning it takes 21 ticks (1.05 seconds) to process the ore rather than the previous 30 ticks (1.50 seconds).  The Dark Steel Ball will consume 2,100 points of durability (out of its maximum of 100,000).

The Bonus Output increases chance based outputs by 200%.  The first Diamond doesn't benefit from the Bonus Output as it isn't chance based.  The second Diamond now has a 50% chance of being created.  Cobblestone is increased to a 30% chance, and Coal Powder is increased to a 10% chance.

The Main Output bonus of 150% is applied to all items.  The first Diamond will always produce 1 Diamond with a 50% chance of another.  The second Diamond will produce depending on the original chance, with a 50% chance of doubling that output; On average, that will be 50% * 150% = 75%.  Cobblestone similarly averages out to 45%, and Coal Powder to 15%.

The end result will be an average of 1.5 Diamonds per ore from the first Diamond, and 0.75 Diamonds per ore from the second Diamond, resulting in an average of 2.25 Diamonds per ore.  For reference, Fortune III averages out to 2.20 Diamonds per ore.