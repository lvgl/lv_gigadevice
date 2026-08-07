# LVGL on GigaDevice Development Boards

Board manifests for [GigaDevice](https://www.gigadevice.com/) evaluation boards
that are adapted to [LVGL](https://lvgl.io/).

This repository does **not** contain application source code. It is a metadata
repository: each supported GigaDevice board is described by one JSON manifest
together with its board image and the vendor logo. LVGL consumes these
manifests to present the boards publicly — for example in the
[LVGL project creator](https://lvgl.io/tools/project-creator) — so that users
can discover a GigaDevice board, see its MCU and display specifications, and
follow the steps to build the matching LVGL demo.

## Repository layout

```
lv_gigadevice/
├── manifests/      # one JSON manifest per board — the actual content of this repo
├── board_images/   # board photos referenced by the manifests
├── logo_images/    # GigaDevice logo referenced by the manifests
└── .github/        # CI workflows
```

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

## Manifest format

Every file in [manifests](manifests) is a single JSON object. These are the
fields LVGL reads when rendering a board entry.

| Field | Purpose |
| --- | --- |
| `name` | Board name shown to the user |
| `maintainer` | Who maintains the LVGL adaptation |
| `hostOperatingsystem` | Host operating systems the toolchain runs on |
| `environment` | Supported IDEs / build environments (MDK, IAR, GD32EmbeddedBuilder) |
| `hardware.chipVendor`, `hardware.manufacturer` | Chip vendor and board manufacturer |
| `hardware.specs` | MCU, RAM, Flash, GPU and display parameters (resolution, size, interface, color depth, technology, DPI, touch pad) |
| `description` | Long description of the board and how LVGL runs on it |
| `shortDescription` | One-line summary used in listings |
| `urlToClone` | Git repository holding the LVGL demo project for this board |
| `logos`, `image` | Raw URLs of the vendor logo and the board photo in this repository |
| `buy_now_links` | Where the board can be purchased |
| `branches` | LVGL release branches the project supports |
| `getStartedInstructions` | Steps to install an IDE, clone the project, build it and download it |
| `settings` | Options the project creator exposes when generating the project |

Display values in `hardware.specs` must come from the panel datasheet of the
board rather than from an estimate — `DPI` is derived from the pixel pitch and
`Technology` is the panel technology type (`a-Si TFT`, `IPS`, …).

## Adding a board

1. Add the board photo to [board_images](board_images), named after the board
   (for example `GD32F470I_EVAL.png`).
2. Copy an existing manifest to `manifests/<BOARD>.json` and fill in every
   field for the new board.
3. Point `image` and `logos` at the raw URLs of the files in this repository,
   and `urlToClone` at the repository that holds the board's LVGL demo project.
4. Check that the file is valid JSON and add the board to the
   [Supported boards](#supported-boards) table above.

## Getting started with a board

The manifests target IDE-based workflows. For a listed board:

1. Install one of the supported IDEs: MDK, IAR or GD32EmbeddedBuilder.
2. Clone the source code from the repository given by `urlToClone`.
3. Build the code with the IDE and download it to the development board.
