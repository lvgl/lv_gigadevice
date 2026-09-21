# Manifests

Every file in this folder is a single JSON object. These are the
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
