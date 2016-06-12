Working with Pulses
========================


Adding 
^^^^^^^^^^^^^^^^^^^^^^

Enable the "Add Pulse" mode using the AP button in toolbar. 
Set the new state using the buttons, H L Z X ,  or 
you can set the bus value if the B button is selected. If the 
“Auto Increment” equals 1 or more , the signal value is automatically incremented 
every time you add a pulse. Just click in the signal during a clock cycle to add 
the pulse. Add pulses quickly by clicking in the signal during the next clock 
cycle for each new pulse.

Click in the signal between the clock edges and the pulse appears. Keep clicking 
to add new pulses or extend a pulse value. If the synchronous clock is not set for the
signal being edited, the clock above will be used. If there is no clock above and
the synchronous clock was not set,  then the pulses will be added using the large
divisions of the time ruler.  You can select “Rising Edge”, “Falling Edge”, or 
“Rising and Falling Edge” synchronous. 


Time Offset
^^^^^^^^^^^^^^^^^^

The pulse offset entry in the pulse panel is used to specify an offset in time. 
When adding pulses, edges are added at the time of the clock edge plus the offset. 

For example: If the clock edges occur at 25ns and 50ns and the offset is 2 ns, 
the pulse will be added with edges at 27ns and 52ns.

Moving 
^^^^^^^^^^^^^^^^^

Select the pulse by selecting both edges. Use the left or right arrow keys with 
Ctrl and Shft key combination to move the pulse. The distance its move depends
on the time per division settings as shown below. ::

  Shft - Left/Right   - time per division         - 100ns
  Left/Right          - time per division / 10    - 10ns
  Ctrl - Left/Right   - time per division / 100   - 1ns

You can also just drag the mouse to move the pulse.


Moving Synchronously
^^^^^^^^^^^^^^^^^^^^^^^

* Select the pulse by dragging the mouse so the pulse is contained in the select 
  rectangle.
* Hold down the Alt key and use the left or right arrow keys to move the pulse 
  synchronously with respect to a clock. The clock must be above the signal 
  that has the pulse being moved.



