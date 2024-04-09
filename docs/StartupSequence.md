``` mermaid
graph TD
    A["Power On"];
    A --> B[Returning from sleep?];
    B -->|No| C[Test ROM?];
    C -->|No| D[VIA Setup];
    C -->|Yes| E[Run Test ROM];
    E --> D;
    D ---> F[Power Manager Communication];
    F -->|Fail| H[Error 0x14];
    F ---> I[Power on SWIM, SCC, Serial, -5V];
    I -->|Fail| H;
    I --> J[ROM Checksum];
    J -->|Fail| K[Error 0x1];
    J --->|Pass| L[Power Manager Self Test];
    L -->|Fail| M[Error 0x10];
    L --->|Pass| N[VRAM Address Test];
    N -->|Fail| O[Error 0x83];
    N --->|Pass| P[VRAM Data Test];
    P -->|Fail| Q[Error 0x82];
    P --->|Pass| R[SCSI Test];
    R --> S[SWIM Test];
    S --> T[Data Bus Test];
    T -->|Fail| U[Error 0xE];
    T --->|Pass| V[Memory Sizing];
    V -->|Fail| W[Error 0x11];
    V --->|Pass| X[Non-Critical Tests];
```
