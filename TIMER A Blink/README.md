James Merrill
Intro to Embedded Systems
September 28 2018

# Read Me
In lab 1, one of the activities required was blinking two LEDs and two completely separate frequencies.  This was done to with the use of software loops that caused manual delays between each blink.  For this activity in lab 2, the same objective was stated but with the use of a TIMER A module. This allowed an internal clock, inside the MSP430 device, to run continuously at a specific frequency to toggle two LEDs on the board.  This was done by setting the proper outputs (the 2 LEDS), creating two TIMER A Clocks to run at a specific manageable frequency (I chose the SMCLK with a clock divider of 8), and 2 Capture/Compare interrupt enabled for the TIMERs and then putting in your desired frequency.  This frequency is determined by the equation which I measured by timing the LED flashing at a specific number.  From there, the interrupt functions are very simple and only toggle the LEDs on and off.  This creates two LEDs flashing at complete separate and controllable frequencies.

# TIMER A Blink
The TIMER peripherals can be used in many situations thanks to it flexibility in features. For this lab, you will be only scratching the surface as to what this peripheral can do. 

## Up, Down, Continuous 
There are a few different ways that the timer module can count. For starters, one of the easiest to initialize is Continuous counting where in the TIMER module will alert you when its own counting register overflows. Up mode allows you to utilize a Capture/Compare register to have the counter stop at a particular count and then start back over again. You can also set the TIMER to Up/Down mode where upon hitting a counter or the overflow, instead of setting the counter back to zero, it will count back down to zero. 

## Task
Using the TIMER module instead of a software loop, control the speed of two LEDS blinking on your development boards. Experiment with the different counting modes available as well as the effect of the pre-dividers. Why would you ever want to use a pre-divider? What about the Capture and Compare registers? Your code should include a function (if you want, place it in its own .c and .h files) which can convert a desired Hz into the proper values required to operate the TIMER modules.

### Extra Work
#### Thinking with HALs
So maybe up to this point you have noticed that your software is looking pretty damn similar to each other for each one of these boards. What if there was a way to abstract away all of the particulars for a processor and use the same functional C code for each board? Just for this simple problem, why don't you try and build a "config.h" file which using IFDEF statements can check to see what processor is on board and initialize particular registers based on that.

#### Low Power Timers
Since you should have already done a little with interrupts, why not build this system up using interrupts and when the processor is basically doing nothing other than burning clock cycles, drop it into a Low Power mode. Do a little research and figure out what some of these low power modes actually do to the processor, then try and use them in your code. If you really want to put your code to the test, using the MSP430FR5994 and the built in super cap, try and get your code to run for the longest amount of time only using that capacitor as your power source.
