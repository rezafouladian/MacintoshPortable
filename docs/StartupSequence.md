???+ Abstract "Initial Startup"

    - Disable processor interrupts
    - Set the speed register to run at full speed
    - Set the RAM config register (unknown)
    - Check if resuming from sleep

???+ Abstract "Initial Tests"

    - Set stack pointer to 0x2000
    - Clear error flag registers
    - Copy test code to RAM
    - Check for diagnostic ROM and execute if found (1)
        { .annotate }

        1.  0xF80000 is checked to see if it contains 0x55AAAA55, and executes code at 0xF80004 if found.
    - VIA test
    - Power Manager test
    - Test 0x10
    - Test 0x83
    - Test 0x82
    - SCSI test
    - SWIM test
    - Data bus test
    - Memory sizing
    - Play boot chime
    - Non-critical tests
    - Finish up error handling

???+ Abstract "Initialize Hardware"

    - Initialize VIA
    - Initialize SCC
    - Initialize SWIM
    - Initialize SCSI

???+ Abstract "Untitled"

    - Check what CPU we're running on
    - Check what logic board we're running on
    - Test RAM
    - Check for diagnostic ROM and execute if found (1)
        { .annotate }

        1. 0xF80080 is checked to see if it contains 0x55AAAA55, and executes code at 0xF80084 if found.  
        This check likely happens because the first check at 0xF80000 is skipped if resuming from sleep.