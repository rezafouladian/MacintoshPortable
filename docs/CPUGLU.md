# CPU GLU

The CPU GLU was also known as the "Normandy Decoder".

## /DTACK Generation

The CPU GLU generates /DTACK for the following memory regions:
- Permanent RAM and Expansion RAM (0x000000-0x8FFFFF)
    - The M5126 generates /DTACK for 0x000000-0x4FFFFF before the CPU GLU does
- Permanent ROM (0x900000-0x9FFFFF)
- Most peripheral addresses (0xF60000-0xFEFFFF)

## RAM Mapping Registers

These 16 registers are in the low bytes starting at 0xFC0000 (0xFC0001, 0xFC0003, etc.)  
Each register is three bits wide.

| Location | |
| --- | --- |
| 0xFC0001 | Bit 2: Moves 0x800000-0x87FFFF from SLOT_CS0 to SLOT_CS1 <br>Bit 1: Unknown <br>Bit 0: Unknown |
| 0xFC0003 | Bit 2: Moves 0x880000-0x8FFFFF from SLOT_CS0 to SLOT_CS1 <br>Bit 1: Unknown <br>Bit 0: Unknown |
| 0xFC0005 | Bit 2: Unknown <br>Bit 1: Unknown <br>Bit 0: Unknown |
| 0xFC0007 | Bit 2: Unknown <br>Bit 1: Unknown <br>Bit 0: Unknown |
| 0xFC0009 | Bit 2: Unknown <br>Bit 1: Unknown <br>Bit 0: Unknown |
| 0xFC000B | Bit 2: Unknown <br>Bit 1: Unknown <br>Bit 0: Unknown |
| 0xFC000D | Bit 2: Unknown <br>Bit 1: Unknown <br>Bit 0: Unknown |
| 0xFC000F | Bit 2: Unknown <br>Bit 1: Unknown <br>Bit 0: Unknown |
| 0xFC0011 | Bit 2:<br>Bit 1: Unknown <br>Bit 0: Unknown |
| 0xFC0013 | Bit 2:<br>Bit 1: Unknown <br>Bit 0: Unknown |
| 0xFC0015 | Bit 2: Moves 0x500000-0x57FFFF from SLOT_CS0 to SLOT_CS1 <br>Bit 1: Unknown <br>Bit 0: Unknown |
| 0xFC0017 | Bit 2: Moves 0x580000-0x5FFFFF from SLOT_CS0 to SLOT_CS1 <br>Bit 1: Unknown <br>Bit 0: Unknown |
| 0xFC0019 | Bit 2: Moves 0x600000-0x67FFFF from SLOT_CS0 to SLOT_CS1 <br>Bit 1: Unknown <br>Bit 0: Unknown |
| 0xFC001B | Bit 2: Moves 0x680000-0x6FFFFF from SLOT_CS0 to SLOT_CS1 <br>Bit 1: Unknown <br>Bit 0: Unknown |
| 0xFC001D | Bit 2: Moves 0x700000-0x77FFFF from SLOT_CS0 to SLOT_CS1 <br>Bit 1: Unknown <br>Bit 0: Unknown |
| 0xFC001F | Bit 2: Moves 0x780000-0x7FFFFF from SLOT_CS0 to SLOT_CS1 <br>Bit 1: Unknown <br>Bit 0: Unknown |

Tests [80 and 81](TestManager.md#test-80-mapper-ram-data-test) in the Test Manager will write values to these registers to test they are functioning properly.

## RAM Config Register
This 3 bit register is at 0xFE0200. Function is unknown. Setting the first bit (bit 0) seems to freeze the system.

## Slim /DTACK Load Register

0xFC0200

Memory access to the Slim Card region of memory (0x500000-0x8FFFFF) has a longer /DTACK delay until the first access of this register.
