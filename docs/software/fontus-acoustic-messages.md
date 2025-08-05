# Fontus Acoustic Messages (FAMs)
 
Fontus Acoustic Messages (**FAMs**) are the standardized 64-bit packets used in the FONTUS underwater acoustic communication protocol. All messages follow the format defined in the [Fontus Bit Definitions Specification v0.3](../assets/files/fontus_bit_definitions_v0.1.pdf).
 
## Overview
 
* **Message Length:** 64 bits
* **Data Payload:** 48 bits (variable by message type)
* **CRC:** 16-bit CRC (bits 48–63), computed over the first 48 bits
* **First Field:** The first 6 bits of every FAM are the `message type` field, which determines the layout and meaning of the rest of the message.
 
## CRC Behavior
 
Each message includes a **16-bit CRC**, computed over the **first 48 bits** of the message:
 
* On **reception**:
 
  * Compute the CRC of bits `0–47` and compare with bits `48–63`.
  * If they match, the message is a valid **public** (non-authenticated) message.
  * If they don't match, append the device's **32-bit passkey** to the 48-bit data and recompute.
 
    * If the new CRC matches, the message is a valid **authenticated** (private) message.
 
This mechanism supports both public and authenticated messages using a single format.
 
## Message Types
 
There are currently 10 defined message types:
 
| Type | Name                 | Direction     | Description                                         |
| ---- | -------------------- | ------------- | --------------------------------------------------- |
| 0    | Localization Request | Ship → Device | Request for device localization and depth           |
| 1    | Localization Report  | Device → Ship | Reports response delay, depth, battery, sensors     |
| 2    | Release Request      | Ship → Device | Requests device to activate its release mechanism   |
| 3    | Release Report       | Device → Ship | Reports result of release activation                |
| 4    | Lost Device Request  | Ship → Device | Broadcast to locate recently lost gear              |
| 5    | Lost Device Report   | Device → Ship | Reports device ID and status (if considered lost)   |
| 6    | Status Request       | Ship → Device | Requests device status (e.g., release, sensors)     |
| 7    | Status Report        | Device → Ship | Reports release status, battery, depth, orientation |
| 8    | Vendor Request       | Ship → Device | Sends vendor-specific payload (authenticated)       |
| 9    | Vendor Report        | Device → Ship | Returns vendor-specific data                        |
 
Refer to **Table 3** in the Fontus specification for detailed field layouts and bit allocations.
 
## YAML-Based Message Definitions
 
To avoid hardcoding the bit-level layout of each message type, we use [YAML files](../software/YAML-code-generation.md) to define:
 
* **Field names** and **bit positions**
* **Scaling functions** for fields (e.g., depth, battery voltage)
* **Fallback values** for invalid/missing data
* **CRC configuration** (typically bits `48–63`)
 
This makes it easy to evolve the protocol without rewriting the parsing/filling code for the bit field of each message type. This also makes extending the protocols supported message types as the spec supports up to 64 message types.
 
## FAM Processing Pipeline
 
FAMs which have valid CRC are processed in a modular pipeline, where each stage is referred to as an **Action**. An Action represents a single processing step, such as reading a value, applying a transformation, or writing output. The following stages outline a typical Action sequence:
 
### 1. Decode Messages With Valid CRC
 
* Extract raw fields (defined in YAML) from the incoming 64-bit FAM
* or read values from the modem's state (e.g., sensor readings, memory)
 
### 2. Transform
 
* Apply scaling or conversion functions according to the spec
 
### 3. Execute
 
* Use the transformed values to fill a FAM field, trigger actions, or update state, etc.
 
For each message type, we can compose a list of **Actions** to execute in order to build up a FAM to transmit. These same Actions can also be used to trigger changes in the trap modem.
 
## Implementation Notes
 
* All FAMs must begin with a **6-bit message type** field.
* All FAMs end with a **16-bit CRC**, covering the first 48 bits.
* Private (authenticated) messages are validated using a passkey as part of CRC calculation.
* Optional fields such as battery, temperature, and orientation include special values indicating missing sensors or invalid data.
* Vendor messages support custom payloads of 17 bits (downlink) and 30 bits (uplink).