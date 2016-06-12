

Generating Timing Diagrams from Verilog Simulations
===================================================

Introduction
------------

It's very handy to generate timing diagrams directly from simulations. Once you have a timing diagram version of the simulation, you can then edit the diagram, add text annotations to show signal relationships, and then save it as an PNG, PDF, or PS file. Then just paste the diagram into the document. This is nice for specifications, review presentations, and design notes.

With the new Python scripting feature, you can generate the timing diagrams automatically from Verilog simulations. This application note shows you a way to use Verilog to generate Python scripts that will automatically build timing diagrams.

The Verilog Example
-------------------

The DUT (Device under Test) is a simple model of a 8 bit memory, sram_1024_8.v. The testbench, sram_tb.v, contains the code needed to generate stimulus for the DUT and sram_timing_diagram.v generates the Python script to automatically build a timing diagram which contains all the signals used by the memory model.

Download all the Verilog for this Example

Output Start and Finish Timing Diagram Functions
------------------------------------------------

The first part of the initial block outputs the scripts needed to initialize the timing diagram script. After the simulation reaches the end time, a few more script functions are needed to zoom into the complete timing diagram. These set the timing diagram start and end time and then zoom in. The Python script name is “sram_td_script.py”. This could be changed to a verilog parameter.

.. code-block:: v
   :linenos:

   initial
   begin
      file = $fopen("sram_td_script.py","w");
      $fwrite(file,"from ta_py_lib 'ta.app' import \*\n");
      $fwrite(file,"from ta_py_lib 'ta.logic' import \*\n");
      $fwrite(file,"from ta_py_lib 'ta.commands' import \*\n");
      $fwrite(file,"td = new_timing_diagram('taApp')"\n");
      $fwrite(file,"start_script(td)\n");
      #end_time
      $fwrite(file,"set_end_time(td, %0d)\n",end_time);
      $fwrite(file,"zoom_in_full(td)\n");
      $fwrite(file,"stop_script(td)\n");
      $fclose(file);
   end
 
Add and Monitor Each Signal Functions
-------------------------------------

An always block is needed for every signal. The code below shows what's needed to monitor the address signal, addr[9:0]. The first time an event is detected, the signal is added to the timing diagram. After, an new edge is added to the signal when an event is detected. You can use this as a template for other signals.

.. code-block:: v
   :linenos:

   always @ (addr) 
   begin
      if ($time >= start_time && $time < end_time) 
      begin
         if (addr_first == 0) 
         begin
            $fwrite(file, "addr = add_digital_bus(td, 'addr[9:0]','%h','Hex')\n",addr);
            addr_first = 1;
         end
         else
            $fwrite(file, "add_edge(td, addr,%0d,'%h')\n",$time,addr);
      end
   end


 
The SRAM Timing Diagram Component
---------------------------------

.. code-block:: v
   :linenos:
    
   `timescale 1ns / 1ps
    
   module sram_timing_diagram ( clk, addr,
                                data, cs, we, oe);
    
   input       clk;
   input [9:0] addr;
   input [7:0] data;
   input       cs;
   input       we;
   input       oe;
    
   parameter integer start_time = 0;
   parameter integer end_time   = 500;
    
    
   integer file;
    
   reg clk_first  = 0;
   reg addr_first = 0;
   reg data_first = 0;
   reg cs_first   = 0;
   reg we_first   = 0;
   reg oe_first   = 0;
    
   //initial $monitor("%d %b %h %h %b %b %b",$time,clk,addr,data,cs,we,oe); 
   //initial $display("start_time = %d", start_time);
   //initial $display("end_time = %d", end_time);
    
   initial
   begin
      file = $fopen("sram_td_script.py","w");
      $fwrite(file,"from ta_py_lib.ta.app import \*\n");
      $fwrite(file,"from ta_py_lib.td.logic import \*\n");
      $fwrite(file,"from ta_py_lib.td.commands import \*\n");
      $fwrite(file,"td = new_timing_diagram(taApp)\n");
      $fwrite(file,"start_script(td)\n");
      #end_time
      $fwrite(file,"set_end_time(td, %0d)\n",end_time);
      $fwrite(file,"zoom_in_full(td)\n");
      $fwrite(file,"stop_script(td)\n");
      $fclose(file);
   end
    
   always @ (clk)
   begin
     if ($time >= start_time && $time < end_time)
     begin
       if (clk_first == 0)
       begin
         $fwrite(file, "clk = add_digital_signal(td,'clk','%b')\n",clk);
         clk_first = 1;
       end
       else
         $fwrite(file, "add_edge(clk,%0d,'%b')\n",$time,clk);
     end
   end
    
   always @ (addr)
   begin
     if ($time >= start_time && $time < end_time)
     begin
       if (addr_first == 0)
       begin
         $fwrite(file, "addr = add_digital_bus(td,'addr[9:0]','%h','Hex')\n",addr);
         addr_first = 1;
       end
       else
         $fwrite(file, "add_edge(addr,%0d,'%h')\n",$time,addr);
     end
   end
    
   always @ (data)
   begin
     if ($time >= start_time && $time < end_time)
     begin
       if (data_first == 0)
       begin
         $fwrite(file, "data = add_digital_bus(td,'data[7:0]','%h','Hex')\n",data);
         data_first = 1;
       end
       else
         $fwrite(file, "add_edge(data,%0d,'%h')\n",$time,data);
     end
   end
    
   always @ (cs)
   begin
     if ($time >= start_time && $time < end_time)
     begin
       if (cs_first == 0)
       begin
         $fwrite(file, "cs = add_digital_signal(td,'cs','%b')\n",cs);
         cs_first = 1;
       end
       else
         $fwrite(file, "add_edge(cs,%0d,'%b')\n",$time,cs);
     end
   end
    
   always @ (we)
   begin
     if ($time >= start_time && $time < end_time)
     begin
       if (we_first == 0)
       begin
         $fwrite(file, "we = add_digital_signal(td,'we','%b')\n",we);
         we_first = 1;
       end
       else
         $fwrite(file, "add_edge(we,%0d,'%b')\n",$time,we);
     end
   end
    
   always @ (oe)
   begin
     if ($time >= start_time && $time < end_time)
     begin
       if (oe_first == 0)
       begin
         $fwrite(file, "oe = add_digital_signal(td,'oe','%b')\n",oe);
         oe_first = 1;
       end
       else
         $fwrite(file, "add_edge(oe,%0d.0e-9,'%b')\n",$time,oe);
     end
   end

   endmodule

        
            

