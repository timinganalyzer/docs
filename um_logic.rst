Logic API
====================


.. function :: addBuffer(String dinName,String tphlName,String tplhName)

    * dinName is the name of the buffer input signal. It can be a DigitalSignal, DigitalBus, or DigitalClock.
    * tphl (Optional) is the name of a User Delay which specifies the propagation delay when switching from "H" to "L".  If not specified, use "";
    * tplh (Optional) is the name of a User Delay which specifies the propagation delay when switching from "L" to "H".  If not specified, use "";

    Example 1: A Buffer with no delays. ::

        td.addBuffer("CLK,"","")

    Example 2:  A Buffer with tphl and tplh delays. ::

        td.addUserDelay("tphl",tphlMin,tphlTyp,tphlMax, "tphl prop delay part xyz");
        td.addUserDelay("tplh",tplhMin,tplhTyp,tplhMax, "tplh prop delay part xyz");

        td.addBuffer("CLK","tphl","tplh");


.. function :: addInverter(String dinName,String tphlName,String tplhName)

    * dinName is the name of the Inverter input signal. It can be a DigitalSignal, DigitalBus, or DigitalClock.
    * tphl (Optional) is the name of a User Delay which specifies the propagation delay when switching from "H" to "L".  If not specified, use "";
    * tplh (Optional) is the name of a User Delay which specifies the propagation delay when switching from "L" to "H".  If not specified, use "";

    Example 1: An Inverter with no delays. ::

        td.addInverter("CLK,"","")

    Example 2: An Inverter with tphl and tplh delays. ::

        td.addUserDelay("tphl",tphlMin,tphlTyp,tphlMax, "tphl prop delay part xyz");
        td.addUserDelay("tplh",tplhMin,tplhTyp,tplhMax, "tplh prop delay part xyz");
        
        td.addInverter("CLK","tphl","tplh");

.. function :: addDFF(String dinName,String clkName,boolean posEdge,String clk2qName,String enName,String rstName, String preName)

    * dinName is the name of the D input signal. It can be a DigitalSignal or a DigitalBus.
    * clkName is the name of the CLK input signal. 
    * posEdge is true for rising edge triggered and false for falling edge triggerred.
    * clk2qName (Optional) is the name of a User Delay which specifies the clock to Q output delay.  If not specified, use "".
    * enName    (Optional) is the name of the ENABLE input signal.  If not specified, use "".
    * rstName   (Optional) is the name of the synchronous RESET input signal. If not specified, use "".
    * preName   (Optional) is the name of the synchronous PRESET input signal.  If not specified, use "".

    Example 1: A positive edge triggered DFF with enable and clk2q delay. ::

        td.addUserDelay("clk2q",clk2qmin,clk2qTyp,clk2qMax, "DFF clock to Q delay part xyz");
        td.addDFF("FIFO_RD","CLK",true,"clk2q","FIFO_RD_EN","","");

    Example 2: A positve edge triggered DFF with enable and clk2q delay and synchronous reset. ::

        td.addUserDelay("clk2q",clk2qmin,clk2qTyp,clk2qMax, "DFF clock to Q delay part xyz");
        td.addDFF("FIFO_RD","CLK",true,"clk2q","FIFO_RD_EN","FIFO_RST","");


.. function :: addCounter(String cntrName,String clkName,boolean posEdge,String clk2qName,boolean upCounter,String enName,String ldName,String pinName, String rstName, String preName)

    * cntrName is the name of the counter output signal. A new DigitalBus will be added to the diagram with this name.
    * clkName is the name of the CLK input signal. 
    * posEdge is true for rising edge triggered and false for falling edge triggerred.
    * clk2qName (Optional) is the name of a User Delay which specifies the clock to Q output delay.  If not specified, use "".
    * upCounter is true for an up counter and false for a down counter.
    * enName    (Optional) is the name of the ENABLE input signal.  If not specified, use "".
    * ldName    (Optional) is the name of the counter LOAD signal input.  When active, the value of the parallel input (pinName) is loaded into the counter on the next clock edge. 
    * pinName   (Optional) is the name of the parallel input signal.  This should be used with ldName. IF not specified, use "".
    * rstName   (Optional) is the name of the synchronous RESET input signal. If not specified, use "".
    * preName   (Optional) is the name of the synchronous PRESET input signal.  If not specified, use "".

    Example 1: A 8 bit up counter, positive edge triggered, with clk2q delay, count enable and synchronous reset. :: 

        td.addUserDelay("clk2q",clk2qmin,clk2qTyp,clk2qMax, "Counter clock to Q delay part xyz");
        td.addCounter("FIFO_WR_CNTR[7:0]","CLK",true,"clk2q",true,"FIFO_RD_CNTR_EN","","","RST","");


