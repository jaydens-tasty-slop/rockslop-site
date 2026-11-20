---
title: Home
nav_order: 1
permalink: /
description: rockslop installs Rockbox on cheap MP3 players, and puts them back to stock.
---

<div class="site-hero" markdown="0">
  <p class="eyebrow">Rockbox for cheap MP3 players</p>
  <h1>Rockbox on the cheapest MP3 players you can buy.</h1>
  <p class="deck">{% include todo.html text="One or two sentences: what rockslop is and why anyone would want it. Headline above is also filler." %}</p>
  <div class="cta-row">
    <a class="cta" href="{{ site.releases_url }}">Download rockslop <small>latest release on GitHub →</small></a>
  </div>
  <div class="meter" aria-label="Project counts">
    <div><b>{{ site.data.ports | where: "state", "released" | size }}</b><span>Ports released</span></div>
    <div><b>{{ site.data.ports | where: "state", "dev" | size }}</b><span>In development</span></div>
    <div><b>3</b><span>Triaged &amp; rejected</span></div>
  </div>
</div>

## Supported players

<div class="cards" markdown="0">
{%- for p in site.data.ports %}
  <a class="card" href="{{ p.url | relative_url }}">
    <div class="photo-frame"><span>PHOTO</span></div>
    <p class="card-title">{{ p.name }} {% include badge.html state=p.state %}</p>
    <p>{{ p.blurb }}</p>
  </a>
{%- endfor %}
</div>

{% include todo.html text="One line pointing at the Failed ports page, and one at the feature and hardware comparisons." %}

## How it works

<div class="cards" markdown="0">
  <div class="card"><p class="card-title">1. Backup</p><p>The whole flash is read and saved before anything is written. Never skipped.</p></div>
  <div class="card"><p class="card-title">2. Flash</p><p>Only the sectors that differ are written, and each one is checksummed on the device.</p></div>
  <div class="card"><p class="card-title">3. Rockbox</p><p>The player reboots into Rockbox and rockslop syncs the files to the microSD card.</p></div>
</div>

{% include todo.html text="Two or three sentences about returning to stock at any time, and about what you get on top of vanilla Rockbox (Bluetooth, FM with RDS, hundreds of plugins). Pull the highlights from the YP3 changelog." %}

{: .warning }
> **This can brick your player, and it voids your warranty.** Rockbox on these players is unofficial and experimental. {% include todo.html text="Rewrite the waiver summary in your own words; the real waiver is in the flasher." %}
