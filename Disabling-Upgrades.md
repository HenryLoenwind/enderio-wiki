# Disabling Dark Steel Upgrades

Disabling Dark Steel Upgrades can be done in 2 ways:

## 1. By editing the `enderio.cfg` file in the `config/enderio` folder.

To edit this file, do the following:
* Open the file with an editor (eg. VS Code, Sublime Text, Notepad++, even Notepad)
* Press CTRL+F (or the key combination which enables you to search text in a file)
* Enter: `upgrades`
* Go to the line: `S:disabled=`
* Add the [IDs](#id-table) of the upgrades you wish to disable after the `=`, separated by a `,`.
  - You can enter *any* upgrade's [ID](#id-table) here. It doesn't matter if the upgrade is for armor, tools or weapons.
  - Example: To disable the Elytra Upgrade and the Flippers Upgrade, the line has to be:
  `S:disabled=enderio:elytra,enderio:swim`.
* Save the file (Ctrl+S)

### ID table:

| Name                   | ID                                              |
| ---------------------- | ----------------------------------------------- |
| Micro Anvil            | enderio:anvil                                   |
| Mini Anvil             | enderio:anvil1                                  |
| Pocket Anvil           | enderio:anvil2                                  |
| Carpeting              | enderio:carpet                                  |
| Depth                  | enderio:depth                                   |
| Direct                 | enderio:direct                                  |
| Elytra                 | enderio:elytra                                  |
| Empowered              | enderio:energyupgrade                           |
| Empowered II           | enderio:energyupgrade1                          |
| Empowered III          | enderio:energyupgrade2                          |
| Empowered IV           | enderio:energyupgrade3                          |
| Empowered V            | enderio:energyupgrade4                          |
| Glider                 | enderio:glide                                   |
| Fork                   | enderio:hoe                                     |
| Inventory I            | enderio:inv                                     |
| Inventory II           | enderio:inv1                                    |
| Inventory III          | enderio:inv2                                    |
| Jump                   | enderio:jumpboost1                              |
| Jump II                | enderio:jumpboost2                              |
| Jump III               | enderio:jumpboost3                              |
| Night Vision           | enderio:nightvision                             |
| Padding                | enderio:padding                                 |
| Simple Solar           | enderiomachines:solar                           |
| Solar I                | enderiomachines:solar1                          |
| Solar II               | enderiomachines:solar2                          |
| Solar III              | enderiomachines:solar3                          |
| Sound Locator          | enderio:sounddetector                           |
| Speed                  | enderio:speedboost1                             |
| Speed II               | enderio:speedboost2                             |
| Speed III              | enderio:speedboost3                             |
| Spoon                  | enderio:spoon                                   |
| Step Assist            | enderio:step_assist                             |
| Flippers               | enderio:swim                                    |
| Explosive I            | enderio:tnt                                     |
| Explosive II           | enderio:tnt1                                    |
| Explosive III          | enderio:tnt2                                    |
| Explosive IV           | enderio:tnt3                                    |
| Explosive V            | enderio:tnt4                                    |
| Travel                 | enderio:travel                                  |
| The One Probe          | enderio:top                                     |
| Naturalist's Eye       | enderiointegrationforestry:naturalist_eye       |
| Apiarist's Hat         | enderiointegrationforestry:apiarist_armor_head  |
| Apiarist's Shirt       | enderiointegrationforestry:apiarist_armor_chest |
| Apiarist's Pants       | enderiointegrationforestry:apiarist_armor_legs  |
| Apiarist's Shoes       | enderiointegrationforestry:apiarist_armor_feet  |
| Revealing              | enderio:gogglesofrevealing                      |
| Thaumaturge's Robe     | enderio:thaumaturge_robe_chest                  |
| Thaumaturge's Leggings | enderio:thaumaturge_robe_legs                   |
| Thaumaturge's Boots    | enderio:thaumaturge_robe_feet                   |

## 2. By removing the crafting recipe for a Dark Steel Upgrade

**This is the better way to do it, since it has less chance of having unintended side effects.**

***The one downside is that upgrade items will still be generated as (and on) dungeon loot. Only disabling the upgrades as shown above (or disabling the dungeon loot completely) will prevent that.***

**To disable the dungeon loot, follow this link: [Disabling Dungeon Loot](https://github.com/SleepyTrousers/EnderIO/tree/master/enderio-base/src/main/resources/assets/enderio/loot_tables/chests)**

To disable a DSU recipe, do the following:
* Copy the file `config/enderio/recipes/darksteel_upgrades.xml` to `config/enderio/recipes/user`
* Find the recipe you want to disable
* Add `disabled="true"` inside the `<recipe>` tag
  - Example: To disable the Elytra Upgrade, the Elytra `<recipe>` should look like this:
  ```xml
    <recipe required="true" name="Dark Steel Upgrade: Elytra" disabled="true">
      <dependency upgrade="enderio:elytra"/>
      <crafting>
        <shapeless>
          <item name="enderio:item_dark_steel_upgrade:0"/><item name="minecraft:elytra"/>
        </shapeless>
        <output name="enderio:item_dark_steel_upgrade:1" nbt='{"enderio:dsu":"enderio:elytra"}'/>
      </crafting>
    </recipe>
  ```
* Save the file (Ctrl+S)