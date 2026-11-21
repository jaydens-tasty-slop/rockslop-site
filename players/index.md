---
title: Players
nav_order: 3
has_children: true
permalink: /players/
---

# Players

{% include player-grid.html %}

{% include players-table.html %}

Some players that I tried that couldn't run rockbox are under [Failed Ports]({{ '/players/failed/' | relative_url }}).

## Feature comparison

{% include todo.html text="One sentence on how to read this table. The first sections are Rockbox's own features: a red Missing or yellow Partial there is something a normal Rockbox has that this build gives up (mostly to fit in RAM). Per-feature notes are on each player's page." %}

{% include feature-table.html %}

{% include legend.html %}

## Hardware comparison

{% include todo.html text="One sentence on what the table is for. The last two columns are the players we rejected (see Failed Ports)." %}

{% include hardware-table.html %}

A question mark is a value we haven't confirmed.
