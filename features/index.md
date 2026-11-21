---
title: Features
nav_order: 4
has_children: true
has_toc: false
permalink: /features/
---

# Features

{% include todo.html text="One paragraph: what rockslop adds on top of stock Rockbox and on top of each player's own firmware. This page lists only the new things; Rockbox's own plugins are not repeated." %}

## Core features

- **Bluetooth audio.** A2DP source with the bitrate adapted to the link, AVRCP (volume and play/pause), auto-reconnect, headset battery level, and a Settings > Bluetooth menu.
- **Bluetooth gamepads and keyboards.** A DualShock 4 or a keyboard can act as the player's buttons.
- **Better FM radio.** Enhanced RDS (programme type, call letters, clock time, RadioText Plus) and FM recording to WAV.
- **Charge limit.** A setting from 100 % down to 50 %, with battery monitoring and a charge guard.
- **Low-memory database.** Browse your library by tags during playback, with a progress count while it builds.
- **Playback in 512 KiB of RAM.** Decoders and plugins load on demand from the SD card; the common codecs (MP3, AAC, WMA, Vorbis, Opus) run straight from flash.

## Original plugins

Written for this port.

{% for p in site.data.plugins.native %}{% if p.origin == "original" %}### {{ p.name }}

{{ p.kind }}. {{ p.what }}{% if p.credit != "" %} {{ p.credit }}{% endif %}{% if p.links.size > 0 %} Credits: {% for l in p.links %}[{{ l.text }}]({{ l.url }}){% unless forloop.last %}, {% endunless %}{% endfor %}.{% endif %}

{% endif %}{% endfor %}
## Ports of single games and apps

Someone else's project, brought to the player one at a time. Each links to where we got it.

{% for p in site.data.plugins.native %}{% if p.origin == "port" %}### {{ p.name }}

{{ p.kind }}. {{ p.what }}{% if p.credit != "" %} {{ p.credit }}{% endif %}{% if p.links.size > 0 %} Upstream: {% for l in p.links %}[{{ l.text }}]({{ l.url }}){% unless forloop.last %}, {% endunless %}{% endfor %}.{% endif %}

{% endif %}{% endfor %}
## Port families

Whole libraries of games from other handhelds, each run by a compatibility layer. Every game is its own plugin and keeps its upstream licence. The pages below list every one, with where we got it.

{% for f in site.data.plugin_families %}{% assign games = site.data.plugins[f.id] %}### {{ f.title }}

{{ f.blurb }} **{{ games.size }} games.** Upstream: [{{ f.upstream.text }}]({{ f.upstream.url }}){% if f.library %}, [{{ f.library.text }}]({{ f.library.url }}){% endif %}.

[All {{ f.title }} games]({{ '/features/' | append: f.id | append: '/' | relative_url }})

{% endfor %}
