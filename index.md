---
title: Home
nav_order: 1
permalink: /
description: rockslop installs Rockbox on cheap MP3 players, and puts them back to stock.
---

# Rockbox on the cheapest MP3 players you can buy

{% include todo.html text="One or two sentences: what rockslop is and why anyone would want it. The headline above is filler too." %}

[Download rockslop]({{ site.releases_url }}){: .btn .btn-primary .fs-5 }

## Supported players

{% include players-table.html %}

{% include todo.html text="One line pointing at the Failed ports page, and one at the feature and hardware comparisons." %}

## Latest announcements

{% include post-list.html limit=3 %}

[All announcements]({{ '/announcements/' | relative_url }})

## How it works

1. **Backup.** The whole flash is read and saved before anything is written. Never skipped.
2. **Flash.** Only the sectors that differ are written, and each one is checksummed on the device.
3. **Rockbox.** The player reboots into Rockbox and rockslop syncs the files to the microSD card.

{% include todo.html text="Two or three sentences about returning to stock at any time, and what you get on top of vanilla Rockbox (Bluetooth, FM with RDS, hundreds of plugins). Pull the highlights from the YP3 changelog." %}

> **This can brick your player, and it voids your warranty.** Rockbox on these players is unofficial and experimental.
{: .warning }

{% include todo.html text="Rewrite the waiver summary in your own words; the real waiver is in the flasher." %}
