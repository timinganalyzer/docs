Latest News 
===========


9/9/13 Beta version 0.970 is Released.
--------------------------------------

* New “Add Pulse” AP mode button in toolbar. When “Add Pulse” mode is enabled, 
  you can add pulses or edges to any signal in the diagram. The Buttons for 
  H L Z X B are disabled when “Add Pulse” mode is disabled.

* New “Show Hidden” button in the toolbar. Use this to show any hidden Pulse 
  Width Labels, Constraints, or Delays. Use the pop-up menu to un-hide any 
  selected hidden object. Use the pop-up menu to hide the object. 
  The hidden objects are shown with a yellow background.

* Selected objects are shown with dashed line red rectangle around the border. 
  Use toolbar buttons to change color, font, and line styles and see the results immediately

* New font select combobox and button in toolbar. You can easily change the font used 
  for any text selected in the diagram with one click.

* Added Differential Driver. Given an input signal, it creates differential signals. 
  Delays from the original input signal can be added to model path delays or skew on each signal.

* Added “Sync Clock” to DigitalSignal and DigitalBus. When adding pulses to a Signal or Bus, 
  the clock above the signal is used by default if the Synchronous Clock is not specified. 
  For example: How can I model clock tree skew? Add a Differential Driver with a DigitalClock 
  named CLK as the input. Specify delays on both outputs CLK+ and CLK- to represent the different 
  path delays and skew. Sounds like a good idea for another application note.

* Updated the Python API. Updated functions with more consistent argument positions for 
  addDigitalClock, addDigitalBus, and addDigitalSignal. This will break older scripts but the 
  changes are very simple. 

The following functions are recommended when adding signals to a timing diagram.

  * dclk = timDiagram.addDigitalClock(name, startState, freq)
  * dclk = timDiagram.addDigitalClock(name, startState, freq, dutyCyle)
  * dclk = timDiagram.addDigitalClock(name, startState, freq, dutyCyle, riseTime, fallTime)
  * dsig = timDiagram.addDigitalSignal(name, startState)
  * dsig = timDiagram.addDigitalSignal(name, startState, riseTime, fallTime)
  * dbus = timDiagram.addDigitalBus(name, startState, stateFormat)
  * dbus = timDiagram.addDigitalBus(name, startState, stateFormat, riseTime, fallTime)
  * The following functions have been removed.

The following functions have been removed.

  * timDiagram.addDigitalClock(dclk)
  * timDiagram.addDigitalSignal(dsig)
  * timDiagram.addDigitalBus(dbus)

* Fixed addTimeWarp script function.
* Plus other minor fixes and improvements.




5/2/13 Beta Version 0.960 is Released.
--------------------------------------

* PulseWidthLabels, Text Labels, Constraints and Delays can moved across TimeWarps. 
* New Toolbar for quick way to add and edit edges and bus values.
* Improved drawing algorithm with TimeWarps improves diagram load times
  and allows start times greater than 0.
* Diagrams can start at a time greater than 0.  This fixes a problem related to the
  scripts for the VHDL and Verilog monitors that were described in the app notes.
  If you captured signals from time t1 to time t2,  the first edge would be wrong
  if t1 was not 0.  
* Added more error checking for edges that were moved and ended up at a
  time that is less than zero. This can happen when move multiple edges
  at one time.    
* Removed number of edges for each signal in the .tim file.  
* Other fixes and improvements

3/1/13 Beta Version 0.958 Is Coming. 
-------------------------------------

Below is preliminary list of changes so far.  Much more coming.
 
* PulseWidthLabel can moved across TimeWarps. Once verified by users,
  this will be added to Delays and Constraints.
* Added more error checking for edges that were moved and ended up at a
  time that is less than zero. This can happen when move multiple edges
  at one time.    
* Removed number of edges for each signal in the .tim file.  


8/16/11
-------

The script below can be used to generate a differential signal. It will be 
included in the distribution of the next version beta 0.957. Just select 
clocks or signals in the timing diagram and then run the script. It will 
add the differential signals for each selected signal. Save the script 
below as diff_signal.py and put in the scripts directory so it can be 
executed from the program script panel::

 
    import ta_utils
    from org.dmad.ta import DigitalBus
     
    td = taApp.getTimingDiagram()
     
    selected_signal_list = td.getEditSigList()
     
    for selected_signal in selected_signal_list:
        if not isinstance(selected_signal, DigitalBus):
            diff_signal = td.addDigitalSignal(selected_signal.getName() + "_diff",
                                              ta_utils.invert(selected_signal.getStartState()))
            for sig_edge in selected_signal.getEdgeList():
                diff_signal.addEdge(sig_edge.getPt2Min(),ta_utils.invert(sig_edge.getNextState()))

Add the following function to ta_utils.py. It is called in diff_signal.py above::

    def invert(state):
        states = {
            "H": "L",
            "1": "L",
            "L": "H", 
            "0": "H",
            "Z": "Z"
        }
        return states.get(state)

5/12/11
-------

Started a new timing diagram library. A place to hold scripts that generate 
timing diagrams for commonly used interfaces.

5/1/11
-------

Added a FAQ. A place to look for answers to commonly asked questions.

2/5/11
-------

Added new documentation. A scripting reference manual reference manual. 
Both are available in html and pdf. A users guide is coming.

9/29/10
-------

Added move signal up and down buttons on the toolbar.

Jython scripts now use the standard libraries without the need for installing 
jython. The standalone jython.jar archive includes the standard libs, and is 
included in the jlib directory. When executing scripts from the 
File → Scripts menu, the interpreter is started and the os and sys libs are 
imported before executing the selected script file. You can also run scripts 
from the command line shell or dos window using the following commands::

    c:\Apps\TimingAnalyzer_b951> java -jar jlib\jython.jar
    ...
    >>>execfile('start_app.py')
    >>>execfile('./scripts/dump_edges.py')

2/6/10
-------

The newest feature is ability to read VCD files and convert it to a timing 
diagram automatically. I have tested with Xilinx Chipscope and Modelsim 
VCD files. Modelsim VCD files don't seem to contain buses so I added a 
function, “Bus Signals” to make buses from sequentially ordered signals 
like ADIO<31>, ADIO<30>, ADIO<29> … You have to hold the shift key and 
click on each signal to select multiple signals. Better signal group 
selections will be addressed in the next version. Selecting groups of 
signals will only take 2 clicks.

Refer to the documentation for more information

1/24/10
-------

Added “Generate Timing Diagrams from Verilog Simulations” Application Note.
This app note shows how to use Verilog to generate timing diagrams by 
writing text files which are Python scripts that the TimingAnalyzer 
executes to draw the diagram. A separate module in the example, 
sram_timing_diagram.v, includes all the source code use to generate the 
Python script. You can read it and download the example at: 
Generate Timing Diagrams from Verilog Simulations

12/15/09
-------

Updated the “Generate Timing Diagrams from VHDL Simulations” Application 
Note. A separate component, sram_timing_diagram.vhd, is now used to 
generate the timing diagram Python script. Start and end time are 
specified as generic parameters so you can make timing diagrams of any window 
in time from the simulation. This could be used as a template and modified to
generate timing diagrams for any interface. A python script could developed 
that automatically builds this file for given list of signals, anyone interested?

12/1/09
-------

Added app notes that explain how to build timing diagrams directly from VHDL 
or Verilog. Refer to Generate Timing Diagrams from VHDL Simulations and 
Generate Timing Diagrams from Verilog Simulations

