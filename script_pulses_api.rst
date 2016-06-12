Pulses API
==============

.. function :: addPulse(Signal sig,double time1, double time2, String newState)

    Adds a Pulse to the Signal. The pulse is added to the signal from time1 to 
    time2.  The newState argument defines the state of the pulse. This actually 
    adds 2 edges to the signal. ::  

        timDiagram.addPulse(read,50.0e-9,100.0e-9,"H")
