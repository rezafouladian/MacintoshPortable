# Macintosh Portable "Sad Mac" Error Codes

These error codes are specific to the Macintosh Portable and may not apply to other systems.

!!! note
    For whatever reason, many of the error codes in Apple's Developer Note for the Macintosh Portable are wrong. It seems most other sites and documentation have copied from that in some way, because everything I see online also has the same mistakes.

When an issue is found during the critical tests on intial startup, the computer will display a "sad mac" icon with an error code indicating which test failed.

## Error Structure

Errors are displayed on screen as two sets of four bytes in hexadecimal.  

In the top set of four bytes, the two bytes on the right are the major error code:  
0000`0000`  
00000000

The bottom set of four bytes is the minor error code:  
00000000  
`00000000`

The two bytes on the left of the top bytes are the [flag bits](#flag-bits):  
`0000`0000  
00000000

## Critical Tests
Critical tests failing during startup tests will usually result in a "Sad Mac" screen and the computer will not continue booting.

### 01 - ROM Test
This test calculates the sum of all bytes of the ROM (4 bytes at a time) minus the 4 byte checksum at the beginning.  
If the checksum does not match, $FFFF is returned in the minor error register.

Example error:
```
00000001
0000FFFF
```
### 03 - RAM Test

This error indicates an issue when running the "modulo 3" RAM test. The test writes a pattern 4 bytes at a time, copying the next pattern from the previous 4 bytes so that any errors in individual bits are copied to the end. The test compares the pattern written at the end to the original test pattern and any bits that do not match will be marked in the minor error register.

The minor error register will contain 2 bytes to indicate any failed bits on the 16-bit data bus.

This is test [*T 2](TestManager.md#test-2-modulo-3-ram-test) when run from the [Test Manager](TestManager.md).

**Example errors:**
```
00000003
00000040
```
Data bit 6 is marked as failed.
<hr>

```
00000003
0000FF00
```
The upper 8 bits on the data bus (bits 8-15) are marked as failed. It's likely one or more RAM chips on the upper byte are failed, or a chip select line is disconnected.

### 05 - Address Line Test
This is test [*T 3](TestManager.md#test-3-address-line-test) when run from the [Test Manager](TestManager.md).

**Example error:**
```
00000005
????????
```
### 06 - VIA Initialization
Note: There is no test at this step. The only way this error code should appear is if there is an [Exception](#exceptions) during this step.
### 08 - Data Bus Test (End of RAM)

This error indicates a failure in reading and writing the last 8 bytes of RAM (where the computer has placed the stack after memory sizing).  
A pattern is written and read 256 times, and any bit errors that occur are represented in the minor error register.  
For more info on the test, see [Data Bus Test](TestManager.md#test-1-data-bus-test).

**Example error:**
```
00000008
0000FF00
```
The upper byte (bits 8-15) failed to verify.

This is test [*T 1](TestManager.md#test-1-data-bus-test) when run from the [Test Manager](TestManager.md).
### 0B - SCSI Initialization
Note: There is no test at this step. The only way this error code should appear is if there is an [Exception](#exceptions) during this step.
### 0C - SWIM Initialization
Note: There is no test at this step. The only way this error code should appear is if there is an [Exception](#exceptions) during this step.
### 0E - Data Bus Test (Start of RAM)

This error indicates a failure in reading and writing the first 8 bytes of RAM.
A pattern is written and read 256 times, and any bit errors that occur are represented in the minor error register.  
For more info on the test, see [Data Bus Test](TestManager.md#test-1-data-bus-test).

**Example error:**
```
0000000E
000000FF
```
The lower byte (bits 0-7) failed to verify.

This is test [*T 1](TestManager.md#test-1-data-bus-test) when run from the [Test Manager](TestManager.md).
### 0F - System error before error table loaded
A system error occurred before the errors were loaded. Normally you would see the "Sorry, a system error occurred" bomb screen, but that part of the OS has not loaded yet.  
The minor error code indicates what error occurred.

**Example error:**
```
0000000F
00000001
```
The minor code `1` indicates a bus error.
### 10 - Power Manager Self Test
The system attempted to run the self test on the power manager, but it either did not respond or the test failed.

See [Power Manager Communication](#14---power-manager-communication) for minor error code meaning.

Example error:
```
00000010
0000CD38
```
### 11 - Memory Sizing Test
This is test [*T 0](TestManager.md#test-0-memory-sizing-test) when run from the [Test Manager](TestManager.md).

Example error:
```
00000011
????????
```
### 14 - Power Manager Communication

??? note "Power Manager Communication Flowchart"

    ``` mermaid
    graph TD
        A[PMGR/VIA ready?];
        A ---->|Yes| B[PMGR handshake response?];
        A -->|No| C[Timeout exceeded?];
        C -->|No| A;
        C -->|Yes| D[Error CD38];
        B ---->|Yes| E[Direction?];
        B -->|No| F[Timeout exceeded?];
        F -->|No| B;
        F -->|Yes| G[Error CD37];
        E -->|Send| H[Send started?];
        E -->|Receive| I[Receive started?];
        I --->|Yes| J[Receive finished?];
        H --->|Yes| K[Send finished?];
        J --->|Yes| Z[Done];
        I -->|No| L[Error CD34];
        J -->|No| M[Error CD33];
        H -->|No| N[Error CD36];
        K -->|No| O[Error CD35];
        K --->|Yes| Z;

    ```

Example error:
```
00000014
0000CD34
```

#### CD33 - During a receive, power manager did not finish a handshake
Example error:
```
00000014
0000CD33
```
#### CD34 - During a receive, power manager did not start a handshake
Example error:
```
00000014
0000CD34
```
#### CD35 - During a send, power manager did not finish a handshake
Example error:
```
00000014
0000CD35
```
#### CD36 - During a send, power manager did not start a handshake
Example error:
```
00000014
0000CD36
```
#### CD37 - Timed out waiting for reply to initial handshake
Example error:
```
00000014
0000CD37
```
#### CD38 - Power manager was never ready to start handshake
Example error:
```
00000014
0000CD38
```
### 82 - VRAM Data Test
Example error:
```
00000082
????????
```
### 83 - VRAM Address Test
Example error:
```
00000083
????????
```


## Non-critical Tests
Non-critical tests will typically not crash the computer when they fail and instead save the error for later.
### 80 - Mapper RAM Data Test
This test read and writes patterns to the CPU GLU mapper registers.

Note: This test is not run on startup and typically only accessible from the [Test Manager](TestManager.md#test-80-mapper-ram-data-test).
### 81 - Mapper RAM Uniqueness Test
This test verifies that CPU GLU mapper registers are unique.

Note: This test is not run on startup and typically only accessible from the [Test Manager](TestManager.md#test-81-mapper-ram-uniqueness-test).
### 84 - SCC Reg Test
### 85 - SCC Loop Test
### 86 - SCC Timer Test
### 87 - VIA Test (Full)
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
### Bit 19 - Star * received
This bit is set when a star/asterisk has been received, used to start a Test Manager command.
### Bit 20 - ASCII input mode
If this bit is set then the Test Manager input expects ASCII input.  
If this bit is cleared then it expects hexadecimal input.
### Bit 21 - Echo enabled
### Bit 22 - Timer enabled
### Bit 23 - New line after messages
If this bit is set then a new line/CRLF is sent after each message.
### Bit 24 - Unexpected exception received
### Bit 25 - Programmer's key interrupt was pressed
### Bit 26 - VIA Test is asserted
### Bit 27 - Bus errors OK
### Bit 28 - Stop on error
### Bit 29 - Loop on error
### Bit 30 - Store results in PRAM
### Bit 31 - Boot after test finishes
