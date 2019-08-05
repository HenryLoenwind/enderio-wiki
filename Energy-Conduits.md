# Energy Conduits

The Energy Conduits transfer µI between capacitor banks/machines.

## There are 3 types of Fluid Conduits:

### Energy Conduit
![](http://loenwind.info/eio/Energy_Conduit.png)

This is the first tier.

It has a Max Output of 640 µI/t.

### Enhanced Energy Conduit
![](http://loenwind.info/eio/Enhanced_Energy_Conduit.png)

This is the second tier.

It has a Max Output of 5,120 µI/t.

### Ender Energy Conduit
![](http://loenwind.info/eio/Ender_Energy_Conduit.png)

This is the third tier.

It has a Max Output of 20,480 µI/t.

## The GUI of all Energy conduits is split between their 2 modes: *insert* and *extract*. These modes can be toggled independently.
![Energy Conduit GUI](https://github.com/paul-soporan/enderio-wiki/blob/master/images/GUIs/Energy-Conduit-GUI.png)

### Insert

Insertion has no additional settings.

### Extract

#### Redstone Mode (*1*)

Controls when the extraction should happen in regards to *Redstone Signal*. It can be set to these modes:

##### Always active
Extraction is always active, ignoring redstone signal.

##### Active with signal
Extraction only happens if the conduit receives a redstone signal(power 1-15).

If the redstone signal is transmitted by a redstone conduit, the Signal Color can be set.

##### Active without signal
Extraction only happens if the conduit doesn't receive a redstone signal(power 0).

If the redstone signal is transmitted by a redstone conduit, the Signal Color can be set.

##### Never active
Extraction is never active, ignoring redstone signal.
