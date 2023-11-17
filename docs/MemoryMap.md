| Start Address | End Address | Description |
| ------------- | ----------- | ----------- |
| FF 0000 | FF FFFF | Auto-vector Read, VPA |
| FE 0000 | FE FFFF | Normal/Idle Mode, Test |
| FD 0000 | FD FFFF | SCC |
| FC 0000 | FC FFFF | Slot Configure |
| FB 0000 | FB FFFF | Sound |
| FA 0000 | FA FFFF | Video |
| F9 0000 | F0 FFFF | SCSI |
| F8 0000 | F8 FFFF | ROM Diagnostics |
| F7 0000 | F7 FFFF | VIA |
| F6 0000 | F6 FFFF | SWIM |
| F0 0000 | F5 FFFF | Reserved (Unknown) |
| E0 0000 | EF FFFF | PDS ROM |
| A0 0000 | DF FFFF | Expansion ROM |
| 90 0000 | 9F FFFF | Permanent ROM |
| 10 0000 | 8F FFFF | Expansion RAM |
| 00 0000 | 0F FFFF | Permanent RAM |

## Permanent RAM

Address Space: 0x000000-0x0FFFFF  
Size: 1MB (0x100000)

Address Lines:

| A23 | A22 | A21 | A20 | A19-A0 |
| --- | --- | --- | --- | ------ |
| L | L | L | L | x |

## Expansion RAM

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

## Reserved (Unknown)

## SWIM

## VIA

## ROM Diagnostics

## SCSI

## Video

## Sound

## Slot Configure

## SCC

## Normal/Idle Mode, Test

## Auto-vector Read, VPA



[^1]: The ROM is selected in a 1MB range, however it is only a 256KB ROM and only has 256KB of address lines connected, so the ROM will be repeated across the 1MB space.