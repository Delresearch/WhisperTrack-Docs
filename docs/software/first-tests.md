# First Air Tests
## Setup
- Using 2 modems with 2 transducers, flash the modems with the [latest firmware](Build WhisperTrack.md).  
- Ensure that the modems are connected to the transducers and powered on.
- Place the transducers 6 inches apart.
## Testing
- Open the modem console for the device that will be acting at the receiver to monitor the incoming data.
- Open the modem console for the device that will be acting as the transmitter.
- In the transmitter console, enter the command `starttx` with a message to send.
- Observe the receiver console for the incoming message and verify the CRC pass with a response message to the transmitter.
- Repeat the process with different messages to ensure consistent communication.

If the messages are not received or the CRC fails there are some troubleshooting steps you can find [here](../Other%20Resources/troubleshooting.md).