

The Outbound contains EEPROMs placed in Apple's "Test Software" address space.

If the stock Macintosh ROM finds the value `0x55AAAA55` there, it will execute that code instead of continuing with normal startup. This check is one of the first few instructions that the computer executes.

Here is an example of the check from the v1 Macintosh Plus ROM:
```
    movem.l $F80000,D0/A0
    cmpi.l  #$55AAAA55,D0
    bne.b   NormalStartup
    lea     NormalStartup,A1
    jmp     (A0)
```

