# Kindle Toolbox

Personal Kindle setup and configuration notes for Kindle 11th Gen 2024 (KT6).

## Device

| Item | Value |
| --- | --- |
| Model | Kindle 11th Generation, 2024 Release |
| KindleModding code | KT6 |
| Firmware | 5.19.6 |
| Jailbreak | ✅ Verified — Véra |

## Current Setup

| Component | Purpose | Status |
| --- | --- | --- |
| KOReader | EPUB/PDF reader and local library | ✅ Verified |
| Reading Statistics | Reading time, history, calendar, and daily records | ✅ Verified |
| WeRead plugin | WeRead bookshelf, downloads, and cached offline reading | ✅ Verified |
| FileSync | Wireless EPUB transfer from a phone | ✅ Verified |
| Custom Screensaver | PNG screensavers and rotation | ✅ Verified |
| SimpleUI | KOReader home screen and reading overview | ✅ Verified |

## Library Management

- Calibre 9.15.0 is the long-term master library manager.
- Calibre main library: `D:\Calibre Library`
- Calibre EPUB routing to `Internal Storage\KOReader_Library` is verified on this KT6.
- KOReader remains the reading, progress, statistics, and Collections layer; the current Kindle library contains 73 EPUB files.
- FileSync remains available for temporary phone-to-Kindle transfers.
- Calibre classifications and KOReader Collections are independent data and are synchronized only through an explicit, reviewed workflow.
- See [Calibre + KOReader library management](docs/calibre-library-management.md) for the verified workflow, field design, taxonomy, backup rules, and Collections process.

## What This Repository Is

This repository records the setup that has been tested on one personal Kindle. It contains:

- device and jailbreak notes;
- installed third-party projects and plugins;
- paths and directory conventions;
- repeatable usage and recovery notes;
- troubleshooting based on observed behavior.

It does not reimplement Kindle software or vendor copies of third-party source code.

## Directory

- [Current setup](docs/current-setup.md)
- [Calibre + KOReader library management](docs/calibre-library-management.md)
- [Device information](docs/device-info.md)
- [Plugins and third-party projects](docs/plugins.md)
- [Jailbreak compatibility record](docs/jailbreak-compatibility.md)
- [KOReader and WeRead](docs/koreader-weread.md)
- [Wireless transfer](docs/wireless-transfer.md)
- [Custom screensaver](docs/screensaver.md)
- [Troubleshooting](docs/troubleshooting.md)
- [Roadmap](docs/roadmap.md)
- [Historical solution comparison](docs/solution-comparison.md)

## Third-party Projects

- [KOReader](https://github.com/koreader/koreader)
- [WeRead KOReader plugin](https://github.com/finlater/weread.koplugin)
- [FileSync KOReader plugin](https://github.com/abrahamnm/filesync.koplugin)
- [Kindle Custom Screensaver](https://github.com/chengandre/kindle-custom-screensaver)
- [SimpleUI KOReader plugin](https://github.com/doctorhetfield-cmd/simpleui.koplugin)

These projects are maintained by their respective authors. This repository only records installation, configuration, and results on the device described above. Third-party code and copyrights remain with their original authors.

## Notes

- `✅ Verified` means tested on this specific KT6 device and current environment only.
- Unknown versions or sources are marked `Needs verification` instead of being guessed.
- No API keys, cookies, tokens, QR contents, serial numbers, Wi-Fi MAC addresses, or account details belong in this repository.
