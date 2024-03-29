
# Table of contents

1. [Introduction](#introduction)
1. [Todo](#todo)
1. [Powered-off Testing](#powered-off-testing)
    1. [Test Setup](#test-setup)
    1. [Always-on 5V](#always-on-5v)
    1. [1.2V Reference](#12v-reference)
    1. [A/D Line](#ad-line)
1. [Powered-on Testing](#powered-on-testing)
    1. [Test Setup](#test-setup-1)
    1. [Powered-on +5V](#powered-on-5v)
    1. [Disk +12V](#disk-12v)
    1. [Disk +5V](#disk-5v)
1. [Additional Testing](#additional-testing)
    1. [-5V](#5v)
    1. [Charge Detection](#charge-detection)
    1. [Low Voltage Cutoff](#low-voltage-cutoff)
    1. [External video +5V](#external-video-5v)
    1. [Battery Compartment/Switch](#battery-compartmentswitch)
1. [Troubleshooting](#troubleshooting)
    1. [Always-on +5V Troubleshooting](#always-on-5v-troubleshooting)
    1. [1.2V Reference Troubleshooting](#12v-reference-troubleshooting)
    1. [A/D Line Troubleshooting](#ad-line-troubleshooting)
    1. [Powered-on +5V Troubleshooting](#powered-on-5v-troubleshooting)
    1. [Disk +12V Troubleshooting](#disk-12v-troubleshooting)
    1. [Disk +5V Troubleshooting](#disk-5v-troubleshooting)
1. [Additional Resources](#additional-resources)
    1. [M5126 RP201 Resistor Network](#m5126-rp201-resistor-network)
    1. [Full Component List](#full-component-list)


# Introduction
The goal of this document is to be an in-depth testing and troubleshooting guide for the Macintosh Portable M5120, and eventually the later backlit model M5126.

This is still heavily a work in progress, so many sections are completely empty.

# ToDo

- Finish most of the document
- Pictures and diagrams
- Seperate M5126 section?
- Make things look better
- Interactivity
- Link schematic pages


## Before you begin


# Powered-off Testing

## Test Setup
For the initial testing while powered off, disconnect everything down to the bare logic board.

You will need the following:
- The main logic board
- A method of connecting power to *both* battery input pins
- A suitable power source

### Connecting to the battery input

#### Using a 4-pin connector
The easiest way is to use a 4-pin power connector like the ones found on an ATX power supply. These are also commonly called "ATX 12V" or "CPU power" connectors.  
You can cut one off an ATX power supply, or buy a 4-pin extender cable commonly avaiable on places like Amazon, eBay, or other online and local computer stores.

<img src="images/4pin.jpg" width=30% alt="A 4-pin ATX CPU power cable with the wires cut.">

#### Clipping on to the board

#### Using the battery box
Using the original battery box and casing is probably the most difficult method of testing, as the large box tends to get in the way.

Before attempting to use the battery box in this way, I recommend [testing the switch](#battery-compartmentswitch).
### Supplying power
When testing with the computer powered off, we don't need much power.

Start with around 6.0V 500mA. This is to reduce the chance of damaging the A/D line due to bad circuity on the hybrid.  
This voltage should be sufficient to run most systems, but you can increase the voltage to 6.5V if you have trouble.

## Always-on +5V

## 1.2V Reference

## A/D Line

# Powered-on Testing

## Test Setup

## Powered-on +5V

## Disk +12V

## Disk +5V

# Additional Testing

## -5V

## Charge Detection

## Low Voltage Cutoff

## External Video +5V

## Battery Compartment/Switch
First off, make sure you know which is the positive and negative terminals on the battery compartment, 9V battery, and 4-pin plug.

With the battery cover off and the switch un-depressed, 

# Troubleshooting

## Always-on +5V Troubleshooting

### No voltage
Issue: No voltage is found on the always-on 5V source.

#### Fuse

#### Q16 Source

#### Q16 Gate

#### +5V Op-amp

### Low voltage
Issue: The always-on +5V is lower than 4.9V.

### High voltage
Issue: The always-on +5V is greater than around 5.4V, or is the same voltage as the battery.

## 1.2V Reference Troubleshooting

## A/D Line Troubleshooting

## Powered-on +5V Troubleshooting

## Disk +12V Troubleshooting

## Disk +5V Troubleshooting

## -5V Troubleshooting

## LCD Panel Section

<img src="images/displaypads1.png" alt="A drawing of a portion of the LCD PCB to show pads used to fix bad connections.">

# Additional Resources

## Hybrid Pinout and Readings

| Pin | Description | Nominal Voltage |
| --- | --- | --- |
| 8 | [+5V Regulation](#5v-regulation) | |
| 11 | +5V | |
| 16 | | |
| 17 | | |
| 18 | +5V | |
| 19 | | |
| 22 | | |
| 25 | | |
| 29 | | |
| 31 | | |
| 33 | -5V | 0V or -5V |
| 37 | -5V Enable | |
| 38 | | 0V |
| 39 | | |
| 40 | | |
| 41 | | |
| 51 | 1.2V Reference | 1.23V |
| 52 | | |
| 62 | [A/D](#ad) | 1V to 5V |

## Hybrid Extended Information

### +5V Regulation

### +5V

### Pin 16

### Pin 17

### Pin 19

### Pin 22

### Pin 25

### Pin 29

### Pin 31

### -5V

### -5V Enable

### Pin 38

### Pin 39

### Pin 40

### Pin 41

### 1.2V Reference

### Pin 52

### A/D

## M5126 RP201 Resistor Network

Appears as Bourns 4816P-E41-000 or Dale 112S0600

Layout is an isolated resistor network.

<img src="images/4816P-1.png" width=30% alt="The isolated resistor layout of a Bourns 4816P-1.">

Values:  
R1 430k  
R2 360k  
R3 1.37k  
R4 845k  
R5 320k  
R6 100k  
R7 100k  
R8 100k

## Full Component List

| Designator | Location | Part | Description | Schematic Page |
| --- | --- | --- | --- | --- |
| C2 | A-5 | | | 14 |
| C12 | G-15 |
| C18 | M-5 | | | 14 |
| C19 | M-5 | | Capacitor for LT1054 on hybrid | 14 |
| C25 | M-2 | | | 14 |
| C26 | M-2 | | | 14 |
| C27 | M-3 | | | 14 |
| C28 | M-4 | | | 14 |
| D1 | A-6 | 1N5817 | | 14 |
| D2 | A-11 | 1N5817 | +5V to 53C80 | 9 |
| D3 | | 1N914 | | 12 |
| D4 | | 1N914 | | 12 |
| R9 | A-12 | 10k Ω 1206 Resistor | | 12 |
| R10 | B-1 |  |  | 14 |
| R11 | C-10 | 1k Ω 1206 Resistor | 53C80 /EOP pull-up | 9 |
| R12 | D-14 | 1k Ω 1206 Resistor | | 6 |
| R13 | F-10 |
| R14 | F-11 |
| R15 | | 10k Ω 1206 Resistor | /SCCW/REQ pull-up | 9 |
| R17 | J-15 | 100k Ω 1206 Resistor | PMGR_IN0 voltage divider | 12 |
| R18 | J-10 | 10k Ω 1206 Resistor | | 12 |
| R19 | K-13 | 100k Ω 1206 Resistor | KBDSTOP pull-down | 13 |
| R20 | L-13 |
| R21 | L-11 | 100k Ω 1206 Resistor | +12V on/off pull-up | 14 |
| R24 | M-7 | 301k Ω 1206 Resistor | SCSI +5V voltage divider | 14 |
| R25 | M-7 | 100k Ω 1206 Resistor | SCSI +5V voltage divider | 14 |
| R26 | | 10k Ω 1206 Resistor | | 8 |
| R36 | | 47 Ω 1206 Resistor | FDB filter | 12 |
| R49 | | 47 Ω 1206 Resistor | | 12 |
| R50 | | 10k Ω 1206 Resistor | /IPL1 pull-up | 3 |
| R75 | | 47 Ω 1206 Resistor | /SOUND_CS filter | 11 |
| R94 | | 100k Ω 1206 Resistor | /LW pull-up | 5 |
| R95 | | 100k Ω 1206 Resistor | Permanent RAM /CS15 pull-up | 15 |
| R102 | | 470 Ω 1206 Resistor | | 12 |
| R103 | | 10k Ω 1206 Resistor | | 12 |
| R108 | | 100k Ω 1206 Resistor | RXDA+ pull-up | 8 |
| R109 | | 100k Ω 1206 Resistor | MODEM_SND_EN pull-down | 11 |
| R112 | | 100k Ω 1206 Resistor | /SLOT_LW pull-up | 5 |
| R113 | | 100k Ω 1206 Resistor | /SLOT_UW pull-up | 5 |
| R116 | | 100k Ω 1206 Resistor | /UW pull-up | 5 |
| R120 | | 100k Ω 1206 Resistor | ROM /OE pull-up | 4 |
| R125 | | 100k Ω 1206 Resistor | RXD_MODEM pull-down | 7 |
| R127 | | 10k Ω 1206 Resistor | /VIAIRQ pull-up | 9 |
| R129 | | 10k Ω 1206 Resistor | /BERR pull-up | 3 |
| R130 | | 10k Ω 1206 Resistor | /BGACK pull-up | 3 |
| R131 | | 10k Ω 1206 Resistor | /BR pull-up | 3 |
| R135 | | 100k Ω 1206 Resistor | Video RAM /RW pull-up | 6 |
| R136 | | 100k Ω 1206 Resistor | Video RAM /CS pull-up | 6 |
| R138 | | 100k Ω 1206 Resistor | /IPL2 pull-down | 3 |
| R139 | | 100k Ω 1206 Resistor | /INDISK1 pull-down | 7 |
| R140 | | 100k Ω 1206 Resistor | CTS_MODEM pull-down | 7 |
| R142 | | 100k Ω 1206 Resistor | | 12 |
| R143 | | 10k Ω 1206 Resistor | /SYS_RST pull-up | 12 |
| R144 | | 100k Ω 1206 Resistor | /MODEM_IN5 pull-up | 12 |
| R146 | | 100k Ω 1206 Resistor | VIA_TEST pull-up | 12 |
| R148 | | 1g Ω 1206 Resistor | | 7 |
| R150 | | 100k Ω 1206 Resistor | /WR pull-down | 7 |
| R151 | | 1k Ω 1206 Resistor | A/D filter | 12 |
| R152 | | 10k Ω 1206 Resistor | | 12 |
| R153 | | 100k Ω 1206 Resistor | PMGR_IN0 voltage divider | 12 |
| R155 | | 10k Ω 1206 Resistor | /NMIIN pull-up | 12 | 
| R156 | | 10k Ω 1206 Resistor | /RESET pull-up | 12 |
| R157 | | 10k Ω 1206 Resistor | | 14 |
| R158 | | 2.2k Ω 1206 Resistor | | 14 |
| R159 | | 2.2k Ω 1206 Resistor | | 14 |
| R160 | | 75k Ω 1206 Resistor | 1.2V reference to SCSI +5V OpAmp | 14 |
| R161 | | 1g Ω 1206 Resistor | | 14 |
| R162 | | 100k Ω 1206 Resistor | | 14 |
| R168 | | 100k Ω 1206 Resistor | /DISP_BLANK pull-up | 12 |
| R173 | | 10k Ω 1206 Resistor | | 14 |
| R174 | | 75k Ω 1206 Resistor | | 14 |
| R175 | | 75k Ω 1206 Resistor | | 14 |
| R176 | | 75k Ω 1206 Resistor | | 14 |
| RP2 | K-13 | | Permanent RAM /CS pull-ups | 15 |
| S1 | J-8 |
| Q1 | | IRF9Z30 | Charge regulator | 14 |
| Q2 | | IRFR9020 | Serial +5V on/off | 8 |
| Q4 | | IRFR9020 | External video +5V on/off | 6 |
| Q8 | | 2N3906 | | 8 |
| Q9 | | 2N7002 | | 8 |
| Q10 | F-10 | IRFR9020 | | 12 |
| Q11 | F-13 | IRFR9020 | | 12 |
| Q12 | | 2N3904 | | 12 |
| Q13 | H-10 | IRFR9020 | | 12 |
| Q14 | J-5 | IRF9Z30 | | 14 |
| Q15 | J-6 | IRF9Z30 | | 14 |
| Q16 | | IRF9Z30 | +5V regulator |
| Q18 | | 2N3904 | | 12 |
| Q19 | | 2N3904 | | 12 |
| Q20 | M-6 | IRF9Z30 | SCSI +5V regulator |
| Q21 | | IRFR9020 | +12V on/off | 14 |
| Q23 | | 2N3904 | | 14 |
| Q25 | | 2N3904 | | 14 |
| U5D | | 74AC245 | Permanent RAM data bus transceiver | 4 |
| U5E | | 74AC245 | Permanent RAM data bus transceiver | 4 |
| U5F | | 27C101 | Hi ROM | 4 |
| U5G | | 27C101 | Lo ROM | 4 |
| U7M | | OP-20 | SCSI +5V OpAmp | 14 |
| U10D | | | CPU GLU | 5 |
| U11K | | 74AC153 | | 7 |
| U11C | | 74AC244 | | 3 |
| U12C | | 74AC244 | | 3 |
| U12D | | 68HC000 | | 3 |
| U12G | | | Misc GLU | 7 |
| U14A | | | Apple Sound | 10 |
| U15B | | | Sony Sound | 10 |
| U15C | | | Sony Sound | 10 |
| U15D | | | Video | 6 |
| VR1 | | | | 14 |
| Y1 | J-11 | | | 7 |