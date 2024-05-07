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

Address Lines When Selected:

| A23 | A22 | A21 | A20 | A19-A0 |
| --- | --- | --- | --- | ------ |
| L | L | L | L | x |

Permanent RAM Layout (M5120):

| | 1 | 2 | 3 | 4 |
| --- | --- | --- | --- | --- |
| B | 0x000000 - 0x00FFFF | 0x010000 - 0x01FFFF | 0x020000 - 0x02FFFF | 0x030000 - 0x03FFFF |
| C | 0x040000 - 0x04FFFF | 0x050000 - 0x05FFFF | 0x060000 - 0x06FFFF | 0x070000 - 0x07FFFF |
| D | 0x080000 - 0x08FFFF | 0x090000 - 0x09FFFF | 0x0A0000 - 0x0AFFFF | 0x0B0000 - 0x0BFFFF |
| E | 0x0C0000 - 0x0CFFFF | 0x0D0000 - 0x0DFFFF | 0x0E0000 - 0x0EFFFF | 0x0F0000 - 0x0FFFFF 
| F | 0x000000 - 0x00FFFF | 0x010000 - 0x01FFFF | 0x020000 - 0x02FFFF | 0x030000 - 0x03FFFF |
| G | 0x040000 - 0x04FFFF | 0x050000 - 0x05FFFF | 0x060000 - 0x06FFFF | 0x070000 - 0x07FFFF |
| H | 0x080000 - 0x08FFFF | 0x090000 - 0x09FFFF | 0x0A0000 - 0x0AFFFF | 0x0B0000 - 0x0BFFFF |
| J | 0x0C0000 - 0x0CFFFF | 0x0D0000 - 0x0DFFFF | 0x0E0000 - 0x0EFFFF | 0x0F0000 - 0x0FFFFF 

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

Address Space: 0xA00000-0xDFFFFF  
Size: 4MB

## PDS ROM

Address Space: 0xE00000-0xEFFFFF  
Size: 1MB

## Reserved (Unknown)

Address Space: 0xF00000-0xF5FFFF

See Also:  
[Slim Card Registers](SlimCards.md#slim-card-registers)

## SWIM

Address Space: 0xF60000-0xF6FFFF  
Size: 64KB

## VIA

Address Space: 0xF70000-0xF7FFFF  
Size: 64KB

## ROM Diagnostics

Address Space: 0xF80000-0xF8FFFF  
Size: 64KB

The system checks for diagnostic ROMs at this location.

## SCSI

Address Space: 0xF90000-0xF9FFFF  
Size: 64KB

## Video

Address Space: 0xFA0000-0xFAFFFF  
Size: 64KB

## Sound

Address Space: 0xFB0000-0xFBFFFF  
Size: 64KB

## Slot Configure

Address Space: 0xFC0000-0xFCFFFF  
Size: 64KB

See Also:  
[CPU GLU](CPUGLU.md)

## SCC

Address Space: 0xFD0000-0xFDFFFF  
Size: 64KB

## Normal/Idle Mode, Test

Address Space: 0xFE0000-0xFEFFFF  
Size: 64KB

See Also:  
[Idle Speed Register](CPUGLU.md#idle-speed-register)

## Auto-vector Read, VPA

Address Space: 0xFF0000-0xFFFFFF  
Size: 64KB



[^1]: The ROM is selected in a 1MB range, however it is only a 256KB ROM and only has 256KB of address lines connected, so the ROM will be repeated across the 1MB space.