 
Download
========


.. _Beta0.9894: http://www.timing-diagrams.com/TimingAnalyzer_b9894.zip 

Download Version `Beta0.9894`_.

* Added Edge margin color and hash lines 
    * Click between min and max edges (this selects the EdgeMargin)
    * Click on toolbar color button to change color
    * Click on Hash line button to add hash lines. Click again to remove them.
* Fixed synchronous moves 
* Improvement to Undo and Redo functions
* Moved settings files to user_home_dir/.ta 
* Updated documentation  


.. _Beta0.9893: http://www.timing-diagrams.com/TimingAnalyzer_b9893.zip 

Download Version `Beta0.9893`_.

* Fixed dragging or moving multiple Delays that start from the same edge 
* Fixed the last edge not displayed after TimeWarp

.. _Beta0.9891: http://www.timing-diagrams.com/TimingAnalyzer_b9891.zip 

Download Version `Beta0.9891`_.

* StateBar vertical line is displayed between clocks to show isolation
  between clock domains


.. _Beta0.989: http://www.timing-diagrams.com/TimingAnalyzer_b989.zip 

Download Version `Beta0.989`_.

* Fixed StateBar display position in edge


.. _Beta0.988: http://www.timing-diagrams.com/TimingAnalyzer_b988.zip 

Download Version `Beta0.988`_.

* Fixed pulse width label dashed lines not visible in image diagrams
* Fixed the examples .tim files that didn't load  


.. _Beta0.987: http://www.timing-diagrams.com/TimingAnalyzer_b987.zip 

Download Version `Beta0.987`_.

* Improved Asynchronous and Synchronous Add Pulse.
* Should be much easier to use now as it was before all the changes in b0.980 


.. _Beta0.985: http://www.timing-diagrams.com/TimingAnalyzer_b985.zip 

Download Version `Beta0.985`_.

* Fixed VCD last value change on bus wrong at end time 
* Fixed signal state displayed after TimeWarp 

.. _Beta0.984: http://www.timing-diagrams.com/TimingAnalyzer_b984.zip 

Download Version `Beta0.984`_.

* Fixed VCD bus size values not the correct length.
* Fixed VCD analog signal drawing routine to use new time engine.
* Fixed VCD analog example sine_waves.vcd


.. _Beta0.983: http://www.timing-diagrams.com/TimingAnalyzer_b983.zip 

Download Version `Beta0.983`_.

* Fixed VCD file time scale - error shown when label not centered.
* Fixed verilog app note source files.      


.. _Beta0.982: http://www.timing-diagrams.com/TimingAnalyzer_b982.zip 

Download Version `Beta0.982`_.

* Fixed Constraint - error shown when label not centered.


.. _Beta0.981: http://www.timing-diagrams.com/TimingAnalyzer_b981.zip 

Download Version `Beta0.981`_.

* Fixed "Add Edge" problem in b0.980
* Time Scale added to Edit Menu
* Quick Guide added to main web page 


.. _Beta0.980: http://www.timing-diagrams.com/TimingAnalyzer_b980.zip 

Download Version `Beta0.980`_.

* New timing engine with fS accuracy.
* Added jitter margins. 
* Delays can show min or max annotations
* Improved Zoom functions.
* A new app note, **"Intro to Timing Analysis"** 
* Improved python scripting API.  
* Plus many bug fixes and improvements. 


.. _Beta0.971: http://www.timing-diagrams.com/TimingAnalyzer_b971.zip 

Download Version `Beta0.971`_.

* Fix Signal names missing in save images.
* Fix Last directory remembered with saving images
* Fix Delay and Constraint edge positions used. 
* Fix Added Max Constraint back in checks. 
* Changed User Delay to Part Delay
* Changed User Constraint to Part Constraint.
* Added Part Delay GUI panel.    
* Added Part Constraint GUI panel.    

.. _Beta0.970: http://www.timing-diagrams.com/TimingAnalyzer_b970.zip 


Download Version `Beta0.970`_.

* New "Add Pulse" AP mode button in toolbar.  When "Add Pulse" mode is
  enabled, you can add pulses or edges to any signal in the diagram.
  The Buttons for H L Z X B are disabled when "Add Pulse" mode is
  disabled. 
* New "Show Hidden" button in the toolbar.  Use this to show any
  hidden Pulse Width Labels, Constraints, or Delays.  Use the
  pop-up menu to un-hide any selected hidden object.  Use the
  pop-up menu to hide the object. The hidden objects are shown
  with a yellow background.
