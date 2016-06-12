

Generating Timing Diagrams from VHDL Simulations
================================================

It's very handy to generate timing diagrams directly from simulations. Once you have a timing diagram version of the simulation, you can then edit the diagram, add text annotations to show signal relationships, and then save it as an PNG, PDF, or PS file. Then just paste the diagram into the document. This is nice for specifications, review presentations, and design notes.

With the new Python scripting feature, you can generate the timing diagrams automatically from VHDL simulations. This application note shows you a way to use VHDL to generate Python scripts that will automatically build timing diagrams.

The VHDL Example
----------------

The DUT (Device under Test) is a simple model of a 8 bit memory, sram_1024_8.vhd. The testbench, sram_testbench.vhd, contains the code needed to generate stimulus for the DUT and sram_timing_diagram.vhd generates the Python script to automatically build a timing diagram which contains all the signals used by the memory model.

Download all the VHDL for this Example

Initialize the Timing Diagram Functions
---------------------------------------

The first part of the process defines variables and generates the beginning of the timing diagram script. The process monitors the signals in the sensitivity list and adds a new edge to the signal every time an event is detected if the simulation time now is greater than the start_time and less then the end_time defined in the variables section. These will set the timing diagram start and end time. The Python script name is defined by py_output as “sram_td_script.py”. This could easily be changed to a process argument.

.. code-block:: vhdl
   :linenos:

   -- initialize the TimingAnalyzer application if use Jython
   --print(py_output, "execfile('./start_app.py')");
   --print(py_output, "");
   print(py_output, "if 'new.tim' != taApp.getFileName():");
   print(py_output, "    taApp.fileNew('TimingDiagram')");
   print(py_output, "td = taApp.getTimingDiagram()");
   print(py_output, "td.startScript()");
 
Add and Monitor Each Signal Functions
-------------------------------------

A monitor block for every signal is included in the body of the process. The code below shows what's needed to monitor the write address signal, waddr(9 downto 0). When an event is detected, an new edge is added to the signal. You can use this as a template for other signals.

