Author(s): Simon R.
Here are some notes about the arduino code and the build process of the Jeff board in March 2020.

*Arduino Code:*
The code provides a readout of RTD and IR sensor data over serial to a laptop running a serial monitor (such as the one included as part of the Arduino IDE).
To compile, it requires the Adafruit libraries for the MLX90614 IR sensor and the MAX31865 RTD breakout/reader which can be located within the links below.

https://learn.adafruit.com/adafruit-max31865-rtd-pt100-amplifier/arduino-code
https://learn.adafruit.com/using-melexis-mlx90614-non-contact-sensors/wiring-and-test


It would be nice if it wasn't necessary to use a laptop to read the sensor data. 
Adding a simple 16x2 display to solve this issue would be very easy.
Adafruit provides Arduino libraries that make interfacing with displays (such as the one linked below) very easy.
https://www.adafruit.com/product/181
And a Arduno library for this: https://learn.adafruit.com/character-lcds/arduino-code


*Notes on the PCB assembly process:*
The design specified SMD resistors of 0805 size, but 0603 were used instead as no 0805 were available. 
The actual resistance values were correct, and since the wattage being dissipated is quite low, the 0603 substitutes are functionally equivalent.

Ceramic caps of 0603 size were substituted in for the polarity-sensitive electrolytic caps that were implied in the pcb silkscreen and KiCad footprints.
The actual capacitance values were correct and are functionally equivalent.


*Finally:*
If making another board, please note that the mic4427ym component is not the correct package/footprint. It's important to note that as of March 2020, the footprint of the mic4427ym in the KiCad drawing does not reflect any available footprint of the mic4427ym as found on the web.
This may have been a design mistake, or simply the original package is no longer available. 
Either way: you can get around this by using a breakout board suitable for the mic4427ym IC itself and merging connections to the jeffBoard or by redesigning the footprint assignment on the jeffBoard to eliminate the mismatch.




