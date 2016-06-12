Signal API
=============


The Signal is the base class for the DigitalClock, DigitalSignal, and DigitalBus.  
Any one of these classes can use the methods described below.


Getters and Setters 
^^^^^^^^^^^^^^^^^^^^^^


.. function :: getEdgeList()

    Returns the list of edges for the signal. ::

        edgeList = pciAddrBus.getEdgeList()


.. function :: getStateAtTime(double time)

    Returns a String that is the state of the signal at the time 
    specified in the argument. ::

        currentState = pciAddrBus.getStateAtTime(45.0e-9)


.. function :: setName(String sigName)

    Sets the name of the signal ::

        mySig.setName("R/W")

.. function :: getName()

    Returns a String that is the name of the signal. ::

        busName = pciAddrBus.getName()


        
.. function :: setHeight(int sigHeight)

    Sets the height, in pixels,  of the signal. :: 

        myBus.setHeight(30)

.. function :: getHeight()

    Returns an int that is the height of the signal in pixels. ::

        pciAddrBusHeight = pciAddrBus.getHeight()


.. function :: setFallTime(double fallTime)

    Sets the fall time of every edge in the signal. ::

        myClock.setFallTime(4.0e-9)

.. function :: getFallTime()

    Returns a double that is the fall time of the edges in the signal. ::

        fallTime = readSig.getFallTime()


.. function :: setRiseTime(double riseTime)

    Sets the rise time of every edge in the signal. ::

        myClock.setRiseTime(4.0e-9)

.. function :: getRiseTime()

    Returns a double that is the rise time of the edges in the signal. ::

        riseTime = writeSig.getRiseTime()



.. function :: setStartState(String startState) 

    Sets the start state of the signal. ::

        myClock.setStartState("L")

.. function :: getStartState()

    Returns a String that is the start state of the signal. ::

        startState = mySig.getStartState()



.. function :: setSpaceAbove(int spaceAbove)

    Sets the blank space, in pixels, above the signal. ::

        pciClock.setSpaceAbove(50)

.. function :: getSpaceAbove() 

    Returns an int that is the space above the signal in pixels. ::

         spaceAbove = sig.getSpaceAbove()



