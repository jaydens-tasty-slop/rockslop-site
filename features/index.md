---
title: Rockslop Features
nav_order: 4
has_children: true
has_toc: false
permalink: /features/
---

# Features

Rockslop adds player support, as well as a collection of themes for each player. I also lost my mind and had an LLM port over 300 games to rockbox. Enjoy!

## New Core features

- **Bluetooth audio.** volume and play/pause,  headset battery level. Under Settings > Bluetooth menu.
  - **Bluetooth gamepads and keyboards.** Pure AI psychosis, I wanted to see if the agent owned the bluetooth stack enough to add PS4 controller support. It did! A DualShock 4/generic BT controller (not LE) or a keyboard can be used
- **Better FM radio.** Enhanced RDS (programme type, call letters, clock time, RadioText Plus) and FM recording to WAV.
- **Charge limit.** A setting from 100 % down to 50 %, with battery monitoring and a charge guard 
- **Touchscreen.** Lots of rewrites around touchscreen players to make touch a first class experience under Rockbox.

## Original plugins

My own wacky ideas.

{% for p in site.data.plugins.native %}{% if p.origin == "original" %}### {{ p.name }}

{{ p.kind }}. {{ p.what }}{% if p.credit != "" %} {{ p.credit }}{% endif %}{% if p.links.size > 0 %} Credits: {% for l in p.links %}[{{ l.text }}]({{ l.url }}){% unless forloop.last %}, {% endunless %}{% endfor %}.{% endif %}

{% endif %}{% endfor %}
## One-off ports

Cool projects I found to add to Rockbox. Minecraft demake included!

{% for p in site.data.plugins.native %}{% if p.origin == "port" %}### {{ p.name }}

{{ p.kind }}. {{ p.what }}{% if p.credit != "" %} {{ p.credit }}{% endif %}{% if p.links.size > 0 %} Upstream: {% for l in p.links %}[{{ l.text }}]({{ l.url }}){% unless forloop.last %}, {% endunless %}{% endfor %}.{% endif %}

{% endif %}{% endfor %}
## Other Handhelds

Most of the new plugins are ports from other open source handheld projects. Warning: very poorly tested! Please report bugs on GitHub.

{% for f in site.data.plugin_families %}{% assign games = site.data.plugins[f.id] %}### {{ f.title }}

{{ f.blurb }} **{{ games.size }} games.** Upstream: [{{ f.upstream.text }}]({{ f.upstream.url }}){% if f.library %}, [{{ f.library.text }}]({{ f.library.url }}){% endif %}.

[All {{ f.title }} games]({{ '/features/' | append: f.id | append: '/' | relative_url }})

{% endfor %}
