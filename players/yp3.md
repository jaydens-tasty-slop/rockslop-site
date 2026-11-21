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
# table_note: ""     # a short note for the Notes column of the Players table
stock_firmware: "?"

intro: |-
  Rockbox on a $9 MP3 player! Cheap, but usable, and working bluetooth. 512 KiB SRAM means some features had to be cut.

  **Important:** Up and Left on D-Pad are the home guesture!
  
hardware_notes: |-
  ### Pros
  * Excellent battery life - around 20 hours screen off. You'll want a screen protector.
  * Swanky 2 core 192mhz processor
  * Build quality feels better than TS17 somehow

  ### Cons
  * Only 5 buttons: makes some games hard to use.
  * Only English (for now)
  * No speech
  * **DSP:** No pitch/speed control, surround, crossfade
  * Cuesheets, key lock, 
  * album art
  * Theme backdrop pictures
  * No dircache, so folders are read straight from SD card
    * Large folders are truncated by default at 256 (configurable from 32 to 512)
  * Playlists are capped at 400
  * Missing Codecs: WMA Pro, Musepack (MPC), RealAudio (Cook), and the chiptune formats 
    SID, NSF, VGM, KSS, HES, SGC, ASAP. WavPack (16-bit), (24-bit/96 kHz)
# install: ""
# problems: ""
# battery_note: ""

# --- Also known as ---
sold_as:
  note: "Wholesalers sell these cheap on Aliexpress and Alibaba, no consistent brand."

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
    1. Turn player off, remove USB

    2. Hold "Down" on the dpad

    3. Plug in USB

    4. Screen will not turn on, if it turns on the player booted

    ### Exiting Download Mode
  
    Press reset button to exit, or press and hold power button for 10+s. 

    > *NOTE:* The player will sit in download mode indefinitely with the screen off, 
    > make sure to turn it off.
    
    The YP3 is almost unbrickable, you can always enter download mode (baked into bootloader).

    ### Alternative (USB In)

    1. Hold down on the dpad
    
    2. Press the "Reset" button on the right

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
  Audio formats: { state: partial, note: "Plays MP3, AAC (incl. HE-AAC), WMA, FLAC, ALAC, Vorbis, Opus and WAV. Limited: WavPack (24/96 is too slow), Vorbis and Opus (small Ogg pages only). Missing: Musepack, WMA Pro, RealAudio and the chiptune formats (too big for the RAM)." }
  DSP and effects: { state: partial, note: "Missing: crossfade, pitch and speed control, surround (left out to save RAM). EQ, compressor, tone and ReplayGain work." }
  Cuesheets: { state: missing, note: "Left out to save RAM." }
  Skins and themes: working
  Theme backdrop pictures: { state: missing, note: "Each is a 40 KiB frame; skins keep their colours and icons." }
  Album art: { state: missing, note: "No RAM for cover bitmaps." }
  Other UI languages: { state: missing, note: "English only. Translations are planned." }
  Voice and spoken menus: { state: missing, note: "No voice files or talk support." }
  Key lock: { state: missing, note: "No key-lock action on this keypad." }
  Browse and play from folders: working
  Large folders: { state: partial, note: "Up to 512 files per folder (default 256); more are cut off." }
  Long playlists: { state: partial, note: "Up to 400 tracks (upstream: 32000)." }
  Database (tag browser): { state: partial, note: "Read from the card: no first-letter menus or play statistics." }
  Directory cache: { state: missing, note: "Folders are read from the card each time." }
  Bookmarks: working
  Plugins and games: { state: working, note: "Over 350 extra plugins, but several big ones don't fit." }
  Plugins run while music plays: { state: missing, note: "One module at a time: music stops while a plugin runs." }
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
