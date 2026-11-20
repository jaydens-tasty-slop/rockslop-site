---
title: Get rockslop
nav_order: 2
permalink: /install/
---

# Get rockslop

<a class="cta" href="{{ site.releases_url }}">Download rockslop <small>Latest release on GitHub</small></a>

{% include todo.html text="Which file to pick on the releases page: the GUI (`rockslop`) or the command line one (`rockslop-cli`), for Linux, Windows (x86-64 and arm64) and macOS. Note that Linux binaries need `chmod +x`." %}

## Before you flash

{% include todo.html text="The waiver, in your words: the flasher's first run asks you to sign it (can brick, voids warranty, don't return a flashed player)." %}

## Put the player in download mode

| Player | How |
| --- | --- |
| [YP3]({{ '/ports/yp3/' | relative_url }}) | Unplug it and power it off (hold the centre key). Hold **Down** while connecting USB, and let go once rockslop finds it. Or hold Down and tap **RESET**. |
| [TS17]({{ '/ports/ts17/' | relative_url }}) | Connect it switched on; stock is kicked into download mode automatically. If Rockbox is already running or it won't start: unplug, switch off, hold **Down** (or **Power**) while connecting and keep holding about 3 s. The screen stays dark. |

{% include todo.html text="Screenshots of the flasher, step by step." %}

## Going back to stock

{% include todo.html text="Return to stock: rockslop keeps a backup of your player's original flash and can write it back at any time. Say where the backups live." %}

## Something went wrong

{% include todo.html text="Recovery steps, where to ask for help (issue tracker link), what to include in a report." %}
