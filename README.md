<!--

2017-05-01: Initial commit.

Licence: LGPL v3

Author: Jean-Marc Paratte
Email: jean-marc@paratte.ch

-->
# jm_Wire - A revisited Wire Library for Arduino

2017-05-01: Initial commit.

This library eliminate all freezing cases and waiting loop.

The provided _jm_LiquidCrystal_I2C_demo_ example demonstrates how it is possible 
to send data to a Hitachi HD44780 or compatible chipsets via I2C without abandon multitasking request.
To illustrate the last sentence, think that the Hitachi HD44780 need about 4.5ms to initialize it or clear it.
The example shows also how to write I2C packets with various delays, by using a fifo buffer.
The multitasking is provided by the jm_Scheduler library.

## Example

    #include <jm_Scheduler.h>
    #include <jm_Wire.h>
  
    // your code...
  
    void setup(void)
    {
      Wire.begin();
    }
  
    void loop(void)
    {
      // do something funny...
    }

