
Table of contents

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


# Powered-off Testing
## Test Setup
For the initial testing while powered off, there's not much that needs to be hooked to the board.

You will need the following:
- The main logic board
- A method of connecting power to *both* battery input pins
- A suitable power source

### Connecting to the battery input

#### Using a 4-pin connector
The easiest way is to use a 4-pin power connector like the ones found on an ATX power supply. These are also commonly called "ATX 12V" or "CPU power" connectors.  
You can cut one off an ATX power supply, or buy a 4-pin extender cable commonly avaiable on places like Amazon or computer stores.
#### Clipping on to the board
#### Using the battery box

Before attempting to use the battery box in this way, I recommend [testing the switch](#battery-compartmentswitch).
### Supplying power
For these initial tests we don't need much power.

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
Issue: The always-on +5V is greater than around 5.4V, or is the same voltage as the battery voltage.
## 1.2V Reference Troubleshooting
## A/D Line Troubleshooting
## Powered-on +5V Troubleshooting
## Disk +12V Troubleshooting
## Disk +5V Troubleshooting
## -5V Troubleshooting