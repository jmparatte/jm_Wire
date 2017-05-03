<!--

2017-05-03: 1.0.1
2017-05-01: Initial commit.

Licence: LGPL v3

Author: Jean-Marc Paratte
Email: jean-marc@paratte.ch

-->
# jm_Wire - Revisited Wire Library for Arduino

2017-05-03: 1.0.1

2017-05-01: Initial commit.

This library eliminate all freezing cases and waiting loops.

The provided _jm_LiquidCrystal_I2C_demo_ example demonstrates how it is possible 
to send data to a Hitachi HD44780 or compatible chipsets via I2C without abandon multitasking request.
To illustrate the last sentence, think that the Hitachi HD44780 need about 4.5ms to initialize it or clear it.
The example shows also how to write I2C packets with various delays, by using a fifo buffer.
The multitasking is provided by the jm_Scheduler library.

1.0.1: jm_Write.h and jm_Wire.cpp files are now exactly the same as the original Wire.h and Wire.cpp as found in Arduino 1.8.2 with a little update of declaratives in jm_Wire.cpp.
All true updates are in files jm_twi.h and jm_twi.c.

## Example

    #include <jm_Scheduler.h>
    #include <jm_Wire.h>
    extern uint16_t twi_readFrom_timeout;
    extern uint16_t twi_writeTo_timeout;
    extern bool twi_readFrom_wait;
    extern bool twi_writeTo_wait;
  
    // your code...
  
    void setup(void)
    {
      Wire.begin();
      twi_readFrom_wait = false; // Suppress twi_readFrom() waiting loop
      twi_writeTo_wait = false; // Suppress twi_writeTo() waiting loop
    }
  
    void loop(void)
    {
      // do something funny...
    }

