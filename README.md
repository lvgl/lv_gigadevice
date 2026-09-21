# LVGL support for GigaDevice Development Boards

This repository contains descriptions for [GigaDevice](https://www.gigadevice.com/) development boards as [manifest JSON files](manifests)
and a getting started guide to create ready-to-use LVGL projects for the supported development boards.

## Supported boards

| Board | Manifest | MCU | Display |
| --- | --- | --- | --- |
| GD32C231-EVAL | [manifests/GD32C231_EVAL.json](manifests/GD32C231_EVAL.json) | GD32C231 (Cortex-M23, 48MHz) | 2.2" 240x320, SPI |
| GD32F470-EVAL | [manifests/GD32F470_EVAL.json](manifests/GD32F470_EVAL.json) | GD32F470 (Cortex-M4, 240MHz) | 4.3" 480x272, TLI |
| GD32F503-EVAL | [manifests/GD32F503_EVAL.json](manifests/GD32F503_EVAL.json) | GD32F503 (Cortex-M33, 252MHz) | 3.2" 240x320, 8080|
| GD32F527-EVAL | [manifests/GD32F527_EVAL.json](manifests/GD32F527_EVAL.json) | GD32F527 (Cortex-M33, 200MHz) | 4.3" 480x272, TLI |
| GD32F5HC-EVAL | [manifests/GD32F5HC_EVAL.json](manifests/GD32F5HC_EVAL.json) | GD32F5HC (Cortex-M33, 200MHz) | 2.2" 240x320, SPI |
| GD32H759-EVAL | [manifests/GD32H759_EVAL.json](manifests/GD32H759_EVAL.json) | GD32H759 (Cortex-M7, 600MHz) | 4.3" 480x272, TLI|
| GD32VW553-EVAL | [manifests/GD32VW553_EVAL.json](manifests/GD32VW553_EVAL.json) | GD32VW553 (RISC-V, 160MHz) | 2.2" 320x240, SPI |
| GD32W515-EVAL | [manifests/GD32W515_EVAL.json](manifests/GD32W515_EVAL.json) | GD32W515 (Cortex-M33, 180MHz) | 2.2" 320x240, SPI|

## Getting started with a board

> [!WARNING]
> The projects still use **LVGL v8.3.11**. They have not been migrated to LVGL v9 yet.

### Prerequisites:

Install one of the supported IDEs:
- [MDK](https://www.keil.com/)
- [IAR](https://www.iar.com/)
- [GD32EmbeddedBuilder](https://www.gd32mcu.com/en/download/7)

### Getting a ready-to-use project

1. Visit [GigaDevice's GitHub Organization](https://github.com/GigaDevice-GD32-MCU/?q=_LVGL&type=all&language=&sort=) and search for `LVGL` among the repositories
2. Clone a repository for your development board
3. Build the code with the IDE and flash it to the development board.

## Adding a board

1. Add the board photo to [board_images](board_images), named after the board
   (for example `GD32F470I_EVAL.png`).
2. Copy an existing manifest to `manifests/<BOARD>.json` and fill in every
   field for the new board.
3. Point `image` and `logos` at the raw URLs of the files in this repository,
   and `urlToClone` at the repository that holds the board's LVGL demo project.
4. Check that the file is valid JSON and add the board to the
   [Supported boards](#supported-boards) table above.

## Support

In case of any issues, please open an issue in this repository.
