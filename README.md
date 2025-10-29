# **One-Handed Keyboard**

> The original project owner received an unusual email. The sender's daughter was run over by a heavy truck on her way to school and permanently lost the use of her right hand. She now has to constantly move between the keyboard and mouse when she uses a computer, which is slow and exhausting. He asked us to help him build a one-handed keyboard for his daughter.

![Left-hand small keyboard](/Docs/Image/左手小键盘右侧面.jpg "Left-hand small keyboard")

![Left-hand large keyboard](/Docs/Image/左手大键盘右侧.jpg "Left-hand large keyboard")

This is a single-mode mechanical keyboard with an integrated trackball. The firmware is powered by [QMK](https://github.com/qmk/qmk_firmware). Many thanks to all of the developers who contribute to the QMK community.

Keyboard build reference: [He Tongxue – We made a special keyboard…](https://www.bilibili.com/video/BV1DtjAzUEb9)

Open-source hardware: [HTXStudio One-Handed Keyboard](https://oshwhub.com/htx-studio/One-Handed_Keyboard)

[GitHub repository](https://github.com/htx-studio/One-Handed-Keyboard)

[Gitee repository](https://gitee.com/htxstudio/one-handed-keyboard)

See the environment setup guide [here](https://docs.qmk.fm/newbs_getting_started "Set up your QMK environment"). The firmware source code can be found [here](https://github.com/htx-studio/qmk_firmware/tree/master/keyboards/htx_studio).

This repository contains:

* Eight PCBs for three keyboard variants (left-hand small, left-hand large, right-hand large), along with the LCSC EDA projects.
* VIA remapping configuration files and precompiled firmware.
* Model design files.

---

## Repository Structure

#### Docs (Documentation)

Datasheets and photos for the components.

#### Firmware

QMK firmware for the three keyboard variants, plus the JSON files for VIA remapping.

#### Hardware

Project files for JLCEDA.

#### Model

Model and machining files used by each keyboard variant.

---

## Build Guide

### PCBs

1 – Right-hand keyboard – hot-swappable (large): FR-4 board, 1.6 mm thickness, four layers, stack-up JLC04161H-3313, impedance control ±20%.

1 – Left-hand keyboard – soldered (small): FR-4 board, 1.6 mm thickness, two layers. ALPS yellow switches require a bit of force to seat fully.

1 – Left-hand keyboard – hot-swappable (large): FR-4 board, 1.6 mm thickness, four layers, stack-up JLC04161H-3313, impedance control ±20%.

2 – USB Type-C: FR-4 board, 1.6 mm thickness, two layers, labeled CON1 (large keyboard only).

3 – Trackball: FR-4 board, 1.6 mm thickness, two layers. Pay attention to the module orientation while soldering. Labeled CON3.

4 – Scroll wheel: FR-4 board, 1.6 mm thickness, two layers. Use a 7 mm encoder and 6 mm buttons with ≤180 g actuation force. Labeled CON2.

5 – Directional keys: FR-4 board, 1.6 mm thickness, two layers. ALPS yellow switches require a bit of force to seat fully. Labeled CON4.

6 – Main control board – left hand (small): FR-4 board, 1.6 mm thickness, two layers.

> * Items 3, 4, and 5 are shared daughterboards for keyboard control.
> * The directional keys board (`5 – Directional keys`) and the small left-hand keyboard (`1 – Left-hand keyboard – soldered`) both use ALPS yellow switches.
> * The large left- and right-hand keyboards are not perfect mirrors of each other.
> * The trackball uses the SPI1 channel, and the scroll wheel has two dedicated signal lines, making it easier to swap in other pointing devices without major changes.
> * The MCU is an STM32G431CBU6.
> * Compatible with both A-to-C and C-to-C cables.

### Printed Parts

Keycaps: resin, PLA, or similar materials.

Trackball holder: resin, PLA, or similar materials.

Mouse buttons: resin, PLA, or similar materials.

Case: resin, PLA, or similar materials.

Base: resin, PLA, or similar materials.

### Padding and Dampening

Positioning plate: recommended material POM, 1.5 mm thickness.

Positioning plate foam strips: adhesive on one side.

Mid-layer foam: recommended material Poron, 3.5 mm thickness.

Switch plate foam: 2 mm thickness.

Bottom foam: recommended material Poron, 4 mm thickness.

Silicone pad (small keyboard only): 5 mm thickness, Shore 00-10 hardness.

### Hardware

|                          | Quantity – large keyboard | Quantity – small keyboard |
| :----------------------- | :-----------------------: | :-----------------------: |
| M3×3×4 heat-set inserts  |             8             |             8             |
| M2×2×3 heat-set inserts  |             2             |             -             |
| M2×3×3 heat-set inserts  |            17             |            12             |
| M3×6 countersunk screws  |             2             |             6             |
| M3×15 countersunk screws |             -             |             4             |
| M3×22 countersunk screws |             6             |             -             |
| M2×8 button-head screws  |             4             |             4             |
| M2×3 button-head screws  |             2             |             -             |
| M2×5 button-head screws  |            13             |             8             |
| M3×16 flat-head screws   |             -             |             2             |

### Other Components

Trackball: 25 mm diameter, PTFE material.

Support balls: 2 mm diameter, PTFE material. Install six pieces in the printed trackball seat.

Scroll wheel: 19–20 mm diameter, 4–5 mm thickness, metal material recommended.

Stabilizers: 2U plate-mount stabilizers.

Switches: small keyboard uses 57 ultra-compact ALPS yellow switches; large keyboard uses 57 standard mechanical switches.

FPC cables: 0.5 mm pitch, 8-pin reverse, two 10 cm cables and two 15 cm cables.

> * FPC connectors on the control board and daughterboards are labeled CON to help match the connections.
> * The provided files use top- and bottom-entry FPC connectors. If both connectors are bottom-entry, use reverse cables to connect them.

### Model Structure

![Left-hand small keyboard exploded view](/Docs/Image/左手小键盘爆炸图.jpg "Left-hand small keyboard exploded view")

![Left-hand large keyboard exploded view](/Docs/Image/左手大键盘爆炸图.jpg "Left-hand large keyboard exploded view")

### Assembly Sequence

> Large keyboard example

**Preparation before assembly**

* Connect the four daughterboards to the main PCB with ribbon cables and flash the firmware.
* Install 3–5 switches along with the scroll wheel and trackball to verify the functions before final assembly.
* Install the correct heat-set inserts in the printed case and base.
* Add legends to the keycaps.
* Apply foam strips to the raised sections of the positioning plate (both sides).

> To flash the firmware for the first time, hold the button labeled "B" on the back of the PCB while plugging in the USB cable.
>
> To update the firmware later, hold the "ESC" key while plugging in the USB cable.
>
> See [Flashing Your Keyboard (QMK)](https://docs.qmk.fm/newbs_flashing) for more details.

**Assembly steps**

1. Mount the four daughterboards in the base with screws (watch the cable routing and orientation). The trackball seat is fastened from underneath.
2. Secure the left and right mouse buttons to the main PCB with screws.
3. Stack the layers in the base’s fan-shaped section from bottom to top: bottom foam, switch plate foam, main PCB, mid-layer foam, positioning plate.
4. Insert the keyboard switches.
5. Place the case on top and fasten it from below with screws.
6. Install the keycaps to complete the build.

> See [this guide](https://github.com/htx-studio/One-Handed-Keyboard/tree/main/Model) for installing the screws and heat-set inserts.

This is our first open-source project. We welcome your feedback and suggestions—thank you for your support.

---

## References

[Quantum Mechanical Keyboard Firmware](https://docs.qmk.fm/)

mrjohnk. ADNS-9800. [GitHub repository](https://github.com/mrjohnk/ADNS-9800/)
