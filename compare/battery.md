---
title: Battery life
parent: Compare
nav_order: 3
permalink: /compare/battery/
---

# Battery life: stock vs Rockbox

{% include todo.html text="Two sentences of headline: wired, Rockbox lasts about as long as stock on the YP3; over Bluetooth it costs hours. Say what you want people to take from it." %}

{% include battery-chart.html %}

## How we measured

- Same 25 MP3s (128 kbit/s, 44.1 kHz, 2 h 21 min) on the card, repeat all, no shuffle.
- Output level matched on a tone through the headphone jack and a PC's Line In, so both firmwares play equally loud.
- Shortest backlight timeout, EQ and effects off, Bluetooth off for the wired runs, the PC 1 m away for the Bluetooth ones.
- Played from a full charge until the player turned itself off (about 3.35 V on both firmwares). Hours are timed from the audio on the PC, not from the player.
- One run per bar. The YP3's stock and Rockbox wired runs differ by less than run-to-run error.

{% include todo.html text="Anything you want to say about how much to trust these (one run each, battery ageing, no temperature control). Link the full procedure if you publish it." %}

## Caveats

- **The TS17's Rockbox run does not count.** It lasted 27.28 h but played about 10 dB quieter than stock, and began from a fuller cell: the TS17's charger can't be stopped from software, so "full" isn't the same twice. It stays on the chart so nobody wonders where the run went. A rerun at matched level is planned.
- **No TS17 Bluetooth runs yet.**
- **The TS28 hasn't been measured.**
- The low-power Bluetooth bar is an experimental build and isn't in the release.
