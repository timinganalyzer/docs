
Quick Guide
===========

The topics below describe commonly used procedures.  Refer to the reference manual for more detail.


Starting a New Timing Diagram
-------------------------------

Use the File Menu -> New to start a new timing diagram.  Choose the right Time Scale for your requirements. 
Default is nSec when the program first starts. The Time Scale is displayed on the Status Bar on the bottom of the window. 
The accuracy is +- 1/1000 of the Time Scale.  

Setting the Time Scale
-----------------------

================================  ===================
Edit Menu -> Time Scale -> pSec.  Accuracy +- 1fSec
Edit Menu -> Time Scale -> nSec.  Accuracy +- 1pSec
Edit Menu -> Time Scale -> uSec.  Accuracy +- 1nSec
Edit Menu -> Time Scale -> mSec.  Accuracy +- 1uSec
================================  ===================
 

Adding Pulses
--------------

Enable "Add Pulse" mode with the AP button in the Toolbar.
When "Add Pulse" is enabled,  H L Z X B buttons are all enabled so you can edit signals and add new pulses.

Select the state of the new pulse with the H L Z X and B buttons.
Click in the signal at a time within the clock cycle of the closest clock above, the new state will be added in that clock cycle. 

For example: If the signal is high in the diagram, and you want to add low pulses in 3 places,  do the following:

* AP button
* L button
* Click in the signal 3 times.  Low pulses are added for each clock cycle.

The new pulses being added are synchronized to the closest clock above the signal or Sync Clock specified in signal panel GUI.
They can be  be synchronized to rising, falling, or both Edges with the arrow buttons in the toolbar.  

If your adding pulse to a bus,  select the B button and type in the bus value.  If you click in the next clock cycle, the bus value will be incremented or decremented by the value specified in the toolbar next to the Spin button.

 
Hide Show Objects 
---------------------

Enable "Show Hiden Objects" mode with the SH button in the Toolbar.

When "Show Hidden" is enabled, all the hidden objects will be visible in the timing diagram. 
The object background will be yellow.  Use the right mouse button to get the pop-up menu and select "Show Object" if you want to make it visible again.

Note:  Hiding and showing Signals is done from the Edit Menu, Signals, "Hide Show".
This operation will be improved in the future and combined with the SH button functionality.
 

Moving Edges
-------------

Select multiple Edges by holding down the shift key and click on the Edges. 
Select one Edge and then the Edit or pop-up menu, "Select All to Right" or "Select All to Left"

Drag the Edges with the mouse or use the following key combinations.

=================   ========================
Ctrl + Arrow Keys   Time Per Division / 100
Arrow keys          Time Per Division / 10     
Shft + Arrow Keys   Time Per Division
=================   ========================



Move All Synchronously 
------------------------

Drag the mouse to create the copy rectangle. Make sure all the objects to be moved are selected. 
Use Alt and Arrow Keys to move all the selected objects 1/2 clock cycle at a time. 

See Video in "Screenshots and Videos" 

This helps when inserting new pulses between other pulses.  Or new transactions between existing transactions. 
For example: If there was 2 write cycles back to back but you wanted to insert a read cycle between them.

 

Zooming In and Out 
---------------------------

==========  ========================================================  
Zoom Out    Pluse Key +  
Zoom In     Minus Key -  
Zoom Full   Asterick Key *  
Zoom Range  Drag to draw a rectangle so no components are selected.
==========  ======================================================== 


Parts Libs 
-----------

Use the Lib Menu to add Part Delays, Part Constraints, and Part JitterMargins to the library for the timing diagram. These are not added to the timing diagram directly.  The user specifies the min, typ, and max values and the description for Part Delays and Constraints and min and max values and the description for Part JitterMargins.

* Use the Lib Menu -> Part Delay or the Pop-up Menu -> Add to put in library.
* Use the Lib Menu -> Part Constraint or the Pop-up Menu -> Add to put in the library.
* Use the Lib Menu -> Part Jitter or the Pop-up Menu -> Add to put in the library.


Adding Delays 
-------------

A Part Delay must be added to the Parts Library before a Delay can be added to the timing diagram.

* Select 2 Edges. Edge 1 is the source of the Delay and Edge 2 is the destination.
* Use the Add Menu -> Delay or the Pop-up Menu -> Add Used Delay.
 

The following fields need to specified in the Delay Panel.

===============   ===============================================================================================================
The Part Delay    For example: This could be tphl for a combinatorial logic AND gate that was added to the Parts Lib.
Edge 1 Position   The start of the Delay will occur at the time of the position in the Edge.
Edge 2 Position   The end of the Delay will occur at the time of the position in the Edge.
Title Position    The title will be displayed to the left, right, or center of the vertical lines from the Edges.
View Case         Draws the min or max Delay in the diagram.
===============   =============================================================================================================== 

Use the Add button to add the Delay to the diagram. 
Use the Update button to change any of the settings for a Delay already being used.

To edit a used Delay, double click on the Delay in the diagram. The Delay Panel will display with the used Delay values. Change any of the values and use the Update button.


Adding Constraints 
------------------

A Part Constraint must be added to the Parts Library before a Constraint can be added to the timing diagram.

Select 2 Edges. Edge 1 is should occur first in time and Edge 2 second. 
For example: For a hold Constraint, select the CLK signal Edge first and then the data signal Edge.
Use the Add Menu -> Constraint or the Pop-up Menu Add Used Constraint.
 
The following fields need to specified in the Constraint Panel.

===================   ===========================================================================================================
The Part Constraint   For example: This could be Thold for a DFF that was added to the Parts Lib.
Edge 1 Position       The start of the Constraint will occur at the time of the position in the Edge.
Edge 2 Position       The end of the Constraint will occur at the time of the position in the Edge.
Title Position        The title will be displayed to the left, right, or center of the vertical lines from the Edges.
Type                  Edge 1 type - Edge 2 type. For example: A hold Constraint would be Edge 1 Max - Edge 2 Min. Select Max-Min 
===================   =========================================================================================================== 

Use the Add button to add the Constraint to the diagram. 
Use the Update button to change any of the settings for a Constraint already being used.

To edit a used Constraint,  double click on the Contraint in the diagram. The Constraint Panel will display with the used Constraint values. Change any of the values and use the Update button.


Adding JitterMargins 
--------------------

Refer to the App Note "Intro to Timing Analysis" for real examples using Jitter Margins.

JitterMargins must be added to the Parts Library before it can be added to the timing diagram.

* Select one or more Edges that require Jitter Margins
* Select Add Used JitterMargin from the Pop-up menu.
   

