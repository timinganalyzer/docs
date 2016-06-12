Working with Edges 
=======================

The Edge Defined
^^^^^^^^^^^^^^^^^^^^^^^^^

An edge occurs when there is the transition from one state to another state. In 
the program, three points in time are saved for each edge. Point 1 is 
the very beginning of the edge transition or the 0% point. Point 2 is commonly 
set to the mid point of the edge transition or the 50% point but this point can
be changed when specifying Delays and Constraints. Sometimes its necessary to 
make calculations from the 10% or 90% positions in the edge transition. This value 
can be set by the user to any value between 5% and 95%. Point 3 is the very end of 
the edge transition.

Selecting and Deselecting
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
 select

  1. Click in an edge to select. 
  2. Hold down the Shft key and click in other edges to select multiple edges. 

 deselect

  1. Click in an empty area of the timing diagram to deselect all objects.
  2. Hit the esc key to deselect all objects.
  3. Hold down the Shft key and click in the selected edges.

 select all edges to the right

  1. Select the first edge.
  2. Edit Menu -> Edge -> Select All to Right or pop-up menu -> Select All Edges to Right
 
 select all edges to the left

  1. Select the first edge.
  2. Edit Menu -> Edge -> Select All to Left or pop-up menu -> Select All Edges to Left


Margins
^^^^^^^^^^^^^^^^^^^^^^

Margins shows the uncertainty in time it could take to change states. The area
between the min and max edge is filled in gray by default.  

Adding

  1. Select the Edge.
  2. Click right mouse button to bring up pop-up menu -> Select Add Margin 

Color

  1. Select the Edge Margin. Click between the min and max edge
  2. Click the color button in the toolbar.

Hash Lines

  1. Select the Edge Margin. Click between the min and max edge. 
  2. Click the Hash button in the toolbar.


Moving 
^^^^^^^^^^^^^^^^^^^^^^

Use the left and right arrows keys at the same time with Ctrl and Shft key to 
precisely position the edge. If multiple edges are selected, they will all move 
together keeping the timing relationships. ::

  Shft - Left/Right   - time per division         - 100ns
  Left/Right          - time per division / 10    - 10ns
  Ctrl - Left/Right   - time per division / 100   - 1ns

You can also move the edges by dragging the mouse. 


Aligning 
^^^^^^^^^^^^^^^^^^^^

You can use “Align Edge” from the “Edit Menu” to align edges in different signals. 
“Align Left” aligns all the selected edges to the edge that occurs first in time. 
“Align Right” aligns all the selected edges to the edge that occurs last in time. 
“Align First” aligns all the selected edges to the first edge selected.

* Select one Edge in each signal. Do not select multiple Edges in one signal.
* From popup-menu or Edit → Edge menu, select the alignment operation.

Deleting 
^^^^^^^^^^^^^^^^^^^^^

* Select the edge. Use “delete” key to remove the edge. If the edge is not the last 
  edge in the signal, the following edge will be removed as well. This is same as deleting 
  a pulse.
* Select multiple edges and then use the “delete” key to remove them all at one time.



