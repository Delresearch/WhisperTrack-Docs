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

Coming Soon!

## Hardware Costs

Details Coming Soon!