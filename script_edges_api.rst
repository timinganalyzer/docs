Edges API
===================

   Three points are save for both the minimum and maxium edges: Pt1, Pt2, and Pt3.  
   Pt1 stores the start time of the edge transition, Pt2 stores the time at the
   specified position of the edge transition, and Pt3 stores the end time of the edge transition.
   The user can specify the position of any edge.   
   
    .. image:: images/edge_min_max.png
       :align: center

   Each edge knows the last edge state. Therefore, the next state of the current edge is also the last
   state of the next edge.   


Adding Edges
^^^^^^^^^^^^ 


.. function :: addEdge(Signal sig,double edgeTime, String newState)

    Adds an Edge to a Signal. The edge is added to the signal at the specified 
    time.  The edge object contains the time and new state of the edge.  
    Adding edges should only be used when the new edge will be last edge in 
    the signal. You can use addPulse() to change the state of a signal at any 
    time. 

    Returns the Edge object. ::

        thisEdge = timDiagram.addEdge(pci_data,340.0e-9,"FF22")


.. function :: addEdge(Signal sig,double minTime, double maxTime, String newState)

    Adds an Edge to a Signal with showing min and max times. The Edge is 
    added to the list of edges for the signal and then sorted by edge times. 

    Returns the Edge object. ::

        thisEdge = timDiagram.addEdge(pci_data,340.0e-9,342e-9,"FF22")


Getters and Setters 
^^^^^^^^^^^^^^^^^^^


.. function :: getPt1Min()

    Returns the time of minimum Edge start point 1. ::

        edgeTime = edge1.getPt1Min()

.. function :: getPt1Max()

    Returns the time of maximum Edge start point 1. ::

        edgeTime = edge1.getPt1Max()



.. function :: getPt2Min()

    Returns the time of minimum Edge mid point 2. ::

        edgeTime = edge1.getPt2Min()

.. function :: setPt2Min(double pt2Min)

    This function sets a new time for the minimum edge point 2 and then
    calculates the minimum edge points 1 and 3. It then adjusts any affected
    delays, constraints, and pulse width labels.  Use this function when 
    changing the time of the minimum edge.
 
    Sets the time of minimum Edge mid point 2. ::

        edge1.setPt2Min(25.0e-9)



.. function :: getPt2Max()

    Returns the time of maximum Edge mid point 2. ::

        edgeTime = edge1.getPt2Max()


.. function :: setPt2Max(double pt2Max)

    This function sets a new time for the maximum edge point 2 and then
    calculates the maximum edge points 1 and 3. It then adjusts any affected
    delays, constraints, and pulse width labels.  Use this function when 
    changing the time of the maximum edge.
 
    Sets the time of maximum Edge mid point 2. ::

        edge1.setPt2Min(25.0e-9)



.. function :: getPt3Min()

    Returns the time of minimum Edge end point 3. ::

        edgeTime = edge1.getPt3Min()

.. function :: getPt3Max()

    Returns the time of maximum Edge end point 3. ::

        edgeTime = edge1.getPt3Max()



.. function :: getPos()

    This returns the % positon of the edge point 2. Legals values
    are from 5 to 95 and most commonly are increments of 5.

    Returns the position of Edge point 2. ::

        edgePosition = edge1.getPos()


.. function :: setPos(int pos)

    This sets the % positon of the edge point 2. Legals values
    are from 5 to 95 and most commonly are in increments of 5.

    Sets the position of Edge point 2. ::

        edge1.setPos(40)




.. function :: getPt1State()

    Returns the Edge last state. ::

        lastState = edge1.getPt1State()


.. function :: getLastState()

    This is the same as getPt1State() above and is the 
    recommended  method to use.

    Returns the edge last state. ::

        lastState = edge1.getLastState()


.. function :: getPt3State()

    Returns the Edge next state. ::

        nextState = edge1.getPt3State()


.. function :: getNextState()

    This is the same as getPt3State() above and is the 
    recommended  method to use.

    Returns the edge next state. ::

        nextState = edge1.getNextState()

