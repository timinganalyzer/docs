DigitalSignal API
============================

The Constructors
^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. function :: DigitalSignal(TimingAnalyzer taApp, String name, double riseTime,double fallTime, String startState)

    The signal height and space above are set to the default values.


.. function :: DigitalSignal(TimingAnalyzer taApp,String name, String startState)


    The signal height, space above, rise time, and fall time are set to the 
    default values.

Adding DigitalSignals
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. function :: addDigitalSignal(String name, String startState)

    Adds a DigitalSignal to this timing diagram. It creates a new instance of a 
    DigitalSignal object.

    Returns a DigitalSignal object that can be used by other routines needed to 
    do timing analysis. The start state of signal can be "H" or "L" or "Z". ::

        dsig = timDiagram.addDigitalSignal("GNT_N","H")

.. function :: addDigitalSignal(DigitalSignal dsig)

    Adds a DigitalSignal to this timing diagram. A DigitalSignal instance is 
    required as the argument. :: 

        timDiagram.addDigitalSignal(mySignal)

