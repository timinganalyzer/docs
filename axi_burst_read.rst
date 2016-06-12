
AXI Burst Read 
===============

Save the following script as axi_burst_read.py ::

    from ta_py_lib.ta.app import *
    from ta_py_lib.td.logic import *
    from ta_py_lib.td.commands import *
     
    td = new_timing_diagram(taApp)
    start_script(td)
    
    aclk    = add_digital_clock(td, "ACLK", "H", 100.0e6)
    set_rise_time(aclk, 0)
    set_fall_time(aclk, 0)
    
    araddr  = add_digital_bus(td, "ARADDR[39:0]", "X", "Hex")
    arvalid = add_digital_signal(td, "ARVALID", "L")
    arready = add_digital_signal(td, "ARREADY", "X") 
    rdata   = add_digital_bus(td, "RDATA[31:0]", "X", "Text")
    rlast   = add_digital_signal(td, "RLAST", "L") 
    rvalid  = add_digital_signal(td, "RVALID", "L") 
    rready  = add_digital_signal(td, "RREADY", "L") 
    
    add_edge(araddr, 103.0, "A")
    add_edge(araddr, 123.0, "X")
    
    add_edge_margin(arvalid, 102.0, 103.0, "H")
    add_edge_margin(arvalid, 122.0, 123.0, "L")
    
    add_edge(arready, 103.0, "L")
    add_edge_margin(arready, 112.0, 113.0, "H")
    add_edge(arready, 123.0, "X")
    
    add_edge(rdata, 154.0, "D(A0)")
    add_edge(rdata, 162.0, "X")
    add_edge(rdata, 184.0, "D(A1)")
    add_edge(rdata, 192.0, "X")
    add_edge(rdata, 194.0, "D(A2)")
    add_edge(rdata, 202.0, "X")
    add_edge(rdata, 224.0, "D(A3)")
    add_edge(rdata, 232.0, "X")
    
    add_edge_margin(rlast, 223.0, 224.0, "H")
    add_edge_margin(rlast, 231.0, 232.0, "L")
    
    add_edge_margin(rvalid, 153.0, 154.0, "H")
    add_edge_margin(rvalid, 161.0, 162.0, "L")
    add_edge_margin(rvalid, 183.0, 184.0, "H")
    add_edge_margin(rvalid, 191.0, 192.0, "L")
    add_edge_margin(rvalid, 193.0, 194.0, "H")
    add_edge_margin(rvalid, 201.0, 202.0, "L")
    add_edge_margin(rvalid, 223.0, 224.0, "H")
    add_edge_margin(rvalid, 231.0, 232.0, "L")
    
    
    add_edge_margin(rready, 133.0, 134.0, "H")
    add_edge_margin(rready, 161.0, 162.0, "L")
    add_edge_margin(rready, 173.0, 174.0, "H")
    add_edge_margin(rready, 191.0, 192.0, "L")
    add_edge_margin(rready, 193.0, 194.0, "H")
    add_edge_margin(rready, 211.0, 212.0, "L")
    add_edge_margin(rready, 223.0, 224.0, "H")
    add_edge_margin(rready, 231.0, 232.0, "L")
    
    set_end_time(td, 300)
    stop_script(td)


.. image:: images/axi_burst_read.png
   :height: 280 pt
   :width: 640 pt
