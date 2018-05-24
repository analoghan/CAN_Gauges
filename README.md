# CAN_Gauges
Arduino/Teensy CAN Gauges with OLED displays

**This sketch is designed to use the following libraries:**

* Cory Fowler's MCP_CAN:https://github.com/coryjfowler/MCP_CAN_lib
* Nox771's i2c_t3: https://github.com/nox771/i2c_t3
* Adafruit GFX: https://github.com/adafruit/Adafruit-GFX-Library
* Adafruit SSD1306: https://github.com/adafruit/Adafruit_SSD1306

**Hardware used is:**

* Teensy 3.2
* SPI bus MCP2515 CAN Adapter
* TCA9548A IIC/I2C 8 channel Multiplexer
* 4x .96" IIC/I2C OLED displays

As built it is tuned for a Teensy 3.2 (but will run on a 3.5/3.6 for sure, though not a Teensy LC).   As such it uses the  i2c_t3 library; however it can use wire.h and run on an Arduino but you will need to adjust the I2C data rate beyond the default 100khz to 400khz or higher.    I am currently running at >1Mhz, which works fine with my wiring and my Teensy, but your mileage may vary, the SSD1306 displays are only rated at 400khz, officially.   I cannot guarantee interrupt behavior on Arduino or other boards, it works properly on Teensy 3.2, 3.5 adn 3.6 from my testing.

CAN decoding/math is currently setup for an AEM Infinity system, using 29 bit addresses and running filters for CAN ID: 0 through D.    This can be adjusted pretty easily, you will simply need the documentation from your manufacturer (or you can reverse engineer it).   This currently only listens/ACKs messages and does not send.

There are several gauges that function simply as performnace/functionality tests in this build.   These will eventually be removed but are currently there to profile performance of the program. 

The button is intended to switch between multiple sets of (up to 4) gauges and is eletrically configured like most example "momentary buttons" on various Arduino/Teensy tutorials.
