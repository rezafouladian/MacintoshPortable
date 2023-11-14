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

## Expansion RAM

## Permanent ROM
The stock ROM is 256KB repeated in a 1MB address space.[^1]  
The permanent ROM can be disabled and replaced with external ROM by flipping a DIP switch on the M5120 or removing a jumper on the M5126.

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