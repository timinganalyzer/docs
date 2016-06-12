DigitalClock API 
==========================

The constructors are used to specify the parameters of the clock. Synchronous 
events are usually connected to edges in the DigitalClock. Increasing the clock 
frequency is a common operation used to check if the logic design still meets 
all the constraints. 

All signals below the clock are considered to synchronous to this clock when 
adding pulses to other signals. Jitter is not functional at this time and 
should be set to 0.0.  It will be be used to model the accuracy of a clock 
in ppms. 


Adding Clocks
^^^^^^^^^^^^^^
    

.. function :: addDigitalClock(String name, String startState, double frequency)

    Adds a DigitalClock to this timing diagram. It creates a new instance of a 
    DigitalClock object.

    Duty cycle, signal height, space above, riseTime, and fallTime are set to default values.

    Returns a Digital Clock object. ::

        dclk = timDiagram.addDigitalClock("CLK25", "H", 25e6)

.. function :: addDigitalClock(String name, String startState, double frequency, int dutyCycle) 

    Adds a DigitalClock to this timing diagram. It creates a new instance of a 
    DigitalClock object.

    Signal height, space above, riseTime, and fallTime are set to default values.

    Returns a Digital Clock object. ::

        dclk = timDiagram.addDigitalClock("CLK25", "H", 25e6, 40)

.. function :: addDigitalClock(String name, double frequency, String startState, int dutyCycle, double riseTime, double fallTime) 

    Adds a DigitalClock to this timing diagram. It creates a new instance of a 
    DigitalClock object.

    Signal height and space above are set to default values.

    Returns a Digital Clock object. ::

        dclk = timDiagram.addDigitalClock("CLK25", 25e6, "H", 40, 2.0e-9, 2.0e-9)


Getters and Setters 
^^^^^^^^^^^^^^^^^^^
        
.. function :: setFrequency(double frequency)

    Set the Clock Frequency. This can be used to test faster clocks in systems 
    to see if the design meets the defined timing constraints. ::

         dclk.setFrequency(50e6)

.. function :: getFrequency() 

    Returns a double that equals the Clock Frequency. ::  

        currentFrequency = dclk.getFrequency()



.. function :: setDutyCycle(int dutycycle) 

    Set the Clock Duty Cycle. ::  

        dclk.setDutyCycle(40)

.. function :: getDutyCycle()

    Returns an integer that is the clock duty cycle. ::   

        dutyCycle = dclk.getDutyCycle()



.. function :: setJitter(double jitter)

    Set the Clock Jitter. This can be used to model the clock accuracy in ppms. 
    Currently, this is not functional and is set to 0.0

.. function :: getJitter() 

    Returns a double that is the Clock Jitter. :: 

        clkJitter = dclk.getJitter()



.. function :: setStartDelay(double startDelay)

    Set the Clock Start Delay. This can be used to shift a clock in time, so 
    you can make a clock that is out of phase with another clock. A feature 
    coming will link the clocks together. ::

         dclk.setStartDelay(25.0e-9)

.. function :: getStartDelay()

    Returns a double that is the Clock Start Delay. ::

        startDelay = dclk.getStartDelay()
