
---
title: Component Selection
---

# Component Selection — Automated Laundry Folding Device

**Individual Subsystem:** Motor-driven folding flap, light detection, and garment weight sensing.

**Note:** Component choices are preliminary because the final folding flap dimensions, weight, and electrical power requirements have not yet been determined.

## 1. DC Gearmotor

*Table 1: DC Gearmotor Comparison*

| **Solution** | **Pros** | **Cons** |
| --- | --- | --- |
| ![](images/1-1.png)<br>**Option 1:** Pololu 3230 — 12 V, 100 RPM, 25D<br>**$29.95/each**<br>[View Pololu 3230 on DigiKey](https://www.digikey.com/en/products/detail/pololu-corporation/3230/10450096) | &#8226; Operates at 12 V, matching the proposed motor power supply.<br>&#8226; Geared output provides reduced rotational speed.<br>&#8226; Compact 25D motor design with a 4 mm shaft. | &#8226; Output torque has not yet been verified for the folding flap.<br>&#8226; Requires an external motor driver to reverse direction.<br>&#8226; Does not include an encoder for position feedback. |
| ![](images/1-2.png)<br>**Option 2:** Pololu 4847 — 12 V, 100 RPM, Encoder<br>**$56.95/each**<br>[View Pololu 4847 on DigiKey](https://www.digikey.com/en/products/detail/pololu/4847/10450249) | &#8226; Integrated encoder provides rotational feedback.<br>&#8226; Operates using a 12 V supply.<br>&#8226; Geared output is suitable for controlled movement. | &#8226; More expensive than the other candidates.<br>&#8226; Encoder requires additional microcontroller input connections.<br>&#8226; Available torque still needs to be verified. |
| ![](images/1-3.png)<br>**Option 3:** Pololu 4745 — 12 V, 100 RPM, 37D<br>**Price to verify**<br>[View Pololu 4745 on DigiKey](https://www.digikey.com/en/products/detail/pololu/4745/10450202) | &#8226; Larger gearmotor family may support heavier mechanical loads.<br>&#8226; Compatible with a proposed 12 V supply.<br>&#8226; Brushed DC motor supports reversible operation. | &#8226; Larger dimensions require more mounting space.<br>&#8226; Increased motor weight may complicate mechanical installation.<br>&#8226; Torque and current requirements still need confirmation. |

**Choice (Provisional):** Option 1 — Pololu 3230 DC Gearmotor.

**Rationale:** The Pololu 3230 provides a reasonable preliminary balance of size, speed, and cost for controlling one folding flap. Its 12 V operating voltage would allow it to share a motor supply with other folding mechanisms. The geared output reduces rotational speed compared with an ungeared motor. However, the final selection will depend on the torque required to lift the flap and clothing, the desired folding time, and the motor's stall current.

---

## 2. H-Bridge Motor Driver

*Table 2: H-Bridge Motor Driver Comparison*

| **Solution** | **Pros** | **Cons** |
| --- | --- | --- |
| ![](images/2-1.png)<br>**Option 1:** STMicroelectronics L293D<br>**$10.06/each**<br>[View L293D on DigiKey](https://www.digikey.com/en/products/detail/stmicroelectronics/L293D/634700) | &#8226; Dual H-bridge design can control two brushed DC motors.<br>&#8226; Through-hole DIP package simplifies prototyping and replacement.<br>&#8226; Supports a 12 V motor supply. | &#8226; Approximately 600 mA continuous output rating may be insufficient for the selected motor.<br>&#8226; Bipolar output transistors produce significant voltage drops and heat.<br>&#8226; Does not provide integrated motor current sensing. |
| ![](images/2-2.png)<br>**Option 2:** Texas Instruments DRV8871DDAR<br>**$2.98/each**<br>[View DRV8871 on DigiKey](https://www.digikey.com/en/products/detail/texas-instruments/DRV8871DDAR/5639726) | &#8226; Supports motor supply voltages from 6.5 V to 45 V.<br>&#8226; Integrated H-bridge provides bidirectional motor control.<br>&#8226; Includes current regulation and protection features. | &#8226; Controls only one DC motor.<br>&#8226; Surface-mount PowerPAD package requires careful PCB design.<br>&#8226; Thermal performance must be checked for the motor load. |
| ![](images/2-3.png)<br>**Option 3:** Texas Instruments DRV8876PWPR<br>**$1.95/each**<br>[View DRV8876 on DigiKey](https://www.digikey.com/en/products/detail/texas-instruments/DRV8876PWPR/10270191) | &#8226; Supports a motor supply voltage range of 4.5 V to 37 V.<br>&#8226; Integrated MOSFET H-bridge supports forward and reverse rotation.<br>&#8226; Includes motor protection features and has a relatively low unit cost. | &#8226; Controls only one DC motor.<br>&#8226; Surface-mount package requires appropriate soldering and PCB layout.<br>&#8226; Continuous output current depends on thermal conditions. |

**Choice (Provisional):** Option 3 — Texas Instruments DRV8876PWPR.

**Rationale:** The DRV8876 is a promising motor driver for controlling the folding flap because it supports bidirectional rotation, allowing the flap to move into its folding position and return to its original position. Its operating voltage range supports the proposed 12 V motor supply, while its integrated protection features are beneficial for a mechanism that may experience mechanical resistance. The final choice must be verified against the motor's stall current and thermal requirements. If the team decides to share a dual-channel driver, this selection may change.

---

## 3. Photoresistor (LDR)

*Table 3: Photoresistor Comparison*

| **Solution** | **Pros** | **Cons** |
| --- | --- | --- |
| ![](images/3-1.png)<br>**Option 1:** Advanced Photonix PDV-P8001<br>**$1.60/each**<br>[View PDV-P8001 on DigiKey](https://www.digikey.com/en/products/detail/advanced-photonix/PDV-P8001/480602) | &#8226; Low-cost light-sensitive resistor.<br>&#8226; Through-hole construction simplifies installation.<br>&#8226; Can be connected to a microcontroller ADC using a voltage divider. | &#8226; Requires calibration for different lighting conditions.<br>&#8226; Ambient lighting changes may cause incorrect detection.<br>&#8226; Cannot directly distinguish clothing from other objects. |
| ![](images/3-2.png)<br>**Option 2:** Advanced Photonix PDV-P8103<br>**$0.72/each**<br>[View PDV-P8103 on DigiKey](https://www.digikey.com/en/products/detail/advanced-photonix/PDV-P8103/480610) | &#8226; Very inexpensive compared with the other candidates.<br>&#8226; Through-hole leads simplify circuit assembly.<br>&#8226; Higher resistance can reduce voltage-divider current consumption. | &#8226; Requires a voltage-divider circuit and calibration.<br>&#8226; Readings can vary with room lighting.<br>&#8226; Response is slower than many semiconductor optical sensors. |
| ![](images/3-3.png)<br>**Option 3:** Advanced Photonix PDV-P8104<br>**$0.90/each**<br>[View PDV-P8104 on DigiKey](https://www.digikey.com/en/products/detail/advanced-photonix/PDV-P8104/480611) | &#8226; Low-cost light detection solution.<br>&#8226; High resistance under low illumination conditions.<br>&#8226; Through-hole package simplifies prototyping. | &#8226; Higher resistance circuits may be more sensitive to electrical noise.<br>&#8226; Detection thresholds depend on ambient illumination.<br>&#8226; Requires calibration and suitable sensor placement. |

**Choice (Provisional):** Option 2 — Advanced Photonix PDV-P8103.

**Rationale:** The PDV-P8103 is a suitable preliminary choice for detecting changes in illumination when clothing or a folding flap blocks a light source. Its low cost and simple voltage-divider interface make it convenient for integration with the microcontroller. However, the sensor must be tested under different lighting conditions to determine an appropriate detection threshold and minimize false readings.

---

## 4. Weight Sensor / Load Cell

*Table 4: Weight Sensor Comparison*

| **Solution** | **Pros** | **Cons** |
| --- | --- | --- |
| ![](images/4-1.png)<br>**Option 1:** SparkFun 14729 — 5 kg Load Cell<br>**$17.81/each**<br>[View SparkFun 14729 on DigiKey](https://www.digikey.com/en/products/detail/sparkfun-electronics/14729/9555603) | &#8226; 5 kg measurement capacity provides room for different garment weights.<br>&#8226; Straight-bar construction can be mounted beneath a weighing platform.<br>&#8226; Produces an electrical signal related to the applied load. | &#8226; Requires rigid and properly aligned mechanical mounting.<br>&#8226; Small sensor output requires amplification and precision conversion.<br>&#8226; Measurement range may be larger than necessary for lightweight garments. |
| ![](images/4-2.png)<br>**Option 2:** SparkFun 13329 — 10 kg Load Cell<br>**$15.15/each**<br>[Search Load Cells on DigiKey](https://www.digikey.com/en/products/filter/industrial-sensors/force-sensors-load-cells-industrial/1066) | &#8226; Higher load capacity supports heavier objects.<br>&#8226; Compact design may suit localized force measurement.<br>&#8226; Can measure applied force through mechanical loading. | &#8226; Higher measurement range may reduce sensitivity to lightweight clothing.<br>&#8226; Proper contact and load alignment are required.<br>&#8226; Additional signal-conditioning electronics are needed. |
| ![](images/4-3.png)<br>**Option 3:** SparkFun 14728 — 0.5 kg Load Cell<br>**$15.50/each**<br>[Search Load Cells on DigiKey](https://www.digikey.com/en/products/filter/industrial-sensors/force-sensors-load-cells-industrial/1066) | &#8226; Lower measurement capacity is potentially useful for lightweight garments.<br>&#8226; Compact sensor for small-load measurements.<br>&#8226; Relatively affordable sensing solution. | &#8226; May overload when heavier garments are placed on the platform.<br>&#8226; Requires appropriate mechanical mounting.<br>&#8226; Requires amplification and calibration for accurate measurements. |

**Choice (Provisional):** Option 1 — SparkFun 14729, 5 kg Load Cell.

**Rationale:** The SparkFun 14729 is a preliminary choice for measuring the weight of clothing placed on the folding platform. Its 5 kg measurement capacity provides flexibility for garments of different weights while remaining suitable for a compact sensing arrangement. The final selection will depend on the expected clothing weight, the weight of the supporting platform, and the mechanical installation. A load-cell amplifier and ADC will be used to convert the small sensor signal into digital measurements for the microcontroller.

---

## 5. Load-Cell Amplifier / ADC

*Table 5: Load-Cell Amplifier Comparison*

| **Solution** | **Pros** | **Cons** |
| --- | --- | --- |
| ![](images/5-1.png)<br>**Option 1:** SparkFun 13879 — HX711 Breakout<br>**$11.50/each**<br>[View SparkFun HX711 on DigiKey](https://www.digikey.com/en/products/detail/sparkfun-electronics/13879/6202732) | &#8226; Designed specifically for interfacing with load cells.<br>&#8226; Converts small analog load-cell signals into digital measurements.<br>&#8226; Breakout board simplifies connection to a microcontroller. | &#8226; Adds an additional circuit board and wiring.<br>&#8226; Requires calibration for accurate weight measurement.<br>&#8226; Limited sampling rate compared with some general-purpose ADCs. |
| ![](images/5-2.png)<br>**Option 2:** Soldered Electronics 333005 — HX711 Breakout<br>**$5.72/each**<br>[View Soldered HX711 on DigiKey](https://www.digikey.com/en/products/detail/soldered-electronics/333005/21720457) | &#8226; Lower price than the other breakout candidates.<br>&#8226; Dedicated HX711 interface for bridge-type load cells.<br>&#8226; Digital output simplifies microcontroller integration. | &#8226; Requires an additional module and wiring.<br>&#8226; Calibration is necessary for accurate measurements.<br>&#8226; Pin arrangement and interface compatibility must be checked. |
| ![](images/5-3.png)<br>**Option 3:** Adafruit 5974 — HX711 24-bit ADC Breakout<br>**$9.95/each**<br>[View Adafruit HX711 on DigiKey](https://www.digikey.com/en/products/detail/adafruit-industries-llc/5974/24639130) | &#8226; Uses a 24-bit ADC designed for load-cell applications.<br>&#8226; Provides digital measurements to the microcontroller.<br>&#8226; Breakout-board construction simplifies prototyping. | &#8226; More expensive than the Soldered Electronics option.<br>&#8226; Requires additional wiring and board space.<br>&#8226; Measurements require calibration and noise management. |

**Choice (Provisional):** Option 2 — Soldered Electronics 333005 HX711 Breakout.

**Rationale:** The Soldered Electronics 333005 provides a relatively inexpensive method of interfacing a bridge-type load cell with the microcontroller. The HX711 amplifies the small load-cell signal and performs analog-to-digital conversion, allowing the system to obtain garment weight measurements. Since all three candidates use the HX711, the final selection is based primarily on cost, integration convenience, and board compatibility.

---

## 6. Wall Power Adapter

*Table 6: Wall Power Adapter Comparison*

| **Solution** | **Pros** | **Cons** |
| --- | --- | --- |
| ![](images/6-1.png)<br>**Option 1:** Bel Power SDI65-12-UDC-P5 — 12 V, 5 A, 60 W<br>**$47.95/each — verify price**<br>[View Bel Power Adapter on DigiKey](https://www.digikey.com/en/products/detail/bel-power-solutions/SDI65-12-UDC-P5/5297523) | &#8226; Regulated 12 V output is compatible with the proposed motor supply.<br>&#8226; Provides up to 5 A and 60 W of output power.<br>&#8226; Commercial external adapter avoids designing a mains-voltage supply. | &#8226; Available current may be insufficient if several motors start simultaneously.<br>&#8226; Requires a compatible DC power connector.<br>&#8226; AC input cord configuration must be verified. |
| ![](images/6-2.png)<br>**Option 2:** Bel Power SDI65-12-UD-P5 — 12 V, 5 A, 60 W<br>**$38.60/each — verify price**<br>[Browse Wall Adapters on DigiKey](https://www.digikey.com/en/products/filter/ac-dc-desktop-wall-power-adapters/130) | &#8226; Regulated 12 V output supports the proposed motors.<br>&#8226; Lower listed price than Option 1.<br>&#8226; Provides a nominal 60 W power output. | &#8226; AC input cord may need to be purchased separately.<br>&#8226; Total current consumption of the machine must be calculated.<br>&#8226; Output connector compatibility must be verified. |
| ![](images/6-3.png)<br>**Option 3:** Bel Power SDI65-12-UC-P5 — 12 V, 5 A, 60 W<br>**Price to verify**<br>[View Bel Power Supply Family on DigiKey](https://www.digikey.com/en/products/filter/ac-dc-desktop-wall-power-adapters/130) | &#8226; Candidate for a shared 12 V power source.<br>&#8226; Commercial desktop adapter simplifies integration.<br>&#8226; May provide a common supply for several subsystems. | &#8226; Exact price and configuration require verification.<br>&#8226; The 5 A output limit may be insufficient for simultaneous motor loads.<br>&#8226; May require additional voltage regulation for logic circuits. |

**Choice (Provisional):** Option 1 — Bel Power SDI65-12-UDC-P5.

**Rationale:** The Bel Power SDI65-12-UDC-P5 is a preliminary candidate for powering the automated laundry-folding device from a single external wall adapter. Its regulated 12 V output is compatible with the proposed DC motor power rail. The adapter could distribute power to multiple folding subsystems, reducing the need for separate wall adapters. However, the final supply must be selected after calculating the total current consumption of all motors and electronics, including the required 25% safety margin. Additional voltage regulation may be necessary for lower-voltage microcontroller and sensor circuits.

---

## Preliminary Pin Table

| **Component / Signal** | **Microcontroller Pin** | **Function** |
| --- | --- | --- |
| H-bridge control input 1 | TBD | Controls motor direction |
| H-bridge control input 2 / PWM | TBD | Controls motor direction and speed |
| Photoresistor voltage-divider output | TBD — ADC | Measures light intensity |
| Load-cell ADC data output | TBD | Receives weight measurements |
| Load-cell ADC clock input | TBD | Controls data communication |
| Limit switch input, if used | TBD | Detects flap end position |

---

## Design Considerations

The component selections above are preliminary and will be updated as the automated laundry-folding device progresses through the design process.

The following requirements must be verified before final component selection:

- Folding flap dimensions, weight, and hinge geometry.
- Required motor torque and desired folding speed.
- Motor startup and stall current.
- H-bridge voltage, current, and thermal compatibility.
- Microcontroller operating voltage and available interface pins.
- Weight sensor range and mounting arrangement.
- Photoresistor performance under different lighting conditions.
- Total electrical current required by all team subsystems.
- Compatibility of the shared wall adapter and voltage regulator.
- Final microcontroller pin assignments.

The completed design will be coordinated with the other team subsystems to ensure compatible electrical interfaces and reliable operation.


