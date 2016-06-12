DigitalSignal API
============================


Adding DigitalSignals
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. function :: addDigitalSignal(String name, String startState)

    Adds a DigitalSignal to this timing diagram. It creates a new instance of a 
    DigitalSignal object.

    Signal height, space above, riseTime, and fallTime are set to default values.

    Returns a DigitalSignal object. ::

        dsig = timDiagram.addDigitalSignal("GNT_N", "H")


.. function :: addDigitalSignal(String name, String startState, double riseTime, double fallTime)

    Adds a DigitalSignal to this timing diagram. It creates a new instance of a 
    DigitalSignal object.

    Signal height and space above are set to default values.

    Returns a DigitalSignal object.  ::

        dsig = timDiagram.addDigitalSignal("GNT_N", "H", 2.0e-9, 2.0e-9)


