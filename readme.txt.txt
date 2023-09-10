
stm32 test proj to read adafruit power sensor ina260
Ju Wang, 2023

----9/9/23 -------------------
ina260 code from 
	https://github.com/ardnew/INA260-STM32-HAL
copy ina260.h .c file to core/include and core/src
note i2c address no need to <<1
sprintf %d. dont %u since negative value is possible and cause strange print value
juwangvsu git repo 

use i2c3, cubemx warning conflict with usb otg, but it still work seems
parts:
	f407 disc1 board + usb-serial adapter
	adafruit ina260 
	motor driver board + 3s batt + motor
wiring:
	all board use 5v/gnd from f401 board
	f407 i2c3:
		sda, scl = pc9, pa8 <-----------> ina260 sda, scl
		
	f407 usart2	
		tx, rx = pa2 pa3  <--------------> usb-serial rx, tx
	ina260:
		vcc,gnd sda, scl see above
		vin+ <-------> batt + 
		vin- <------->  motor board +
	ina260 gnd <--------> batt -
		this can be skipped here since the motor driver ground is also connected to batter -
	the ina260 is inserted inline to the load. see photo
	
	
