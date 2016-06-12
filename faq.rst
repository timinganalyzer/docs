
Frequently Asked Questions
==========================


Why won't it start?
----------------------

In the settings directory, there is a file called ta_open_files_list. This 
file contains the names of the timing diagram files that were left open when
you last closed the program. If one of the files is missing or it was moved,
this would cause the program to hang when starting. If one of the files is 
saved on a network drive and the network drive is not mapped or not 
responding, this would also cause the program to hang when starting.

How do I start the program from the command line?
-------------------------------------------------

You might want to start the program from the command line if your developing 
python scripts and want to see the debug information that is output to the shell.

Refer to getting_started.

You might also want to start the program from the command line and specify 
more heap memory if your converting larger vcd waveforms diagrams to 
timing diagrams.

Refer to Working with VCD Files

How do I perform a timing analysis?
--------------------------------------

In older versions of the program, you had to select the analysis mode using a
menu. You had a choice of min, typ, max, or margins and you couldn't edit the
timing diagram when margins was selected. Now, it is always in the margins 
mode and you can edit the diagram. You can also move the min and max edges 
in an edge margin or delay with the mouse or arrow keys in combination with 
Crtl, Shft, and Alt keys.

Basic procedure for timing analysis:

* Add delays that represent real part delays specified by the manufacturer.
* Add constraints that represent real part constraints specified by the 
  manufacturer. Constraint errors are shown in orange, otherwise they are 
  gray. A report of the delays and constraints will be coming a new 
  version soon.
* Move the edges that connect to one of the delays in a path with the mouse 
  and see how it affects the constraint.  If there is a constraint error, 
  you can move one of the edges to the left decreasing the delay time. If 
  the constraint error is eliminated (color changed to gray), a faster part 
  with less delay is one way to fix the problem.  If there isn't a constraint
  error and you move one of the edges increasing the delay time and a 
  constraint error occurs, then you might be able to use a slower part with
  more delay and still meet the timing requirements.

What new features are planned
-------------------------------

* generate reports listing actual delays and constraint values
* VCD output from timing diagram for use as simulator test vectors.
* bus enumerations for state machines
* Min/Max VCD diagrams for gate level simulation results
* more timing diagram generator scripts (common bus protocols)
* Define transactions. Copy and paste transactions
* Printing diagrams.

What improvements are planned
---------------------------------

* change to individual User Delay and User Constraint panels.  
* edit TimeWarps.  
* generate timing diagrams directly from SystemVerilog app note
* generate timing diagrams directly from SystemC app note
* multi line text labels
* horizontal dividers to label groups of signals
* statebar grid shows vertical bars on all rising or falling clock edges
* output python script commands instead of command text.
* User guide and intro to timing analysis app note 

What known issues will be addressed
------------------------------------

* larger bus values. You can specifiy bus values greater than 32 bits, but
  any math functions are limited to 32 bit signed numbers.
* arrows don't look right when delays are very small
* same constraint/delay name shown multiple times in gui combobox
* when bus values are separated by a timewarp, you can not edit the value 
  on the left
* lines are not aligned to the edges for 0.0 rise and fall times
* undo “delete signal” does not bring the signal back sometimes
* undo moving objects sometimes don't go back to the original position
* text labels are drawn below the image boundaries when signal heights are 
  increased
* colors in image do not match the signal line and edge colors
* SaveAs adds multiple file extensions to the file name when “All Files”
  filter is selected

I'm having other problems, what should I do?
----------------------------------------------

If your problem is not shown in the list above, send an email that includes
a dump of the command line text logs. 

Start the program from the command line as described in getting started, copy the 
information that is displayed in the shell window, and send to 
timinganalyzer@gmail.com with an explanation of the issue your having.

