# nakamochi 3D designs

at the moment, there's only an FFF (Fused Filament Fabrication) design suitable
for 3D printing at home in the [fff](fff/) directory.

all design sources are made in [freecad](https://freecad.org/) no older than v0.20.
a stock installation of freecad should be sufficient but you might want to install
[fasteners workbench](https://wiki.freecadweb.org/Fasteners_Workbench) if working on
a design assembly.

## fff

the main file is in [fff/provcase.FCStd](fff/provcase.FCStd). "provcase" stands for
"provisional case" because it is still unclear whether this will be a final design.

the project contains all the parts to make a full assembly with the following BOM:

- [raspberry pi 4 model b](https://www.raspberrypi.com/products/raspberry-pi-4-model-b/)
- [waveshare 4.3inch DSI LCD](https://www.waveshare.com/wiki/4.3inch_DSI_LCD)
- [joi-it armor "block" heatsink](https://joy-it.net/en/products/RB-AlucaseP4+07)
- [sandisk portable 1TB SSD sdssde30-1t00](https://www.westerndigital.com/en-in/products/portable-drives/sandisk-usb-3-2-ssd)

all object constraints reference an embedded spreadsheet `params` to avoid 
[topological naming problem](https://wiki.freecadweb.org/Topological_naming_problem).
prefer constraining against datum objects instead of faces and other elements produced
directly from sketches like pads.

finally, the [fff/provcase-assembly.FCStd](fff/provcase-assembly.FCStd) file contains
an "assembly" group. this is simply a collection of parts composed together to help
visualize how and whether all of them fit well together. it links to the provcase.FCStd,
so you'll need both files. this assembly group calculates all placement offsets from
`asmsheet` spreadsheet. here's how the assembly looks like:

![provisional fff case assembly](fff/provcase-assembly.png)

the "assembly" std part has a custom property "view" with two options: exploded and
assembled. the property is configured from the same asmsheet.

### 3D printing the parts

> TODO: insert here acceptable 3D printer specs and an assembly guide

## assets

various files are placed in the [assets](assets/) to use in an assembly composition.
for example, you'll find a 4.3inch display, raspberry pi 4 and a heatsink in there.

when creating a design assembly, make a new [std part](https://wiki.freecad.org/Std_Part)
group and import desired assets into it. if an asset is in a freecad file format,
open the file and drag&drop the top level object into the newly created std part.
then close the original file ignoring the changes.

## license

[CC-BY 4.0](https://creativecommons.org/licenses/by/4.0/)
