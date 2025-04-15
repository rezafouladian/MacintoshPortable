# Testing and Troubleshooting Guide

## Test Setup

### Powering the Logic Board

#### Using the 4-pin connector

#### Through the battery box

## Powered Off Testing

### Always-on +5V

There are many places to check the always-on +5V from, such as:

1. Pin 2 of Q16, or the heatsink attached to Q16
    - There's a chance of poor connectivity between the heatsink and the body of Q16, so if you see a strange reading test from another point
1. The positive leg of C16
1. Pins 11 and 18 of the hybrid

Here is an image highlighting those points:

![](media/5VPoints.jpg){ width="160px" }

The +5V is typically around 5.2V, but anywhere between 5.0-5.3V should probably be fine.

### Battery Level (A/D)

## Powered On Testing

### Powered-on +5V

### +12V

### -5V

## Troubleshooting

### Always-on +5V Troubleshooting

#### No voltage

1. Check Fuse

1. Low Voltage Comparator

#### Incorrect voltage

1. Check 1.2V Reference

### 1.2V Reference Troubleshooting

The 1.2V reference provides a reference voltage for several key parts of voltage regulation.

This is provided by a Linear Technology LT1004-1.2. The IC is marked "0412" and is located on the hybrid module.

![](media/LT1004.jpg){ width="160px" }

The reference needs a small amount of current to create the reference voltage, typically around 8µA at the minimum. 

Here is an image highlighting current supply path for the reference. Highlighted in yellow is the supply from the battery, through two resistors. After the second resistor the voltage should be 1.2V, highlighted in green.

![](media/Hybrid1_2VCurrentSupply.jpg){ width="160px" }

If you believe the reference is not getting enough current, you can try adding a resistor (recommended size between 100kΩ and 200kΩ) to supply more current.  
Be careful not to supply too much current, as the reference will have to dissipate that as heat.

### Low Voltage Comparator Troubleshooting
