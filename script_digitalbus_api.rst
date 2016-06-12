DigitalBus API
====================

    Groups of signals are represented by a DigitalBus. For example, a processor 
    address bus or data bus. The DigitalBus name must be in the format 
    bus_name[MS:LS].  Where MS is the most significant signal position and LS 
    in the least significant signal position. Valid state formats are
    "Hex","Bin","Dec", or "Text". 

Adding DigitalBus Signals
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^


.. function :: addDigitalBus(String name, String startState, String stateFormat)

    Adds a DigitalBus to this timing diagram. It creates a new instance of a 
    DigitalBus object.

    Signal height, space above, riseTime, and fallTime are set to default values.

    Returns a DigitalBus object. :: 

        dbus = timDiagram.addDigitalBus("ADDR[15:0]","Z","Hex")

.. function :: addDigitalBus(String name, String startState, String stateFormat, 
                             double riseTime, double fallTime)

    Adds a DigitalBus to this timing diagram. It creates a new instance of a 
    DigitalBus object.

    Signal height and space above are set to default values.

    Returns a DigitalBus object. :: 

        dbus = timDiagram.addDigitalBus("ADDR[15:0]", "Z", "Hex", 2.0e-9, 2.0e-9)



Getters and Setters 
^^^^^^^^^^^^^^^^^^^^

.. function :: getBusName(String name)

    This returns a String that is the name part of name[MS:LS]. The example 
    below returns "ADDR". ::

        busName = dbus.getBusName("ADDR[15:0]")


.. function :: getBusNameX(String name)

    Returns and integer that is the DigitalBus MS signal index. The example 
    below returns 15. ::

        msIndex = dbus.getBusNameX("ADDR[15:0]")


.. function :: getBusNameY(String name)

    Returns an integer that is the DigitalBus LS signal index. The example 
    below returns 0. ::

        lsIndex = dbus.getBusNameY("ADDR[15:0]")


.. function :: getStateFormat()

    Returns a String that is the DigitalBus State Format. It could be 
    "Hex","Bin","Dec", or "Text". ::

        stateFormat = dbus.getStateFormat()

.. function :: setStateFormat(String stateFormat)

    Set the DigitalBus State Format. This sets the current state format to a 
    new value and changes all the bus values to the new state format. ::

        dbus.setStateFormat("Hex")

.. function :: getNumBits()

    Returns an integer that is the number of signals in the DigitalBus. ::

        numSignals = dbus.getNumBits()

