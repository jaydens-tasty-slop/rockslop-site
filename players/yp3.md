---
layout: player
title: YP3
parent: Players
nav_order: 1
permalink: /players/yp3/

# --- Identity ---
player: yp3
state: released          # a key of _data/states.yml
blurb: "SmartLink SL6801. 128x160, D-pad, Bluetooth, FM."
stock_firmware: "?"

# --- Prose (Markdown). Delete a line and a 'Write me' box takes its place. ---
# intro: ""
# hardware_notes: ""
# install: ""
# problems: ""

# --- Also known as ---
sold_as:
  note: "Unknown: we don't yet know what this is sold as, or by whom."

buy:
  - { store: AliExpress, url: "https://www.aliexpress.us/item/3256807764385286.html", price: "paid $9.79" }

# --- Hardware (one value per row of _data/hardware.yml; "?" = unknown) ---
hardware:
  Processor:
    SoC: "SmartLink SL6801"
    CPU: "2x Cortex-M4, 64 MHz normal / 192 MHz max"
  Memory:
    RAM: "512 KiB SRAM"
    Code storage: "2 MiB SPI NOR"
    Execute in place (XIP): "Yes, uncached: hot code is copied to SRAM; codecs and plugins load from SD"
    Music storage: "microSD"
  Display & input:
    Display: "128x160, GC9106"
    Touch: "No"
    Buttons: "D-pad + centre, reset pinhole"
  Wireless & audio:
    Bluetooth: "Yes"
    FM radio: "RDA5807"
    Microphone: "On the board, no port in the case"
    Speaker: "Yes (mono)"
  Physical:
    USB: "USB-C"
    Battery: "?"
    Case: "?"

# --- Getting to download mode ---
download:
  short: "Hold Down + plug in USB (or Down + RESET)"     # one line for the comparison table
  how: >-
    Switch the player off and unplug it. Hold **Down** while connecting USB, and
    let go once your computer sees the device. Or hold Down and tap **RESET**
    with a pin. This is the chip's boot ROM, so it works whatever is on the
    flash, even a broken Rockbox. A plain RESET (without Down) just restarts.
  usb:
    stock: { id: "301a:2801", name: "SMTLINK CARDREADER 1.00" }
    download: { id: "301a:2800", name: "SMTLINK DEVICE 2.00" }
    rockbox: { id: "1209:0001", name: "Rockbox media player" }

# --- Battery: hours played from full to empty, same files, level-matched ---
battery:   # omit a value if not measured yet
  - { mode: wired, title: "Headphone jack", stock: 21.29, rockbox: 20.07 }
  - { mode: bt, title: "Bluetooth (A2DP to a PC, 1 m)", stock: 20.82, rockbox: 19.55 }

# --- Features (states for the comparison table) ---
features:
  Wired audio playback: working
  Bluetooth audio (A2DP): working
  Bluetooth gamepads and keyboards: working
  Video playback: working
  Built-in speaker: working
  FM radio: working
  FM recording: working
  Microphone recording: working
  Real power-off and wake: working
  Touchscreen: na
  Plugins and games: working
  Real-time clock and alarm: working
  Charge limit: working
  Flash with rockslop: working
  Return to stock with rockslop: working

# --- Status table (state: a key of _data/states.yml) ---
status:
  Core:
    - { name: Boot and power-on, state: working, note: "Runs in place from SPI NOR; the stock bootloader hands over." }
    - { name: Real power-off and wake, state: working, note: "Centre key, about 3 s to power on. On USB the chip restarts instead of powering off, as stock." }
    - { name: Recovery to download mode, state: working, note: "A watchdog returns a hung player to the ROM's USB mode." }
    - { name: Second CPU core, state: planned, note: "Both cores are Cortex-M4. Rockbox runs on one." }
  Display & input:
    - { name: LCD 128x160, state: working, note: "GC9106, RGB565, DMA frame push." }
    - { name: Backlight, state: working, note: "PWM, 10 brightness levels, timeout and wake." }
    - { name: Buttons, state: working, note: "Five keys and a reset pinhole; Rockbox's usual keymap with a few extras." }
  Audio:
    - { name: MP3 / FLAC / Vorbis / Opus / AAC / WMA, state: working, note: "Codecs load from the SD card on demand." }
    - { name: Headphone output, state: working, note: "44.1 kHz and others, correct pitch and channels." }
    - { name: Speaker, state: working, note: "The jack cuts it in hardware; there is no detect line." }
    - { name: Recording from the mic, state: working, note: "WAV, AIFF, WavPack and MP3 encoders." }
  Radio & wireless:
    - { name: FM radio, state: working, note: "RDA5807; autoscan, presets, RDS and FM recording." }
    - { name: Bluetooth audio (A2DP + AVRCP), state: working, note: "Source role; reconnects when the same headset returns." }
    - { name: Bluetooth gamepads and keyboards, state: working, note: "DualShock 4 and keyboards act as the player's buttons." }
  Storage & USB:
    - { name: microSD (FAT, state: working, note: "4-bit bus, DMA." }
    - { name: USB mass storage, state: working, note: "About 1 MB/s read and write." }
  Power:
    - { name: Battery monitoring, state: working, note: "Voltage only; the reading is not calibrated." }
    - { name: Charging control, state: working, note: "Charge Limit setting, 50 to 100 %." }
    - { name: CPU voltage scaling, state: planned, note: "CPU switches 64 / 192 MHz; core voltage is not scaled." }
  Software:
    - { name: Real-time clock and alarm, state: working, note: "" }
    - { name: Plugins and games, state: working, note: "Over 350 extra plugins, loaded from the SD card." }
    - { name: Video playback, state: working, note: "AVI, MKV and MP4." }
---