* Selected objects are shown with dashed line red rectangle around
  the border. Use toolbar buttons to change color, font, and line 
  styles and see the results immediately 
* New font select combobox and button in toolbar. You can easily change 
  the font used for any text selected in the diagram with one click.
* Added Differential Driver.  Given an input signal,  it creates
  differential signals.  Delays from the original input signal can
  be added to model path delays or skew on each signal.
* Added "Sync Clock" to DigitalSignal and DigitalBus.
  When adding pulses to a Signal or Bus,  the clock above the signal
  is used by default if the Synchronous Clock is not specified.
  For example:  How can I model clock tree skew?  
  Add a Differential Driver with a DigitalClock named
  CLK as the input. Specify delays on both outputs CLK+ and CLK- 
  to represent the different path delays and skew. Sounds like a 
  good idea for another application note.
* Updated the Python API.  Updated functions with more consistent 
  argument positions for addDigitalClock, addDigitalBus, and 
  addDigitalSignal.  This will break older scripts but the changes
  are very simple.  I will add a note in the announcement that
  shows how to fix the scripts.

  The following functions are recommended when adding signals to a timing diagram.

  * dclk = timDiagram.addDigitalClock(name, startState, freq)
  * dclk = timDiagram.addDigitalClock(name, startState, freq, dutyCyle)
  * dclk = timDiagram.addDigitalClock(name, startState, freq, dutyCyle, riseTime, fallTime)
  * dsig = timDiagram.addDigitalSignal(name, startState)
  * dsig = timDiagram.addDigitalSignal(name, startState, riseTime, fallTime)
  * dbus = timDiagram.addDigitalBus(name, startState, stateFormat)
  * dbus = timDiagram.addDigitalBus(name, startState, stateFormat, riseTime, fallTime)

  The following functions have been removed.

  * timDiagram.addDigitalClock(dclk)
  * timDiagram.addDigitalSignal(dsig)
  * timDiagram.addDigitalBus(dbus)

* Fixed addTimeWarp script function.   
* Plus other minor fixes and improvements.  

.. _Beta0.963: http://www.timing-diagrams.com/TimingAnalyzer_b963.zip 

Download Version `Beta0.963`_.

* Fixed Edge fall time -- Signals were using one value for rise and
  fall times. 
* Fixed Locale settings to english and US. This should override any
  settings made by the JVM. This Locale is displayed if 
  started from the command line. 
* Added VCD Analog Signals. Try sine_waves.vcd in example dir. 
  VCD files get converted automatically to timing diagrams so 
  this is the start of AnalogSignal for timing diagrams. More 
  capablities will be added in future versions.  Recommendations and
  suggestions welcome from users. Looking for VCD file examples from
  users to help test this feature.
* Started the clean-up of the examples directory.  There where many
  examples from previous versions of the TimingAnalyzer that were not
  working.

      * cnstrnt_err.tim     
      * cram_read.tim    
      * pci_bus_master_mem_read.tim
      * pci_bus_master_mem_write.tim
      * pci_io_read.tim
      * pci_io_write.tim
      * sine_waves.vcd


.. _Beta0.962: http://www.timing-diagrams.com/TimingAnalyzer_b962.zip 

Download Version `Beta0.962`_.

* Fixed VCD file loading
* Fixed Python scripts not executing from GUI


.. _Beta0.961: http://www.timing-diagrams.com/TimingAnalyzer_b961.zip 

Download Version `Beta0.961`_.

* Fixed update UserDelay options
* Added constraint margin time in display when "show constraint time" is selected.   
* Fixed Clock, Signal, and Bus edge values only using pS when adding signals 


.. _Beta0.960: http://www.timing-diagrams.com/TimingAnalyzer_b960.zip 

Download Version `Beta0.960`_.

* PulseWidthLabels, Text Labels, Constraints, and Delays can cross TimeWarps 
* Improved drawing routines allow timing diagram to start at a time other than 0
* Fixes VHDL and Verilog monitors so simulation waveform views can start at a time other than 0
* Add and Edit Pulses and Edges with new toolbar .
* Many other improvements and fixes 

.. _Beta0.957: http://www.timing-diagrams.com/TimingAnalyzer_b957.zip 

Download Version `Beta0.957`_.

* Included images directory in TimingAnalyzer.jar to clean up the install directory
* Fixed bus value select when the bus value did not contain a number.
* Fixed clock edge times displayed that were rounded to ns. Now accurate to +/- 1.0E-15.
* Fixed user delay / constraint panel textfields position on OS X


