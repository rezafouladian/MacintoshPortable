To enter the test manager, you can ground the VIA_TEST line located at pin 7 of the J22 edge connector. This must be done at boot before the cursor appears.

Connect a serial cable to the Modem port on the Portable.

Baud Rate: 9600  
Parity: None  
Data Bits: 8  
Stop Bits: 2

Most examples here that involve additional input assume you are running in [*A - ASCII Mode](#a---ascii-mode).  
For example, before running a command like `*T000100050000` make sure you've run `*A` at least once, or the system will assume the input is hex rather than ASCII.

### *S - Service Mode

Stops the startup message if entered using VIA_TEST or enabled using [*5](#5-display-boot-message), and disables the sleep timer which will normally shut down the computer after some time.

### *L - Load A4

Load a value into address register A4, for use in other commands.

Input: 4 Bytes

Example Usage:
```
*L00900000
```

### *B - Set Byte Count

Load a value into data register D4, for use in other commands.

Input: 2 Bytes

### *D - Get Data

### *C - Checksum

### *G - Execute

Execute code from a provided memory address.

Input: 4 Bytes

Example Usage:
```
*G00900058
```

### *0 - Load A0

Load a value into address register A0, for use in other commands.

Input: 4 Bytes

Example Usage:
```
*000100000
```

### *1 - Load A1

Load a value into address register A1, for use in other commands.

Input: 4 Bytes

Example Usage:
```
*100200000
```

### *4 - Clear D6/D7

Clears the error result registers in D6 and D7.

### *5 - Display Boot Message

### *7 - Prevent Sleep

Prevents the computer from sleeping automatically.

### *A - ASCII Mode

### *H - Hex Mode

### *R - Send Test Results

Outputs the D6 and D7 result registers.

### *M - Memory Dump

Dump memory starting at the address in A4, for D4 bytes.

[A4](#l---load-a4): Start address  
[D4](#b---set-byte-count): Number of bytes to dump

Example Usage:
```
*L000FFFF0
*B000F
*M
```

### *E - Echo On

### *I - Restart Test Manager

### *P - Power Manager Command

Send commands to the Power Manager.

Input: 2 + ? Bytes

Example usage:
```
*P100104
```
This command should turn off the hard drive power. (Untested)

### *T - Run Critical Test

Run a test from the built in critical tests.

Input: 6 Bytes  

Input structure:  

1. 2 bytes for the test number (Example: `0004` for the ROM Test)
2. 2 bytes for the number of passes (Example: `00FF` to run for 255 passes)
3. 2 bytes for test options

Example Usage:
```
*T000400FF0000
```

#### Test 0: Memory Sizing Test

#### Test 1: Data Bus Test

A0: Test address

#### Test 2: Modulo 3 RAM Test

[A0](#0---load-a0): Start address  
[A1](#1---load-a1): End address

Example Usage:
```
*000000000
*100100000
*T000200010000
```

#### Test 3: Address Line Test

#### Test 4: ROM Test

This test calculates a checksum individually for the two ROM chips.

#### Test 5: Reverse Modulo 3 RAM Test

[A0](#0---load-a0): Start address  
[A1](#1---load-a1): End address

Example Usage:
```
*000000000
*100100000
*T000500010000
```

#### Test 6: March RAM Test

[A0](#0---load-a0): Start address  
[A1](#1---load-a1): End address

Example Usage:
```
*000000000
*100100000
*T000600010000
```

### *N - Run Non-critical Test

Input: 6 Bytes

#### Test 80: Mapper RAM Data Test

See also: [CPU GLU RAM Mapping Registers](CPUGLU.md#ram-mapping-registers)

#### Test 81: Mapper RAM Uniqueness Test

See also: [CPU GLU RAM Mapping Registers](CPUGLU.md#ram-mapping-registers)

#### Test 82: VRAM Data Test

#### Test 83: VRAM Address Test

#### Test 84: SCC Register Test

#### Test 85: SCC Loop Test

#### Test 86: SCC Timer Test

#### Test 87: VIA Test

#### Test 88: SCSI Test

#### Test 89: ASC Test

#### Test 8A: PRAM Test

This test does not do anything and always fails.