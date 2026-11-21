---
title: Development
nav_order: 5
has_toc: false
permalink: /development/
---

# Development

rockslop is based off of rockbox and is open source! 

For players with buttons we want to track upstream pretty closely.

For touchscreen players, a focus of rockslop is to improve rockbox's somewhat lacklustre touchscreen support so its a first-class citizen.

## New Ports

Contributions are welcome! I'll be pretty liberal about merging new hardware support and bugfixes as long as it was done by you or a frontier LLM (I don't want your brain-damaged local quantized deepseek) and you tested the crap out of it. The YP3 had hundreds of hours of bench testing.

### auto-rockbox makes it easy!

The [auto-rockbox](https://github.com/jaydens-tasty-slop/auto-rockbox) project contains agent instructions and a test suite for entirely hands-off rockbox ports. If you can get a player into download mode, and it has a documented boot ROM, a frontier LLM can probably do a port. If you follow the checklist in arb I'll probably accept it.

## Source

| Repository | What it is |
| --- | --- |
| [rockslop](https://github.com/jaydens-tasty-slop/rockslop) | Flasher for rockslop |
| [rockbox](https://github.com/jaydens-tasty-slop/rockbox) | Our fork of the Rockbox source, with the player ports. |
| [auto-rockbox](https://github.com/jaydens-tasty-slop/auto-rockbox) | The tooling for bringing up and testing new players (`arb`). |
| [rockslop-site](https://github.com/jaydens-tasty-slop/rockslop-site) | This website. |
