Constraint API
================

.. function :: add_part_constraint(TimingDiagram td, String name, double min, double typ, double max, String note)

    Add a PartConstraint. Minimum, Typical and Maximum constraint times are 
    required as arguments and are used when a timing analysis is executed. 

    Returns a new PartConstraint. ::

        setup_pcnstrnt = add_part_constraint(td, "tsetup", 12.0e-9, 12.0e-9, 12.0e-9, "min pulsewidth")

.. function :: addConstraint(UserConstraint usrCnstrnt,Edge srcEdge,Edge destEdge)

    Adds a Constraint to the timing diagram. Requires a UserConstraint and 2 Edges as 
    arguments.  
    
    Returns the Constraint object. ::

        setup_cnstrnt = td.addConstraint(setup_ucnstrnt,clk_edge,sigQ_edge)
        