.. code-block:: vhdl
   :linenos:

   if (waddr'event) then
     if (waddr_first = '0') then
       print(py_output, "waddr = td.addDigitalBus(" & "'waddr[9:0]'" & 
                        ",'" & hstr(waddr) & "','Hex')");
       waddr_first <= '1';
     else
       print(py_output, "td.addEdge(" & "waddr" & "," & integer'image(time_now) &
                                    ".0e-9" & ",'" & hstr(waddr) & "')");
     end if;
   end if; 
 
Finalize Timing Diagram Functions
---------------------------------

To complete the timing diagram script, the start time and end time are specified, then we “zoomIn” to show the complete diagram, then the stopScript() function actually draws the diagram.

.. code-block:: vhdl
   :linenos:

   elsif (now > end_time) then 
     if (finish = '0') then
        print(py_output, "td.setStartTime(" & integer'image(scaled_start_time) & ".0e-9)");
        print(py_output, "td.setEndTime(" & integer'image(scaled_end_time) & ".0e-9)");
        print(py_output, "td.zoomIn(" & integer'image(scaled_start_time) & ".0e-9," 
                                      & integer'image(scaled_end_time) & ".0e-9)");
        print(py_output, "td.stopScript()");
        finish <= '1';
     end if;
   end if;


The SRAM Timing Diagram Component
---------------------------------

 
.. code-block:: vhdl
   :linenos:

   library IEEE;
   use IEEE.std_logic_1164.all;
   use STD.textio.all;
   use work.txt_util.all;
    
    
   entity sram_timing_diagram is
     generic (
       start_time  : time := 0 ns;
       end_time    : time := 500 ns);
     port (
       clk50     : in std_logic;
       enable    : in std_logic;
       write     : in std_logic;
       waddr     : in std_logic_vector(9 downto 0);
       din       : in std_logic_vector(7 downto 0);
       read      : in std_logic;
       raddr     : in std_logic_vector(9 downto 0);
       dout      : in std_logic_vector(7 downto 0));
   end sram_timing_diagram;
    
   architecture sram_timing_diagram_rtl of sram_timing_diagram is
    
     signal start  : std_logic := '0';
     signal finish : std_logic := '0';
    
     signal enable_first   : std_logic := '0';
     signal write_first    : std_logic := '0';
     signal waddr_first    : std_logic := '0';
     signal read_first     : std_logic := '0';
     signal raddr_first    : std_logic := '0';
     signal clk50_first    : std_logic := '0';
     signal din_first      : std_logic := '0';
     signal dout_first     : std_logic := '0';
    
   begin
    
     build_timing_diagram : process(enable,write,waddr,read,raddr,clk50,din,dout)
       variable in_line            : line;
       variable out_line           : line;
       variable time_now           : integer;
       variable scaled_start_time  : integer;
       variable scaled_end_time    : integer;
       file py_output      : text open write_mode is "sram_td_script.py";
     begin
       if ( now >= start_time and now <= end_time) then
         if (start = '0') then
    
           -- initialize the TimingAnalyzer application if use Jython
           --print(py_output, "execfile('./start_app.py')");
           --print(py_output, "");
           print(py_output, "if 'new.tim' != taApp.getFileName():");
           print(py_output, "    taApp.fileNew('TimingDiagram')");
           print(py_output, "td = taApp.getTimingDiagram()");
           print(py_output, "td.startScript()");
    
           scaled_start_time   := (start_time / 1 ns);
           scaled_end_time     := (end_time / 1 ns);
           start <= '1';
         else
    
           time_now := ( now / 1 ns);
    
           if (clk50'event) then
             if (clk50_first = '0') then
               print(py_output, "clk50 = td.addDigitalSignal(" & "'clk50'" &  
                                ",'" & str(clk50) & "')");
               clk50_first <= '1';
             else
               print(py_output, "td.addEdge(" & "clk50" & "," & integer'image(time_now) & 
                                            ".0e-9" & ",'" & str(clk50) & "')");
             end if;
           end if; 
    
           if (enable'event) then
             if (enable_first = '0') then
               print(py_output, "enable = td.addDigitalSignal(" & "'enable'" & 
                                ",'" & str(enable) & "')");
               enable_first <= '1';
             else
               print(py_output, "td.addEdge(" & "enable" & "," & integer'image(time_now) &
                                ".0e-9" & ",'" & str(enable) & "')");
             end if;
           end if; 
    
           if (write'event) then
             if (write_first = '0') then
               print(py_output, "write = td.addDigitalSignal(" & "'write'" &  
                                ", '" & str(write) & "')");
               write_first <= '1';
             else
               print(py_output, "td.addEdge(" & "write" & "," & integer'image(time_now) &
                                ".0e-9" & ",'" & str(write) & "')");
             end if;
           end if; 
    
           if (waddr'event) then
             if (waddr_first = '0') then
               print(py_output, "waddr = td.addDigitalBus(" & "'waddr[9:0]'" & 
                                ", '" & hstr(waddr) & "','Hex')");
               waddr_first <= '1';
             else
               print(py_output, "td.addEdge(" & "waddr" & ", " & integer'image(time_now) &
                                ".0e-9" & ",'" & hstr(waddr) & "')");
             end if;
           end if; 
    
           if (din'event) then
             if (din_first = '0') then
               print(py_output, "din = td.addDigitalBus(" & "'din[7:0]'" & 
                                ", '" & hstr(din) & "','Hex')");
               din_first <= '1';
             else
               print(py_output, "td.addEdge(" & "din" & ", " & integer'image(time_now) &
                                ".0e-9" & ",'" & hstr(din) & "')");
             end if;
           end if; 
    
           if (read'event) then
             if (read_first = '0') then
               print(py_output, "read = td.addDigitalSignal(" & "'read'" &  
                                ", '" & str(read) & "')");
               read_first <= '1';
             else
               print(py_output, "td.addEdge(" & "read" & ", " & integer'image(time_now) &
                                ".0e-9" & ",'" & str(read) & "')");
             end if;
           end if; 
    
           if (raddr'event) then
             if (raddr_first = '0') then
               print(py_output, "raddr = td.addDigitalBus(" & "'raddr[9:0]'" &
                                ", '" & hstr(raddr) & "','Hex')");
               raddr_first <= '1';
             else
               print(py_output, "td.addEdge(" & "raddr" & ", " & integer'image(time_now) &
                                ".0e-9" & ",'" & hstr(raddr) & "')");
             end if;
           end if; 
    
           if (dout'event) then
             if (dout_first = '0') then
               print(py_output, "dout = td.addDigitalBus(" & "'dout[7:0]'" &
                                ", '" & hstr(dout) & "','Hex')");
               dout_first <= '1';
             else
               print(py_output, "td.addEdge(" & "dout" & ", " & integer'image(time_now) &
                                ".0e-9" & ",'" & hstr(dout) & "')");
             end if;
           end if; 
    
         end if;
       elsif (now > end_time) then 
         if (finish = '0') then
            print(py_output, "td.setStartTime(" & integer'image(scaled_start_time) &
                                              ".0e-9)");
            print(py_output, "td.setEndTime(" & integer'image(scaled_end_time) &
                                            ".0e-9)");
            print(py_output, "td.zoomIn(" & integer'image(scaled_start_time) & 
                                        ".0e-9, " & integer'image(scaled_end_time) &
                                        ".0e-9)");
            print(py_output, "td.stopScript()");
            finish <= '1';
         end if;
       end if;
     end process;
    
   end sram_timing_diagram_rtl;
