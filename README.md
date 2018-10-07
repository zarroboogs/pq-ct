
# Persona Q Cheat Table

A cheat table for __Persona Q__, a game developed by Atlus, for use while playing on Citra.

__WARNING:__ Generally untested, use at your own discretion, don't blame me for borked saves, etc.

__NOTE:__ The table is mostly dynamically generated, due to some limitations opening certain group records for the first time can take a while.

## Prerequisites

* Latest Cheat Engine release.
* Latest Citra release, preferably _nightly-mingw_, however canary\msvc builds should also work.
* Persona Q. This table has been tested with the undubbed US version, `CTR-AQQE`, together with the undubbed DLC.

## Installation

1. Download and install Cheat Engine (or use the portable version).
2. Clone or download this repository.

## Usage

1. Open Citra and launch __Persona Q__.
2. Open Cheat Engine and attach it to the Citra process.
3. Load the `citra-pq.CT` table. If prompted, allow the main table script to run.
4. Enable the table via one of the `[ENABLE]` scripts at the top, depending on your Citra flavor (mingw/msvc).

---

## Table Contents

Most stuff should be self-explanatory; however, some notes may be required:

1. __Play Time__, `t`, is measured using the following relationship: `t = 30 * 60 * (60 * h + m)`, where `h` and `m` are the number of hours and minutes played respectively.

2. The __Hit Meter__ appears to the right during each battle and is used for invoking the leader skill. The maximum meter level is 5 and each level is divided to 100 ticks, so 500 ticks will max out the meter.

3. The items within the __Item Inventory__ can only be edited via the table - adding and removing items would involve messing with emulated in-game pointers, which is not fun. To add an item, buy a cheap item from the workshop and edit it via the table, or create the item in the __Item Store__ and retrieve it from there.

4. In-game, English characters from user input are encoded as two bytes, using the SHIFT-JIS encoding for FULLWIDTH LATIN characters. However, ASCII is a subset of SHIFT-JIS, and is fully supported by the game - every non user input English string in the game is ASCII encoded.

   Strings in-game (including user input strings) are `\0` terminated.

   Examples for user input strings are the __P3 Hero__ and __P4 Hero__ names. Usually, these are limited to 6 chars, but are stored in memory as 14 bytes: `(14 - 1) // 2 == 6` (for the first name and last name each). However, these can be edited as ASCII strings (1 byte per character), thus increasing the total character limit per name to 13 chars: `(14 - 1) // 1 == 13`.

   To edit a string, e.g. the __P4 Hero__ name, use the following process:

   1. Highlight a name record and press `Ctrl+B` to browse the memory at that address.
   2. Zero out the bytes from that point up to the closest `00` byte.
   3. Then, use the table to edit the name to the desired ASCII string.
   4. Do this for both the first and last name.
   5. Do the same for the full name, with a format of `"<fname> <lname>"`.

   |                      |                      |                      |
   |:--------------------:|:--------------------:|:--------------------:|
   | ![n0](img/name0.png) | ![n1](img/name1.png) | ![n2](img/name2.png) |
   | ![n3](img/name3.png) | ![n4](img/name4.png) | ![n5](img/name5.png) |
