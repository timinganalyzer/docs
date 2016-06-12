TimingDiagram API
=================================


The TimingDiagram class controls all functions related to drawing the timing 
diagram. Multiple timing diagrams can be viewed and edited in separate tab 
windows. A command manager implements Undo and Redo functions for most all the 
functions. Some of the functions use multiple commands that are executed 
together as one command from a linked list of commands.

.. function :: addDigitalClock(String name, double frequency, String startState) 

    Adds a DigitalClock to the timing diagram. It creates a new instance of a 
    DigitalClock object using the arguments. This function is undoable and 
    redoable.

    Returns a DigitalClock object that can be used by other routines. The name, 
    frequency, duty cycle, rise time, fall time, start delay, start state, and 
    height can be changed using updateDigitalClock() ::

        dclk = td.addDigitalClock("CLK25",25e6,"H")


.. function :: addDigitalClock(String name, double frequency, String startState, int dutyCycle)

    Adds a DigitalClock to the timing diagram. It creates a new instance of a 
    DigitalClock object using the arguments. This function is undoable and 
    redoable.

    Returns a Digital Clock object that can be used by other routines. The 
    name, frequency, duty cycle, rise time, fall time, start delay, start 
    state, and height can be changed using updateDigitalClock() ::

        dclk = td.addDigitalClock("CLK25",25e6,"H",40)


.. function :: addDigitalBus(String name, String startState, String stateFormat)

    Adds a DigitalBus to the timing diagram. It creates a new instance of a 
    DigitalBus object using the arguments. This function is undoable and 
    redoable.

    Returns a DigitalBus object that can be used by other routines needed to 
    do timing analysis. The parameters can be changed using updateDigitalClock. 
    The stateFormat can be "Hex", "Bin", "Dec", or "Text" ::

        dbus = td.addDigitalBus("ADDR[15:0]","Z","Hex")

.. function :: addDigitalSignal(String name, String startState)

    Adds a DigitalSignal to this timing diagram. It creates a new instance of a 
    DigitalSignal object using the arguments. This function is undoable and redoable.

    Returns a DigitalSignalobject that can be used by other routines.  The 
    parameters can be changed using updateDigitalSignal(). The start state of 
    signal can be "H" or "L" or "Z" ::

        dsig = td.addDigitalSignal("GNT_N","H")

.. function :: addEdge(Signal sig, double edgeTime, String newState)

    Adds an Edge to a Signal. The edge is added to the signal at the specified 
    time.  The edge object contains the time and new state of the edge. Adding 
    edges should only be used when the new edge will be last edge in the signal. 
    Use addPulse() to change the state of a signal otherwise. This function is 
    undoable and redoable.
 
    Returns the Edge object ::

        thisEdge = td.addEdge(myBus,340.0e-9,"FF22")

.. function :: addPulse(Signal sig, double time1, double time2, String newState)

    Adds a Pulse to a Signal. The pulse occurs from time1 to time2. The 
    newState argument defines the state of the pulse. This actually adds 2 
    edges to the signal.  This function is undoable and redoable ::

        td.addPulse(mySignal,50.0e-9,100.0e-9,"H")

.. function :: addPulseWidthLabel(Edge e1, Edge e2, String label, String labelPos)

   Adds a PulseWidthLabel between two edges. The label is can be displayed on the left,
   right, or center of the edges. ::
   
       td.addPulseWidthLabel(edge1,edge2,"t_min","Center")  

.. function :: addStateBar(Edge ed, String label, String lineType, int offsetX, int offsetY)

   Adds a StateBar to an Edge. The label is displayed to the right of the 
   line on top of the waveform.  The label can be moved by specifying an 
   offset in pixels in the X and Y directions. The line type string can be 
   "Dashed" or "Solid". 

   Ths function is undoable and redoable.  :: 

        td.addStateBar(clk_edge,"","Dashed",0,0)

.. function :: addTextAboveSignal(String sigName, String text, double time, int offset)

    Adds a text label to the timing diagram above a signal. The following example adds
    the label "Write Transaction" 20 pixels above the top of the write_cmd signal 
    at 50 ns ::

        td.addTextAboveSignal("write_cmd", "Write Transaction", 50.0e-9, 20)

.. function :: addTextBelowSignal(String sigName, String text, double time, int offset)

    Adds a text label to the timing diagram below a signal. The following example adds
    the label "Write Transaction" 20 pixels below the bottom of the write_cmd signal 
    at 50 ns ::

        td.addTextBelowSignal("write_cmd", "Write Transaction", 50.0e-9, 20)

.. function :: addTimeWarp(double startTime, double endTime)

   Adds a TimeWarp that begins at the startTime and ends at the endTime. startTime should
   be less than endTime. ::

        td.addTimeWarp(50.0e-9,800.0e-9)


.. function :: addUserDelay(String delayName, Edge ed1, Edge ed2, double min, double typ, double max)

    Add a User Defined Delay. The Delay is added to the second edge.  Minimum, 
    Typical and Maximum delay times are required as arguments and are used 
    when a timing analysis is executed. The time of the second edge time is 
    the first edge time plus the delay. This function is undoable and redoable 
    and is the same as adding a Delay from the GUI. All other Delay parameters 
    are set to the default values.

    Returns the Delay object ::

        tpDelay = td.addUserDelay("tpd",edge1,edge2,4.0e-9,8.0e-9,12.0e-9)

.. function :: addUserConstraint(String myConstraint,Edge e1,Edge e2,double min, double typ, double max)

    Add a User Defined Constraint. The Constraint is added to the second edge.  
    Minimum, Typical and Maximum constraint times are required as arguments 
    and are used when a timing analysis is executed. This function is undoable 
    and redoable and is the same as adding a Constraint from the GUI. All other 
    Constraint parameters are set to the default values.

    Returns the new Constraint ::

        myConstraint = td.addUserConstraint("tsetup",edge1,edge2,12.0e-9,12.0e-9,12.0e-9)

.. function :: getTimeScale()

    Returns the time scale of the timing diagram. 
    Valid values are  1.-e-3 1.0e-6 1.0.e-9 1.0e-12 ::

        tScale = td.getTimeScale()

.. function :: getSignalList()

    Returns an ArrayList which contains all the signals in the current timing 
    diagram ::

        sigList = td.getSignalList()

.. function :: setEndTime(double ts)

    Sets the end time of the timing diagram. ::

        td.setEndTime(300.0e-9)

.. function :: setStartTime(double st)

    Sets the start time of the timing diagram. ::

        td.setStartTime(20.0e-9)

.. function :: setTimePerDivision(double tpd) 

    Sets the time for each large division.  tpd should not include the timeScale ::

        td.setTimePerDivision(20.0)

.. function ::  setTimeScale(double ts) 

    Sets the time scale for the timing diagram. 
    Valid values are 1.0e-3, 1.0e-6, 1.0e-9. and 1.0e-12 ::

       td.setTimeScale(1.0e-9)

.. function :: zoomIn(double startTime, double endTime)

    This zooms in to a window in time in the timing diagram. ::

        td.zoomIn(300.0e-9, 800.0e-9)

.. function :: zoomIn()      

    This divides the time per division by 2.0. ::

        td.zoomIn()

.. function :: zoomOut()      

    This multiplies the time per division by 2.0. ::

        td.zoomOut()

