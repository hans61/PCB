8 Bit Audo with the TLC7524
===========================
This is a small circuit board to test 8 bit audio on the Gigatron. The circuit is from Axelb, thank you very much. Unfortunately I made a mistake. Pin 3 of the MCP6022 is connected to RFB (16). The connection must be separated and a wire must be soldered to VREF (15).
To test the DAC, I first connected it to an Arduino Uno. With the Gigatron it can be connected to the new extension of lb3361. Many thanks to lb3361 for his work. The following connections must be established:

|Expansion|TLC7524|
|-----------|-----------|
|VCC|+5V|
|/AUXCTRL|/WR|
|/AUXDEV0|/CS|
|A8-A15|D0-D7|
|GND|GND|

In order for the TLC7524 to accept the data, the /WR of GAL1 must be negated.
I changed line 65:
DEVCLKOUT = !(OE & WE & SPECIALCODE);
