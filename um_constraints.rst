Working with Constraints
=============================================

About Part Constraints
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Part Constraints are specified in the "Part Constraint" and represent actual part 
constraints specified by the manufacturer. A "Part Constraint" needs to specified before 
adding a Constraint to the diagram.   


Adding New Constraints 
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

1. Select 2 edges.  The first edge selected should occur in time before the second.
2. Add Menu -> Constraint or Ctrl 8 or pop-up menu -> Add Constraint
3. Enter the Constraint parameters in the Constraint panel and hit the Add button. 
  

Time Calculations
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Constraints are used to specified parameters like setup and hold times and pulse width min 
and max times. When specifying a constraint, the constraint type determines how 
the slack time calculations are made. 

* Max-Min – measured from source edge max time to the destination edge min time.
* Max-Max – measured from source edge max time to the destination edge max time.
* Min-Max – measured from source edge min time to the destination edge max time.
* Min-Min – measured from source edge min time to the destination edge min time.



Adding Previously Used Constraints
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

1. Select 2 edges.  The first edge selected should occur in time before the second.
2. Pop-up menu, select "Add Used Constraint"

Selecting and Deselecting 
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

 select

   1. Click on the Constraint name or drag mouse to form rectangle around the Constraint 
   2. Hold down the Shft key and click on the Constraint names


 deselect
 
   1. Deselect all.  Esc key or click in empty area
   2. Hold down the Shft key and click on the Constraint names

Moving 
^^^^^^^^^^^^^^^^^^^^^^^

1. Select the constraints.
2. Use Alt and left key to move the Constraints back one half clock cycle
3. Use Alt and right key to move the Constraints forward one half clock cycle.


Moving the Text Labels
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

 horizontally

   1. Select the Constraint.
   2. Use left or right key to move the label to the left, right, or center
      position.

 vertically

   1. Select the Constraint.
   2. Use up and down keys to move the label. Use the Shft or Alt key with
      the up and down key to precisely position the text. You can select
      multiple constraints and move all the labels at the same time.


Deleting 
^^^^^^^^^


1. Select the Constraints.
2. Use the delete key.
 
 
