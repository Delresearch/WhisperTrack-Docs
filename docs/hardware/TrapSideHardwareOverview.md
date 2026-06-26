# WhisperTrack Trap-Side Hardware Overview
## WhisperTrack Trap-Side Hardware System Block Diagram

![image](../assets/images/hardware/WhisperTrack_TrapSide_Modem_Block_Diagram.png)

## Trap-Side Printed Circuit Board Assembly (PCBA) 3D Renderings

![image](../assets/images/hardware/PCBA_top.png)

![image](../assets/images/hardware/PCBA_top_iso.png)

![image](../assets/images/hardware/PCBA_bottom.png)

![image](../assets/images/hardware/PCBA_bottom_iso.png)

The above 3D renderings of the PCBA are shown with the piezoelectric tube mounted.

## Trap-Side Modem Photos

![image](../assets/images/hardware/modem-no-ring-bottom.png)

![image](../assets/images/hardware/modem-bottom-angled.png)

## External Electrical Interface

The external electrical interface of the WhisperTrack Trap-Side Modem consists of a six-conductor cable (Alpha Wire 25106 BK199). The wiring assignments are given below: 

| Conductor | Color | Function | Notes |
| -------- | ------- | ------- |------- |
| 1 | BLACK | GND | 0VDC |
| 2 | BROWN | BOOT0_N | Connect to GND before power up to put modem in ROM bootloader mode |
| 3 | RED | VIN | +12 VDC to +42 VDC |
| 4 | ORANGE | RS-232 RXD | RS-232-compliant voltage levels |
| 5 | YELLOW | RS-232 TXD | RS-232-compliant voltage levels |
| 6 | GREEN | Trigger | Diode-blocked internal pull-up to +1.85V. Allowable external pull-up to +50V |

One method to communicate with the Trap-Side Modem via RS-232 is by using a USB-to-RS232 adapter cable, such as [FTDI USB-RS232-WE-1800-BT_5.0](https://ftdichip.com/products/usb-rs232-we-1800-bt_5-0/). If using this adapter cable, then BLACK, ORANGE, & YELLOW wires can be connected directly together between the Trap-Side Modem and the adapter cable.

## Transmit Amplitude

The Trap-Side Modem's transmit amplitude is directly set by the boost converter's output voltage. The boost converter can be set to 24V, 36V, or 48V. The power consumption during transmit will change proportionally with the boost converter output voltage setting. 

## Power Consumption

With the minimum supply voltage of 12V, the power consumption during Receive mode is approximately 15mW using the 068-0098-00 hardware. 

## Hardware Costs

Quotes based on 068-0098-00 hardware from July 2025 at both Domestic (USA) and China-based contract manufacturers. No tariffs are included in these cost figures.

| Part Number | Description | Domestic Qty 12 Unit Cost | Domestic Qty 100 Unit Cost | Domestic Qty 1000 Unit Cost | China Qty 12 Unit Cost | China Qty 100 Unit Cost | China Qty 1000 Unit Cost |
|---|---|---:|---:|---:|---:|---:|---:|
| 050-0098-00 | PCB JMJ POPOTO WHISPERTRACK MODEM BOARD | $90.32 | $13.60 | $5.60 | $30.00 | $5.03 | $2.54 |
| 094-0098-00 | ELEC BOM JMJ POPOTO WHISPERTRACK MODEM BOARD | $102.80 | $88.33 | $56.53 | $102.22 | $68.68 | $56.03 |
| 068-0098-00 | JMJ POPOTO WHISPERTRACK MODEM BOARD - ADDITIONAL ASSEMBLY COSTS | $219.41 | $82.95 | $44.14 | $21.73 | $5.62 | $2.56 |
|  | 068-0098-00 SUBTOTAL (UNIT COST) | $412.53 | $184.88 | $106.27 | $153.95 | $79.33 | $61.13 |
|  | 068-0098-00 SUBTOTAL (TOTAL COST) | $4,950.38 | $18,487.60 | $106,265.60 | $1,847.37 | $7,933.37 | $61,129.00 |
| 014-0066-00 | Piezo Cylinder:<br>C-38.00mm-34.00mm-25.00mm-Type II (ID +)<br>OD±0.35mm ID±0.35mm Ln±0.15mm <br>APC International 42-1052 | $71.98 | $57.97 | $46.06 | $71.98 | $57.97 | $46.06 |
| 036-0020-00 | CABLE 6COND 22AWG BLK SHLD FEET | $9.08 | $7.15 | $6.12 | $9.08 | $7.15 | $6.12 |
| TBD | Potting Material |  |  |  |  |  |  |
| TBD | 3D print mounting flange |  |  |  |  |  |  |
| TBD | 3D print potting mold |  |  |  |  |  |  |
|  | **Grand Total Unit Cost** | **$493.59** | **$250.00** | **$158.45** | **$235.00** | **$144.46** | **$113.31** |
|  | **Grand Total Cost** | **$5,923.04** | **$24,999.87** | **$158,449.85** | **$2,820.03** | **$14,445.64** | **$113,313.25** |