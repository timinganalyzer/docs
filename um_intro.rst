Introduction 
=================================


Drawing Timing Diagrams -- The Basics
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

The most common way to draw timing diagrams is by using the Graphical User Interface (GUI). 
There are example timing diagrams in the examples directory and there is also a step-by-step 
example shown in the main menu. You can also draw timing diagrams using Python scripts. There are 
examples of Python scripts in the scripts directory. 


The basic procedure for drawing timing diagrams:

    *Add a clock ( Add Menu -> DigitalClock )* 

      When the clock panel is displayed, set the options to the desired values and then hit the add
      button. The clock will be displayed immediately in the timing diagram below the last signal.

    *Add other signals ( Add Menu -> DigitalSignal or DigitalBus )*

      Set the options to the desired values and hit the "Add" button. The signal or bus will be
      displayed below the last signal.


    *Add pulses synchronized to the clock above ( Click in Signal )*
                        

      Enable the "Add Pulse" mode using the AP button in the toolbar. Set the state of the new pulse and then select
      "Rising Edge", "Falling Edge", or "Rising and Falling Edge" to synchronize the new pulse being added to the
      clock above or the sycnhronous clock you specified when adding the signal.  Click in the signal during 
      the clock cycle to add the pulse.  There are toolbar options to automatically increment or decrement bus values so 
      you can click in a signal quickly multiple times to make a counter. 
   
      The pulses that have been added are not connected to the clock signal. So if you change the frequency 
      of the clock signal, the pulses in the signals will not adjust to the new position of the clock 
      edges. When the pulses were added, the clock cycle time was used in order to calculate the time of 
      the edges in the pulses. In order to have the pulse edge times follow any change in frequency of 
      the synchronizing clock, you have to add Delays between clock edges and the signal edges. Delays 
      represent actual hardware delays like combinatorial delays tphl, tplh, and tcomb, as well as 
      synchronous delays like register CLK-to-Q output delays. 
