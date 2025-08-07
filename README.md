# Phalanx 36: a Layout for the Kinesis Advantage 360 Pro

Reaching for keys sideways has always been difficult for my inflexible, stubby fingers. If that sounds familiar, then Phalanx was designed for you! Its core principle is to eliminate all lateral finger movement.

![Phalanx 36 Layout](/assets/layout.png)

## Features

0. **Zero Lateral Finger Movement**: To enforce strict columnar movement (true to the Phalanx name), each finger is assigned exactly one column.

1. **QWERTY Number One**: To reduce cognitive load for the most common migration path, the default keymap minimizes deviations from standard QWERTY letter positions. While the default is QWERTY-based, other keymaps like Dvorak or Colemak are easily adapted to the columnar philosophy.

2. **Two Strong Thumbs**: To maximize utility of the strongest digits, the two keys under each thumb are dual-purpose: they perform direct inputs (`Space`, `Backspace`, etc.) when tapped and switch layers when held.

3. **Three Compact Layers**: To make all layers easily accessible via the thumb keys, the entire keymap is organized into only three layers: a base layer for alphas, a symbol layer, and a navigation/numpad layer.

4. **A Home for All Four Modifiers**: To centralize control and eliminate dedicated modifier keys, all home-row keys are also dual-purpose: they perform as standard letter keys when tapped and act as modifiers (`Shift`, `Cmd`, `Ctrl`, `Option`) when held. `CapsLock` is toggled by double-tapping `Escape`.

## Motivation

![Adv360 Mod](/assets/modded-adv360.jpg)

My journey into split ergonomic keyboards began with the Advantage 360 Pro. The switch was revelatory, but it also surfaced a painful truth. And I mean **pain** in the physical sense.

As I disciplined myself to type "correctly" - with wrists stationary - I found that reaching sideways caused strain in my index and pinky fingers.

Phalanx grew out of my effort to eliminate that pain. By restricting each finger to its most natural forward-and-back motion and offloading work to the thumbs, this layout creates a typing experience that is finally comfortable for my hands. I'm sharing it in the hope that it can do the same for you.

## Download

You can find versions of the default keymap under [Releases](https://github.com/mkovaxx/phalanx36-for-Adv360-Pro/releases), or customize it and make your own build (see below).

See instructions below on how to flash the firmware onto your Adv360 Pro.

## How to Flash Your Adv360 Pro

Follow the programming instruction on page 8 of the [Quick Start Guide](https://kinesis-ergo.com/wp-content/uploads/Advantage360-Professional-QSG-v8-25-22.pdf) to flash the firmware.

1. Extract the firmware from the archive downloaded from GitHub.
1. Connect the left side keyboard to USB.
1. Press the reset button (see below) to put the left side into bootloader mode; it should attach to your computer as a USB drive.
1. Copy `left.uf2` to the USB drive and it will disconnect.
1. Power off both keyboards (by unplugging them and making sure the switches are off).
1. Turn on the left side keyboard with the switch.
1. Connect the right side keyboard to USB to power it on.
1. Press the reset button (see below) to put the right side into bootloader mode to attach it as a USB drive.
1. Copy `right.uf2` to the mounted drive.
1. Unplug the right side keyboard and turn it back on.
1. Enjoy!

> **Reset Button**: There are also physical reset buttons on both keyboards which can be used to enter and exit the bootloader mode. Their location is described in section 2.7 on page 9 in the [User Manual](https://kinesis-ergo.com/wp-content/uploads/Advantage360-ZMK-KB360-PRO-Users-Manual-v3-10-23.pdf) and use is described in section 5.9 on page 14.

> **Note**: Some operating systems wont always treat the drive as ejected after the settings-reset file is flashed or may throw a spurious error, this doesn't mean that the flashing process has failed.

## How to Customize and Build Your Own

1. Fork this repo.
2. Enable GitHub Actions on your fork.
3. Open your fork in [Keymap Editor](https://nickcoutsos.github.io/keymap-editor).
4. Edit the keymap.
5. Click `Save` to commit your changes and trigger a build.
6. Click the button next to `Save` to open the build run page.
7. Download the firmware from the Artifacts section at the bottom.

## Known Issues

### Battery Reporting

By default, reporting the battery level over BLE is disabled, as this can cause some computers to spontaneously wake up repeatedly. If you'd like to enable this functionality change `CONFIG_BT_BAS=n` to  `CONFIG_BT_BAS=y` in [adv360_left_defconfig](/config/boards/arm/adv360/adv360_left_defconfig#L58).

## Credits

Phalanx stands on the shoulders of the following giants:

- [Advantage 360 Pro by Kinesis](https://kinesis-ergo.com/shop/adv360pro): Inspired this layout and is the primary target for its implementation.
- [ZMK Firmware](https://github.com/zmkfirmware/zmk): Enables re-programming the Adv360 and supporting complex behaviors such as hold/tap.
- [Keymap Editor by nickcoutsos](https://github.com/nickcoutsos/keymap-editor): Helps edit ZMK keymap configurations. No need to understand ZMK internals or even programming.
- [Keyboard Layout Editor by ijprest](https://github.com/ijprest/keyboard-layout-editor): Helps visualize keyboard layouts and keymaps in a compact way.
