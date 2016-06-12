Script Examples 
=================================

.. highlight:: python
   :linenothreshold: 5

 
Drawing a Timing Diagram
^^^^^^^^^^^^^^^^^^^^^^^^^^^  

                                       
The script draw_diagram.py is shown below ::

    # start a new timing diagram
    if taApp.getFileName() != "new.tim":
        taApp.fileNew("TimingDiagram")
    
    # get the reference to the timing diagram
    td = taApp.getTimingDiagram()
    
    # add the signals
    dclock  = td.addDigitalClock("test-clk", 20.0e6, "H")
    dsignal = td.addDigitalSignal("mem_read", "L")
    dbus    = td.addDigitalBus("mem_add[15:0]", "CC00", "Hex")
    
    # add pulses to the signal and bus
    td.addPulse(dsignal, 50.0e-9, 100e-9, "H")
    td.addPulse(dbus, 30.0e-9, 120e-9, "CC05")
    
    # add 2 edges to the signal
    td.addEdge(dsignal, 200.0e-9, "H")
    td.addEdge(dsignal, 250.0e-9, "L")
    
    # add 2 edges to the bus
    td.addEdge(dbus, 180.0e-9, "CCCC")
    td.addEdge(dbus, 270.0e-9, "CD00")


                                                
Creating a D Flip Flop   
^^^^^^^^^^^^^^^^^^^^^^^^^^^

The script dff.py is shown below ::

    # start a new diagram 
    if taApp.getFileName() != "new.tim":
        taApp.fileNew("TimingDiagram")
    
    # get the current timing diagram
    td = taApp.getTimingDiagram()
    
    # add the CLK, D, and Q signals
    clk  = td.addDigitalClock("CLK",20.0e6,"H")
    sigD = td.addDigitalSignal("D","L")
    sigQ = td.addDigitalSignal("Q","L")
    
    # add a pulse and two edges to the D input
    sigD.addPulse(75.0e-9,125.0e-9,"H")
    sigD.addEdge(175.0e-9,"H")
    sigD.addEdge(225.0e-9,"L")
    
    # define and add a UserDelay
    clk2q_min = 2.0e-9
    clk2q_typ = 4.0e-9
    clk2q_max = 6.0e-9
    clk2q_dly = td.addUserDelay("CLK2Q",clk2q_min,clk2q_typ,clk2q_max,"DFF Clock to Q ouput delay");
        
    # get the clock edge list
    # loop on each edge in the list
    #    if its the rising edge
    #        save the edge time
    #        save the D input state
    #        if next state doesn't equal last state and
    #           this new edge time is greater the last edge time
    #           add the new edge
    #           add a delay to the edge
    clk_edge_list = clk.getEdgeList()
    ls = "L"  
    for clk_edge in clk_edge_list:
        if clk_edge.getNextState() == "H":
            et = clk_edge.getPt2()
            ns = sigD.getStateAtTime(et)
            if ((ns != ls) and (et + clk2q_min > sigQ.getLastEdgePt2())):
                sigQ_edge = sigQ.addEdge(et,ns)
                td.addDelay(clk2q_dly,clk_edge,sigQ_edge)
            ls = ns

            


Dumping Signal Values
^^^^^^^^^^^^^^^^^^^^^^^

The script dump_edges.py is shown below ::
                                                          
    import ta_utils
    from org.dmad.ta import DigitalClock
    
    outfile = ta_utils.setOutputFileName("dump_edges.txt")
    td = taApp.getTimingDiagram()
    
    signal_list = td.getSignalList()
    
    clock_signal = None
    for signal in signal_list:
        if isinstance(signal, DigitalClock):
            clock_signal = signal
        else:
            outfile.write("%s " % (signal.getName()))
    
    outfile.write("\n")
    
    for clock_edge in clock_signal.getEdgeList():
        if clock_edge.getNextState() == "H":
            edge_time = clock_edge.getPt2()
            for sig in signal_list:
                if sig != clock_signal:
                    outfile.write("%s " % (sig.getStateAtTime(edge_time)))
            outfile.write("\n")
    
    outfile.close()

                       
                       
Generating VHDL Test Vectors
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

The script vhdl_test_vectors.py is shown below ::

    import ta_utils
    
    from org.dmad.ta import DigitalSignal
    from org.dmad.ta import DigitalBus
    from org.dmad.ta import DigitalClock
                                      
    out_file = ta_utils.setOutputFileName("vhdl_test_vectors.txt")
    td = taApp.getTimingDiagram()
    ts = td.getTimeScale()
    ts_text = ta_utils.getTimeScaleText(ts)
     
    signals = td.getSignalList()
    for sig in signals:
        i = 0
    
        out_file.write("%s <= " % (sig.getName()))
    
        for edge in sig.getEdgeList():
            if isinstance(sig, DigitalSignal) or isinstance(sig, DigitalClock):
                line = "'%s'"  % (edge.getNextState())
                if i != 0:
                    line = "    %s after %s %s" % \
                        (line,
                         ta_utils.round3Places(edge.getPt2() / ts),
                         ts_text)
            elif isinstance(sig, DigitalBus):
                state_format = {
                    "Hex":  "X\"",
                    "Bin":  "\""
                }
    
                sStart = state_format[sig.getStateFormat()]
    
                line = "%s%s\"" % (sStart, edge.getNextState())
                if i != 0:
                    line = "    %s after %s %s" % \
                        (line,
                         ta_utils.round3Places(edge.getPt2() / ts),
                         ts_text)
                        
            if ( i == len(sig.getEdgeList())-1):
                out_file.write("%s;\n\n" % (line))
            else:
                out_file.write("%s,\n" % (line))
    
            i += 1
    out_file.close()


                


