| Start Address | End Address | Description |
| ------------- | ----------- | ----------- |
| FF 0000 | FF FFFF | [Auto-vector Read, VPA](#auto-vector-read-vpa) |
| FE 0000 | FE FFFF | [Normal/Idle Mode, Test](#normalidle-mode-test) |
| FD 0000 | FD FFFF | [SCC](#scc) |
| FC 0000 | FC FFFF | [Slot Configure](#slot-configure) |
| FB 0000 | FB FFFF | [Sound](#sound) |
| FA 0000 | FA FFFF | [Video](#video) |
| F9 0000 | F9 FFFF | [SCSI](#scsi) |
| F8 0000 | F8 FFFF | [ROM Diagnostics](#rom-diagnostics) |
| F7 0000 | F7 FFFF | [VIA](#via) |
| F6 0000 | F6 FFFF | [SWIM](#swim) |
| F0 0000 | F5 FFFF | [Reserved (Unknown)](#reserved-unknown) |
| E0 0000 | EF FFFF | [PDS ROM](#pds-rom) |
| A0 0000 | DF FFFF | [Expansion ROM](#expansion-rom) |
| 90 0000 | 9F FFFF | [Permanent ROM](#permanent-rom) |
| 10 0000 | 8F FFFF | [Expansion RAM](#expansion-ram) |
| 00 0000 | 0F FFFF | [Permanent RAM](#permanent-ram) |

## Permanent RAM

Address Space: 0x000000-0x0FFFFF  
Size: 1MB (0x100000)

Address Lines:

| A23 | A22 | A21 | A20 | A19-A0 |
| --- | --- | --- | --- | ------ |
| L | L | L | L | x |

## Expansion RAM
Space allocated for up to 8MB of expansion RAM.

Address Space: 0x100000-0x8FFFFF  
Size: 8MB (0x800000)

## Permanent ROM

Address Space: 0x900000-0x9FFFFF  
Size: 1MB (0x100000)

The stock ROM is 256KB repeated in a 1MB address space.[^1]  
The permanent ROM can be disabled and replaced with external ROM by flipping a DIP switch on the M5120 or removing a jumper on the M5126.

Address Lines:

| A23 | A22 | A21 | A20 | A19-A0 |
| --- | --- | --- | --- | ------ |
| H | L | L | H | x |

## Expansion ROM
This 4MB of address space is reserved for ROM expansion.

## PDS ROM

Address Space: 0xE00000-0xEFFFFF

## Reserved (Unknown)

Address Space: 0xF00000-0xF5FFFF

## SWIM

Address Space: 0xF60000-0xF6FFFF

## VIA

Address Space: 0xF70000-0xF7FFFF

## ROM Diagnostics

Address Space: 0xF80000-0xF8FFFF

## SCSI

Address Space: 0xF90000-0xF9FFFF

## Video

Address Space: 0xFA0000-0xFAFFFF

## Sound

Address Space: 0xFB0000-0xFBFFFF

## Slot Configure

Address Space: 0xFC0000-0xFCFFFF

## SCC

Address Space: 0xFD0000-0xFDFFFF

## Normal/Idle Mode, Test

Address Space: 0xFE0000-0xFEFFFF

## Auto-vector Read, VPA

Address Space: 0xFF0000-0xFFFFFF



[^1]: The ROM is selected in a 1MB range, however it is only a 256KB ROM and only has 256KB of address lines connected, so the ROM will be repeated across the 1MB space.