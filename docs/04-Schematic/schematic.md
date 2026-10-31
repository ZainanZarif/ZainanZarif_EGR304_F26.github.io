---
Individual Subsystem Schematic
---

## Overview

<img src="https://raw.githubusercontent.com/ZainanZarif/ZainanZarif_EGR304_F26.github.io/d76dfbf76d025156072acaff80462c2084526dc9/docs/04-Schematic/Pictures/Zarif_EGR304_Subsystem.svg" width="100%">

**Figure #1:** Complete individual subsystem schematic.

### Schematic Description

The individual subsystem schematic is organized into five main sections: the Curiosity Nano microcontroller circuit, power supply circuit, op-amp and filter circuit, ribbon connectors, and extra GPIO headers. A 9V DC supply is regulated to 5V using the L7805 voltage regulator to power the system. The photoresistor detects changes in light intensity, and the MCP6004 op-amp circuit conditions the sensor signal before sending it to the microcontroller. The design also includes control buttons, a status LED, UART connections for communication with other subsystems, and spare GPIO pins for future expansion. Test points are included at key locations to simplify debugging and voltage measurements.

## Resources

The individual subsystem schematic is available as a PDF download [**here**](files/Zarif_EGR304_Subsystem.pdf), and the complete KiCad project ZIP file is available [**here**](files/Zarif_EGR304_Subsystem%20%286%29.zip).



