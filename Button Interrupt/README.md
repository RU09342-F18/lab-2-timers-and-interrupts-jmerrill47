James Merrill
Intro to Embedded Systems
September 28 2018

# Read Me
The Button Interrupt activity acted as a further exploration of the toggling done in lab 1.  With knowledge of interrupts, instead of linking the button right to the LED, the button was linked to an interrupt which causes the LED to Toggle. To set the program up, you need to disable the watchdog timer, set the proper output (LED), enable the interrupt for the button (with all of its features), enable the pull up resistor and clear the interrupt flags for the button.  You then need to set it to the proper Low Power Mode that allows the button to function as an interrupt trigger.  After this is set up, the rest of the code is easy.  You need to set up the interrupt function and for this lab it's toggling the LED back and forth which includes a XOR gate and clearing the interrupt flags connected to the button.
