# jeff_board
A straightforward Arduino Nano breakout board that allows for driving 2 PWM lines up to 30V, powered on 12/24V, and connects to two thermal sensors. 
-
The jeff board was designed to clean up two temperature sensors and a fan and heater driver into one breakout board, minimizing space occupied on the VAP print-head. Below is a list of the hardware on it, with a brief justification. This device is designed for academic research VAP machines, and is implemented on the systems at Herrick Labs at Purdue University.

<b>Components</b>

<b> Arduino Nano:</b> the Nano is a small-footprint implementation of the arduino uno with some changes to make it ideal for embedded project prototyping. More information can be found on the Arduino website (https://www.arduino.cc/en/Guide/ArduinoNano). The new Arduino Nano Every is a drop-in replacement, and is a bit cheaper. Note: there are hundreds of knock-off Arduino Nanos available for a quarter of the price, most of which will work with this board. If you're not comfortable debugging electronics issues, I recommend sticking to the original.

<b>MLX90614 IR Temperature Sensor:</b> Melexis makes great IR sensors that are easy to interface with over I2C. I used Adafruit's library for this (https://learn.adafruit.com/using-melexis-mlx90614-non-contact-sensors/wiring-and-test). This is where the ambient temperature is determined as well. In the future, moving to a tighter view-angle would be good (right now it's 90deg, sub-15deg would be great). 

<b>MAX31865 RTD Amplifier and Platinum RTD Sensor:</b> I chose an RTD sensor because the reservoir sensing needs to be really accurate right around room temp. We probably won't be heating the reservoir above around 40degC, so this is a good choice. I'm using a MAX31865 breakout board from Adafruit, but there's no reason that can't be added to the PCB in the future. In fact, I'd prefer it. 

<b>MIC4427 and various power MOSFETs:</b> the MIC4427 is a low-side MOSFET driver. This is necessary to avoid over-heating, since the Arduino Nano can't provide enough current to drive the gate capacitance quickly. This should also allow some robustness for knock-off arduinos. The specific power MOSFET isn't as important, as long as it's an N-Channel rated to at least 30Vds, has a low Rdon at Vgs of 5V or lower (this will often be called a logic-level power FET), and has the same pinout in a TO-220 package. For driving the fan, you're going to want a power MOSFET with a body diode. On the jeff board in HERL, I've used IRLB3034PbF which is an extremely robust power MOSFET.

<b>DC-DC Step-Down converter:</b> This board is designed to run off of the 3D printer power supply, both 12V and 24V models. You can use any linear or switching DCDC step-down converter that fits in the TO-220 footprint with the same pinout, but my preference is the Traco Power TSR series (https://www.tracopower.com/products/browse-by-category/show/dc-dc-converters/non-isolated-step-down-regulators/tsr-1/1/). These are really reliable and temperature tolerant, and the last thing we want is the temperature control board to lose power mid-print. 
