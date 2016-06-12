DigitalBus API
====================

The Constructors
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

    Groups of signals are represented by a DigitalBus. For example, a processor 
    address bus or data bus. The DigitalBus name must be in the format 
    bus_name[MS:LS].  Where MS is the most significant signal position and LS 
    in the least significant signal position.

.. function :: DigitalBus(TimingAnalyzer taApp,String name,double riseTime,double fallTime,String startState,String stateFormat)

    The signal height and space above are all set to the default values.


.. function :: DigitalBus(TimingAnalyzer taApp,String name,String startState,String stateFormat)

    The signal height, space above, rise time, and fall time are all set to 
    the default values.

Adding DigitalBus Signals
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. function :: addDigitalBus(DigitalBus myBus)

    Adds a DigitalBus to this timing diagram. The DigitalBus instance is 
    required as the argument. ::

        timDiagram.addDigitalBus(myBus)

.. function :: addDigitalBus(String name, String startState, String stateFormat)

    Adds a DigitalBus to this timing diagram. It creates a new instance of a 
    DigitalBus object.

    Returns a DigitalBus object. :: 

        dbus = timDiagram.addDigitalBus("ADDR[15:0]","Z","Hex")

Changing DigitalBus Parameters
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

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

