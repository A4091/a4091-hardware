# A4091 hardware

This project contains Schematics and PCBs for the ReA4091 board,
which is a reimplementation of the Commodore A4091 SCSI controller
for the A4000 and A3000.

## EasyEDA

In the `easyeda/` directory you will find the PCB and schematics files in
EasyEDA's json format. You can load these files into your EasyEDA instance to
work on them.

| Filename                        | Explanation |
|---------------------------------|-------------|
| PCB_ReA4091_RevXX_YYYYMMDD.json | PCB         |
| SCH_ReA4091_RevXX_YYYYMMDD.json | Schematics  |

## Production Files

### BOM

The BOM is available as a CSV file exported by EasyEDA. You can also check out
the [Interactive BOM](https://scsi.me/bom.html).

### Gerber

Upload the Gerber Zip file to the manufacturing house of your choice. *NOTE:*
You will most likely see the price increase after a manual review of the design
because the integrated active SCSI-2 terminator is considered a second design.

#### Recommendations

When ordering PCBs, the following values are suggested.

- PCB thickness: 1.6mm
- Layers: 4
  - L1 (Top layer): `Gerber_TopLayer.GTL`
  - L2 (Inner layer 1): `Gerber_InnerLayer1.G1`
  - L3 (Inner layer 2): `Gerber_InnerLayer2.G2`
  - L4 (Bottom layer): `Gerber_BottomLayer.GBL`
- Different Designs: 2
- Surface finish: ENIG
- Gold Fingers: Yes
- 45 degree finger chamfered: Yes
- Material Type: FR-4 TG155
- Remove Order Number: Yes
- High-definition Exposure Silkscreen

### Pick And Place

There are three variants of PickAndPlace files in this repository:
- PickAndPlace_ReA4091_RevX_YYYYMMDD.csv
- PickAndPlace_ReA4091_RevX_YYYYMMDD_panelized_coordinates.csv
- PickAndPlace_ReA4091_RevX_YYYYMMDD_panelized_coordinates_mirror.csv
Please discuss with your fab house which one to use.

## Schematics

The `schematics/` directory contains the latest schematics in PDF format.

## Assembly

*NOTE:* The design has two footprints for a polyfuse: F309A is a through-hole
footprint and is the same as what Commodore and DKB used in their original
boards (the big yellow coin). If you prefer a sleeker look, it is recommended
to go with an SMD polyfuse on F309B instead. Do not stuff both.

For the ROM using a Winbond W27C512 is highly recommended as it is an EEPROM
version that can be erased without an ultraviolet light box.

### GALs

For the GALs, we have used ATF22V10-10 parts for all parts except for U306 and
U205. If you use Atmel GALs for those two parts, the card will *NOT* work
correctly.

- U306 should be a Lattice 22V10-6 or 22V10-7 (-10 will work in many
  instances).
- U205 should be a Lattice 22V10-15 part.

If you are familiar with WinCUPL and/or the Zorro III bus protocol, and can
help us debug why Atmel parts don't work in these positions, please [contact
us](mailto:a4091@amiga.technology)


