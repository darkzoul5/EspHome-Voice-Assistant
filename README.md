# ESP32 Voice Assistant Config

This repository contains ESPHome configurations for an ESP32-S3 based voice assistant.

## Schematic

![Voice Assistant Schematic](images/circuit_image.svg)

## Main Files

- `VA - v4.yaml`: current configuration - official home assistant voice PE config adjusted to my hardware.
- `VA - v3.yaml`: my 3rd attempt creating a config mostly from scratch copying a lot of online sources
- `official-voice-pe.yaml`: upstream reference configuration

## Hardware Used

- ESP32-S3 DevKitC-1 class board (N16R8 variant - 16MB flash, 8MB PSRAM)
- WS2812 8-LED ring (`GPIO47`)
- USB-C PD trigger board (configured for 5 V output)
- 2x `INMP441` I2S microphones
  - WS: `GPIO39`
  - SCK: `GPIO38`
  - SD: `GPIO40`
  - L/R-1: `GND`
  - L/R-2: `3.3V`
  - Vin: `3.3V`
  - GND: `GND`
- 2x `MAX98357A` I2S speaker amps
  - LRC: `GPIO1`
  - BCLK: `GPIO2`
  - DIN: `GPIO42`
  - GAIN: `none` (`GND` for more volume, but that can break)
  - SD: `3.3V` (through 210 kΩ resistor!!!)
  - Vin: `5V`
  - GND: `GND`
- 2x 4-inch 4Ω 3w speakers
- Center button (`GPIO21`)

## Notes

- LED ring size changed from 12 LEDs to 8 LEDs.
- All LED effects were scaled from 12-led math/indexing to 8-led math/indexing.
- `hardware_mute_switch` on GPIO20 and `jack_plugged` (jack detect) on GPIO17 are present in `VA - v4.yaml` but are not used in my hardware build.
