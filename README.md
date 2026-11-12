# ZMK config: TOTEM (Keyboard Hoarders build)

ZMK firmware for my [Keyboard Hoarders TOTEM](https://keyboard-hoarders.com/products/totem-wireless-tented-resin-case), the Bluetooth version with Seeed XIAO nRF52840 controllers.

The shield files, keymap and settings come from the seller's config, [KeyboardHoarders/zmk-totem-config](https://github.com/KeyboardHoarders/zmk-totem-config). That config is based on [GEIGEIGEIST's TOTEM](https://github.com/GEIGEIGEIST/TOTEM). I changed one thing: the Bluetooth name is "Totem Keyboard" instead of "KBHTotem" (`config/totem.conf`).

## Where to edit

- `config/totem.keymap`: the keymap
- `config/totem.conf`: settings such as the Bluetooth name, sleep timeout and radio power
- `build.yaml`: the firmware files GitHub builds (left, right, settings_reset)
- `boards/shields/totem/`: the hardware definition (pins and layout). You shouldn't need to touch it.

Pushing to `main` builds the firmware on GitHub Actions. `zmk download` opens the Actions page.

## Flashing

Unzip `firmware.zip` from the latest successful run. Then, for each half:

1. Plug the half in over USB and double-press its reset button. A drive appears on the Mac.
2. Drag that half's file onto the drive. Use `totem_left-xiao_ble-zmk.uf2` for the left and `totem_right-xiao_ble-zmk.uf2` for the right. The drive ejects itself when it's done.

If the halves stop talking to each other or Bluetooth pairing gets stuck, flash `settings_reset-xiao_ble-zmk.uf2` onto **both** halves first, then flash left and right again. This wipes all pairings, so you'll have to pair the keyboard with your Mac again.
