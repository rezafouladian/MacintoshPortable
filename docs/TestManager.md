### *S - Service Mode

### *L - Load A4

Input: 4 Bytes

### *B - Set Byte Count

Input: 2 Bytes

### *D - Get Data

### *C - Checksum

### *G - Execute

Input: 4 Bytes

### *0 - Load A0

Input: 4 Bytes

### *1 - Load A1

Input: 4 Bytes

### *4 - Clear D6/D7

### *5 - Display Boot Message

### *7 - Prevent Sleep

### *A - ASCII Mode

### *H - Hex Mode

### *R - Send Test Results

### *M - Memory Dump

### *E - Echo On

### *I - Restart Test Manager

### *P - Power Manager Command

Input: ? Bytes

### *T - Run Critical Test

Input: 6 Bytes

#### Test 0: Memory Sizing Test

#### Test 1: Data Bus Test

A0: Test Address

#### Test 2: Modulo 3 RAM Test

A0: Start address  
A1: End address

#### Test 3: Address Line Test

#### Test 4: ROM Test

This test calculates a checksum individually for the two ROM chips.

#### Test 5: Reverse Modulo 3 RAM Test

A0: Start address  
A1: End address

#### Test 6: March RAM Test

A0: Start address  
A1: End address

### *N - Run Non-critical Test

Input: 6 Bytes

#### Test 80: Mapper RAM Data Test

#### Test 81: Mapper RAM Uniqueness Test

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