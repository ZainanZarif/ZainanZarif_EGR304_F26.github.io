
# PCB Design

## Introduction

This page documents the PCB design of my individual subsystem for the laundry folding device.
The PCB was designed using KiCad and incorporates the electronic components required for my subsystem, including the PIC18F57Q43 Curiosity Nano microcontroller, MCP6004 operational amplifier, voltage regulator, sensors, and supporting circuitry.

## PCB Specifications

| Parameter | Specification |
|-----------|---------------|
| Design Software | KiCad |
| PCB Dimensions | 100 mm x 100 mm |
| Copper Layers | 2 (Front and Back) |
| Copper Thickness | 0.5 oz/ft² |
| Power Input | 9V DC |
| Regulated Voltage | 5V DC |
| Ground Planes | Front and Back |
| Design Rules Check | Passed |

## Front PCB Layout

The front copper layer (F.Cu) contains routed electrical connections, component pads, and a copper ground plane. 

![Front PCB Layout](./images/PCB_Front.png)

**Figure 1:** Front copper layer of the individual subsystem PCB.

## Back PCB Layout

The back copper layer (B.Cu) contains additional electrical connections and a ground plane. Both copper layers are used to complete the circuit routing while maintaining required clearances.

![Back PCB Layout](./images/PCB_Back.png)

**Figure 2:** Back copper layer of the individual subsystem PCB.

## PCB Design Files

The following files contain the completed PCB layout and KiCad design project.

- [Download PCB Layout PDF](PCB_Layout.pdf)
- [Download Complete KiCad Project ZIP](Zarif_EGR304_Subsystem%20%287%29.zip)




