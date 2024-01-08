For whatever reason, many of the error codes in Apple's Developer Note for the Macintosh Portable are wrong. It seems most other sites and documentation have copied from that in some way, because everything I see online also has the same mistakes.

## Critical Tests
### 01 - ROM Test
This test calculates the sum of all bytes of the ROM (4 bytes at a time) minus the 4 byte checksum at the beginning.  
If the checksum does not match, $FFFF is returned in the minor error register.
### 03 - RAM Test
### 05 - Address Line Test
This is test *T 3 when run from Test Manager.
### 06 - VIA Test
### 08 - Data Bus Test
This is test *T 1 when run from Test Manager.
### 0B - SCSI Test
Note: This test does not appear to ever result in a sad mac
### 0C - SWIM Test
Note: This test does not appear to ever result in a sad mac
### 0E - Data Bus Test
### 0F - System error before error table loaded
A system error occurred before the errors loaded.  
The minor error code indicates what error occurred.
### 10 - Power Manager Self Test
### 11 - Memory Sizing Test
This is test *T 0 when run from Test Manager.
### 14 - Power Manager Communication
#### CD33 - During a receive, power manager did not finish a handshake
#### CD34 - During a receive, power manager did not start a handshake
#### CD35 - During a send, power manager did not finish a handshake
#### CD36 - During a send, power manager did not start a handshake
#### CD37 - Timed out waiting for reply to initial handshake
#### CD38 - Power manager was never read to start handshake
### 82 - VRAM Data Test
### 83 - VRAM Address Test

## Non-critical Tests
### 80 - Mapper RAM Data Test
This test read and writes patterns to the CPU GLU mapper registers
### 81 - Mapper RAM Uniqueness Test
This test verifies that CPU GLU mapper registers are unique 
### 84 - SCC Reg Test
### 85 - SCC Loop Test
### 86 - SCC Timer Test
### 87 - VIA Test (Same as above, when run from Test Manager)
### 88 - SCSI Test (Full)
### 89 - ASC Test
### 8A - PRAM Test
This test does not do anything and always fails.

## Exceptions
Exception codes are ORed into the major error register, so it's possible they could combine with an existing error code.  
The minor error code is the current location of the stack pointer.
### 0100 - Bus Error
### 0200 - Address Error
### 0300 - Illegal Instruction
### 0400 - Divide By Zero
### 0500 - Check Instruction
### 0600 - TrapV Exception
### 0700 - Priviledge Violation
### 0800 - Trace
### 0900 - Line A Exception
### 0A00 - Line F Exception
### 0B00 - Unassigned Exception
### 0C00 - FPU Protocol Violation
### 0D00 - Format Exception
### 0E00 - Spurious Interrupt
### 0F00 - Trap Instruction Vectors
### 1000 - Interrupt Level 1
### 1100 - Interrupt Level 2
### 1200 - Interrupt Level 3
### 1300 - Interrupt Level 4
### 1400 - Interrupt Level 5
### 1500 - Interrupt Level 6
### 1600 - Interrupt Level 7
### 1700 - FPU Branch or Set on Unordered Condition
### 1800 - FPU Inexact Result
### 1900 - FPU Divide By Zero
### 1A00 - FPU Underflow
### 1B00 - FPU Operand Error
### 1C00 - FPU Overflow
### 1D00 - FPCP Signaling NaN
### 1E00 - PMMU Configuration
### 1F00 - PMMU Illegal Operation
### 2000 - PMMU Access Level Violation
## Flag Bits
To determine the flags, convert the major error register to binary. The high word contains the flags.
### Bit 16 - Message queued
### Bit 17 - SCC is INITed
### Bit 18 - Prevent automatic sleep
### Bit 19 - 
### Bit 20 - 
### Bit 21 - 
### Bit 22 -
### Bit 23 - 
### Bit 24 - Unexpected exception received
### Bit 25 -
### Bit 26 - VIA Test is asserted
### Bit 27 -
### Bit 28 - Stop on error
### Bit 29 - Loop on error
### Bit 30 -
### Bit 31 - 