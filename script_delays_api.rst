Delay API
================


.. function :: addUserDelay(String delayName,Edge ed1,Edge ed2,double min,double typ,double max,String note)

    Add a User Defined Delay to the diagram database. The user delay stores the 
    minimum, typical and maximum delay times and a text string label.  

    Returns the UserDelay object. ::

        clk2q_udly = td.addUserDelay("CLK2Q",clk2q_min,clk2q_typ,clk2q_max,"DFF Clock to Q ouput delay")

.. function :: addDelay(UserDelay usrDly,Edge srcEdge,Edge destEdge)

    Adds a Delay to the timing diagram. Requires a UserDelay and 2 Edges as 
    arguments.  
    
    Returns the Delay object. ::

        clk2q_dly = td.addDelay(clk2q_udly,clk_edge,sigQ_edge)


