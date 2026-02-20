# Build with MPLAB X and XC32 GitHub Action

This action will build a MPLAB X / XC32 project.

It runs on Linux Ubuntu latest and uses:

* [MPLAB X](https://www.microchip.com/en-us/development-tools-tools-and-software/mplab-x-ide)
* [XC32](https://www.microchip.com/en-us/development-tools-tools-and-software/mplab-xc-compilers)

## Inputs

### `mplabx_version`

Version of MPLAB X to use. Defaults to `6.20`.

### `xc32_version`

Version of the XC32 compiler to use. Defaults to `4.60`.

### `dfp_packs`

Optional comma-separated list of packs to install in the format `PACK_NAME=VERSION`.

### `project`

**Required** The path of the project to build (relative to the repository). For example: `/github/workspace`.

### `configuration`

The configuration of the project to build. Defaults to `default`.

## Outputs

None.

## Example Usage

Add the following `.github/workflows/build.yml` file to your project:

```yaml
name: Build

on:
  pull_request:
    branches: [ "main", "dev" ]

jobs:
  build:
    name: Build the project
    runs-on: ubuntu-latest
    steps:
      - name: Checkout code
        uses: actions/checkout@v4

      - name: UAMP Build with MPLAB X and XC32
        uses: uampio/mplabx-xc32-build-action@v1.0.46
        with:
          project: /github/workspace
          dfp_packs: ""
          configuration: default
          mplabx_version: "6.30"
          xc32_version: "4.60"

```

# Acknowledgements

Inspired by <https://github.com/velocitek/ghactions-mplabx>.
