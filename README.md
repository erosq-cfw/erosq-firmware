# erosq-firmware

Wi-Fi and Bluetooth chip firmware for the EROS Q (AzureWave AW-NM372SM,
Cypress/Infineon CYW43438), as used by
[erosq-buildroot](https://github.com/erosq-cfw/erosq-buildroot).

| file | what |
|---|---|
| `firmware/cyw43438-7.46.58.35.bin` | Wi-Fi firmware (brcmfmac) |
| `firmware/nvram_azw372.txt` | Wi-Fi NVRAM (board calibration) |
| `firmware/wifimac.txt` | NVRAM `macaddr` value the stock image uses |
| `lib/firmware/BCM4343A1_001.002.009.0122.0538.hcd` | Bluetooth patchram |

## Origin

The files are copied byte for byte, unmodified, from the stock HiBy EROS Q
firmware v2.2 (`update_erosQ_v2.2-rbuninstall.upt`, `SYSTEM.UBI`), at the
paths shown. `SHA256SUMS` lists their hashes, and erosq-buildroot's
`package/erosq-board/extract-stock-firmware.py` pins the same values.

They contain no per-device data. The firmware and NVRAM are identical on
every unit. The `macaddr` in `wifimac.txt` is a vendor constant that the chip
ignores: each module's real Wi-Fi and Bluetooth addresses are in its own OTP.

## Licence

None. These files come with no licence from their authors and are
redistributed as-is, solely so the firmware works on hardware its owners
already have. They are not covered by the MIT licence of the erosq-cfw
projects. If you are a rights holder and want them removed, open an issue.

Builds don't need this repository: without it, erosq-buildroot builds an
image with Wi-Fi and Bluetooth disabled, or takes the files from a stock
image you supply.
