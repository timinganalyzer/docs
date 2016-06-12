Working with VCD Files 
===========================

Its very convenient to take simulation waveform diagrams and convert them 
to a timing diagram. If you create a VCD file while running simulations, 
just open the VCD file as you would a timing diagram file. The program will 
read and parse VCD file and convert it to a timing diagram automatically 
and save it in the same directory the VCD file is in. 

Reading
^^^^^^^^^^^^^^^^

Use File→open from the menu or toolbar button, and select *.vcd in the file 
filter in the dialog. Select the VCD file. The TimingAnalyzer reads the VCD 
file and automatically converts it to a timing diagram that is saved in the 
same directory the VCD file is in. 

Writing
^^^^^^^^^^^^^^^

This option will be added.  Saving diagrams as VCD files 
can be useful for simulation test vectors. 


Bus Signals
^^^^^^^^^^^^^^^^
Some VCD files don't 
seem to contain buses so there a function, “Bus Signals” that can be used 
to make buses from sequentially ordered signals like ADIO<31>, ADIO<30>, ADIO<29> …

If you want to bus signals, select the signals, click the right mouse button 
to bring up the pop-up menu, and select “Bus Signals”. The new bus should 
appear above the most significant signal in the diagram.

Limitations
^^^^^^^^^^^^^^^^^^^

VCD files are commonly very large files when produced from simulators. The 
TimingAnalyzer does not handle large files very well at this time because it 
was original designed to work with small text timing diagram files, so I 
limited the file size to 100,000 lines. This is hardcoded in the VCD parser, 
so the first 100,000 lines of any VCD will be parsed and displayed. It is 
recommended to create smaller sized VCD files from simulations that contain 
just the transactions of interest that you want to convert to a timing diagram.


It is possible to run out of memory on the heap if there are lots of edges in 
the vcd file. If this happens, a java “OutOfMemory” error occurs. you can 
increase the memory limit allocated for the program by running the program 
from the command line as shown below ::

  java -Xmx512m -jar TimingAnalyzer.jar 

-Xmx512m specifies the maximum heap memory the program can use in MBytes, 
in this case 512M Bytes


User Support
^^^^^^^^^^^^^^^^^^^^^


Beta 0.947 is the first release with this feature. If you find a VCD file that 
is not loading properly, please send me a copy and I will do my best to fix asap.

Limitations

   1. VCD $dumpvars is supported but not $dumpports. $dumpports includes port 
      driver data and is used typically used to drive a tester.
   2. The first 100,000 lines of a VCD file are parsed and converted to a 
      timing diagram. All lines after are ignored.
   3. If signal definitions take more than 100,000 lines, the VCD file will 
      cause an “OutOfBounds” Exception. Close the empty tab window.

Testing ( Request for VCD example files )

   1. All VCD files tested use binary notations for signal values changes. Can 
      anyone provide example VCD files that use hex notations for bus signals?
   2. Scopes are added to the signal names to keep hierarchy information. Can 
      anyone provide example VCD files that contain signal names with hierarchy?



