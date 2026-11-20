---
title: Failed ports
nav_order: 5
permalink: /failed-ports/
---

# Failed ports

{% include todo.html text="Intro: we buy cheap players, triage them, and most don't make it. This page is the honest record, and a warning if you're shopping. Say what triage involves (download mode, memory map, flash, RAM)." %}

| Player | Chip | Verdict | Why |
| --- | --- | --- | --- |
| [US212D](#us212d) | Actions ATJ2127 | {% include badge.html state="rejected" %} | 168 KiB RAM, NAND only. And fake storage. |
| [S5](#s5) | Actions ATJ2157 | {% include badge.html state="rejected" %} | 288 KiB RAM, NAND only. |
| [M7](#m7) | SmartLink SL6806 | {% include badge.html state="parked" %} | Triage unfinished. |

## US212D
{: #us212d }

<span class="verdict">Rejected</span> <span class="verdict">Fake storage</span>

{% include todo.html text="One or two lines of colour on the player (sold as 32 GB, aluminium, Bluetooth transmitter firmware, manual says 'ATJ2127' but names the model Cb2732). Add the brand / listing if you want to name it, plus a photo." %}

### Hall of shame: 32 GB that isn't

<div class="capacity" markdown="0">
  <div class="adv">ADVERTISED: 32 GB</div>
  <div class="bar"><i style="width: 12.5%"></i></div>
  <div class="row"><span>REAL: 4 GiB of NAND</span><span>12.5 % of what's on the box</span></div>
</div>

The player's USB disk reports two LUNs of 33.2 GB and exactly 30,000 MiB. Behind them is a single 4 GiB NAND chip. We proved it on 2026-11-17 by writing signed blocks through raw SCSI at 3.82, 7.63, 11.4 ... 30.52 GiB: **every one of them read back the block written at 0 GiB**. Writes past 4 GiB are lost and reads wrap around. The test blocks were restored afterwards.

Even fully populated, the controller could address at most 16 GiB.

{% include todo.html text="Your own words on this. Maybe a short 'how to check your own card/player' (f3write / f3read) box for readers." %}

### Why it failed anyway

| Item | Detail |
| --- | --- |
| **RAM** | 168 KiB of on-chip SRAM. No DRAM. |
| **Code storage** | NAND only: no execute-in-place flash. Stock pages code in from NAND. |
| **CPU** | MIPS32 M4K, no cache, no FPU. Not ARM, so none of our other ports' code applies. |
| **Storage** | No microSD slot. |
| **Firmware** | 2013 Actions SDK, 48 MiB, 135 files. Its Bluetooth name is "us212d蓝牙发射机". |

For scale, the YP3's static RAM alone nearly fills 168 KiB before any code is loaded.

**Status:** dropped, and the player was returned (2026-11-17).

## S5
{: #s5 }

<span class="verdict">Rejected</span>

{% include todo.html text="One or two lines on the player: QNGEE S5, 128x160 touchscreen, Bluetooth, FM, clip, SD slot, micro-USB. Photo." %}

| Item | Detail |
| --- | --- |
| **RAM** | 288 KiB of SRAM in three blocks (224 + 32 + 32 KiB). No PSRAM seen. |
| **Code storage** | NAND only, 16 KiB pages. A normal Rockbox core can't run in place. |
| **CPU** | Cortex-M4F. Fine. |
| **Storage** | NAND of 2 x 16 GiB dies. **Genuine 32 GB**: stock's 31 GiB disk fits. |
| **Verdict** | Possible only with all code in RAM or a paging scheme. Much harder than the ports we ship. |

{: .note }
> We first called the S5's storage fake, from one chip-enable's worth of evidence. That was wrong: its second die answers on a pad our probe didn't enable. We corrected the record. **The S5 is not in the hall of shame.**

## M7
{: #m7 }

<span class="verdict" style="border-color: #6b6b66; color: #6b6b66;">Parked</span>

{% include todo.html text="Decide whether this belongs on the page at all. It is not a rejection yet: say what is still open." %}

| Item | Detail |
| --- | --- |
| **SoC** | SmartLink SL6806, the YP3's family: same Cortex-M4 core. |
| **RAM** | **1 MiB SRAM**, twice the YP3's. No PSRAM seen. |
| **Flash** | SPI NOR, 2-4 MiB; the window we saw holds only a bootloader and SD updater. |
| **Open** | Where the main application lives (another flash region, or the SD card). |

## What would change our mind

{% include todo.html text="What would make a rejected player worth revisiting (a hidden PSRAM, a better loader, a donor board). Invite readers to send in players or findings." %}
