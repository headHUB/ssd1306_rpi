# ssd1306_rpi
ssd1306 Command Line Tool for Raspberry Pi / Orange Pi

You can operate from command line.  
You can choose Hardware-SPI/Software-SPI/Hardware-I2C/Software-I2C Interface.  
Software-I2C Libray is here. Thank you for usefull library.  
https://github.com/electronicayciencia/wPi_soft_i2c  

Command line parameters:  
+1 String : String for #1 line(with External Font)  
+2 String : String for #2 line(with External Font)  
+3 String : String for #3 line(with External Font)  
+4 String : String for #4 line(with External Font)  
+a String : String for #1 line(with Internal Font)  
+b String : String for #2 line(with Internal Font)  
+c String : String for #3 line(with Internal Font)  
+d String : String for #4 line(with Internal Font)  
-1 : delete #1 line  
-2 : delete #2 line  
-3 : delete #3 line  
-4 : delete #4 line  
+R n : Set inverse mode #n Line  
-R n : Unset inverse mode #n Line  
+U n : Set underline mode #n Line  
-U n : Unset underline mode #n Line  
+L   : Scroll Up 1Line  
-L   : Scroll Down 1Line  
P1 n : Set start colum n to line#1  
P2 n : Set start colum n to line#2  
P3 n : Set start colum n to line#3  
P4 n : Set start colum n to line#4  
r  : remove all string  
s  : show display  

You can use within script.  
#!/bin/bash  
./oled r  
./oled +1 "ABCDEFG"  
./oled +2 "abcdefg"  
./oled +3 "1234567"  
./oled +4 "Hello World!!"  
sudo ./oled s  

---

Wire connection for Hardware SPI

OLED---Raspberry  
Gnd----Gnd  
VCC----3.3V  
SCL----SCLK(Pin#23)  
SDA----MOSI(Pin#19)  
RST----GPIO2 *  
D/C----GPIO4 *  

(*)You can change any pin.  

---

Wire connection for Software SPI

OLED---Raspberry  
Gnd----Gnd  
VCC----3.3V  
SCL----GPIO11 *  
SDA----GPIO10 *  
RST----GPIO2 *  
D/C----GPIO4 *  

(*)You can change any pin.  

---

Wire connection for Hardware I2C

OLED---Raspberry  
Gnd----Gnd  
VCC----3.3V  
SCK----SCL(Pin#5)  
SDA----SDA(Pin#3)  

---

Wire connection for Software I2C

OLED---Raspberry  
Gnd----Gnd  
VCC----3.3V  
SCK----GPIO8 *  
SDA----GPIO7 *  

(*)You can change any pin.  

---

Install for Hardware SPI  
git clone https://github.com/nopnop2002/ssd1306_rpi.git  
cd ssd1306_rpi/  
cc -o oled oled.c fontx.c -lwiringPi -DSPI  
bash ./test.sh  

---

Install for Software SPI  
git clone https://github.com/nopnop2002/ssd1306_rpi.git  
cd ssd1306_rpi/  
cc -o oled oled.c fontx.c -lwiringPi -DSOFT_SPI  
bash ./test.sh  

---

Install for Hardware I2C  
git clone https://github.com/nopnop2002/ssd1306_rpi.git  
cd ssd1306_rpi/  
cc -o oled oled.c fontx.c -lwiringPi -DI2C  
bash ./test.sh  

---

Install for Software I2C  
git clone https://github.com/nopnop2002/ssd1306_rpi.git  
git clone https://github.com/electronicayciencia/wPi_soft_i2c  
cd ssd1306_rpi/  
cp ../wPi_soft_i2c/soft_i2c.* ./  
cc -o oled oled.c fontx.c soft_i2c.c -lwiringPi -DSOFT_I2C  
bash ./test.sh  

---

Left  : OrangePi + SPI Module  
Right : RaspberryPi + I2C Module  

![oled-2](https://user-images.githubusercontent.com/6020549/28252021-b1a9ff4a-6ac5-11e7-9265-b757e4b3cf1d.JPG)

---

![oled-1](https://cloud.githubusercontent.com/assets/6020549/24071131/782737a8-0c0e-11e7-9312-44ec00312f52.JPG)

![oled-2](https://cloud.githubusercontent.com/assets/6020549/25184287/f9945e38-2554-11e7-9075-e63d90b4a3a2.jpg)

![oled-4](https://cloud.githubusercontent.com/assets/6020549/24076582/e037998c-0c77-11e7-9e48-525e27c478a3.JPG)

Line1-2 : External Font  
Line3-4 : Internal Font  


![oled-5](https://cloud.githubusercontent.com/assets/6020549/24293214/f627fefc-10d3-11e7-9304-bcfd58d59d92.JPG)

---

Set start colum  

![oled-6](https://cloud.githubusercontent.com/assets/6020549/24125179/b3b09bfe-0e0a-11e7-83bc-9dbd7b26db18.JPG)


![oled-7](https://cloud.githubusercontent.com/assets/6020549/24125192/d2c40328-0e0a-11e7-8a6a-884c0600059e.JPG)

---

OrangePi ZERO Universal HAT + OLED  

![zero-hat-7](https://user-images.githubusercontent.com/6020549/28547249-00f71026-7109-11e7-9a11-0bbb95423381.JPG)
