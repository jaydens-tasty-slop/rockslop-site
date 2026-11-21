---
layout: player
title: YP3
parent: Players
nav_order: 1
permalink: /players/yp3/
player: yp3          # key into _data/status, _data/battery, _data/hardware
state: released        # a key of _data/states.yml
blurb: "SmartLink SL6801. 128x160, D-pad, Bluetooth, FM."
specs:
  SoC: "SmartLink SL6801"
  CPU: "2x Cortex-M4, 64 MHz normal / 192 MHz max"
  RAM: "512 KiB SRAM"
  Flash: "2 MiB SPI NOR"
  XIP: "Yes, uncached (hot code runs from SRAM)"
  Display: "128x160 GC9106"
  Stock firmware: "?"
# Optional prose (Markdown); a missing one shows a "Write me" box:
# intro, hardware, install, problems, battery_note
# photos: [{ src: /assets/images/yp3/front.jpg, alt: "Front" }]
xip: >-
  The core runs **in place** from the 2 MiB SPI NOR flash (XIP), read in quad
  mode at about 55 MHz. There is **no XIP cache**, so code in flash runs
  roughly 75 times slower than from SRAM: the hot paths (the text path, the
  PCM and tick handlers) are copied to SRAM, and codecs and plugins are not in
  flash at all but load from the SD card into a shared arena. This is why the
  YP3 gets by on 512 KiB of RAM.
download:
  how: >-
    Switch the player off and unplug it. Hold **Down** while connecting USB, and
    let go once your computer sees the device. Or hold Down and tap **RESET**
    with a pin. This is the chip's boot ROM, so it works whatever is on the
    flash, even a broken Rockbox. A plain RESET (without Down) just restarts.
  usb:
    - { mode: Stock firmware (USB disk), id: "301a:2801", name: "SMTLINK CARDREADER 1.00" }
    - { mode: Download / recovery (boot ROM), id: "301a:2800", name: "SMTLINK DEVICE 2.00" }
    - { mode: Rockbox, id: "1209:0001", name: "Rockbox media player" }
---
