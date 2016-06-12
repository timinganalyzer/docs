Python Utilities
================

There is a file called ta_utils.py in the scripts directory. 
It contains many commonly used methods that simplify script
development.   Some of provided examples make use of these
funcions as described below.


.. function :: setOutputFileName(file_name)

    Use file.write() and file.writelines() to write to the 
    output file in your script. The file will be output to 
    the scripts directory.

    Returns the pointer to the file. ::

        outfile = ta_utils.setOutputFileName("dump_edges.txt")
        outfile.write("%s " % (signal.getName()))
        outfile.close()


.. function :: getTimeScaleText(time_scale)

    This function is used to get the text version of the 
    time scale value. The input can be
    1.0e-3, 1.0e-6, 1.0e-9, or 1.0e-12. 
    
    Returns a string for text time scale value input. The values
    returned can be "ms", "us", "ns", or "ps".  ::

        ts_text = ta_utils.getTimeScaleText(ts)


.. function :: get_ts_text(time_scale)

    This function is used to get the numeric string version of the 
    time scale value. The input can be
    1.0e-3, 1.0e-6, 1.0e-9, or 1.0e-12. 
    
    Returns a string for text time scale value input. The values
    returned can be "e-3", "e-6", "e-9", or "e-12".  ::

        ts_text = ta_utils.get_ts_text(ts)



.. function :: invert(state)

    This function is used to invert a binary value. 
    The input can be "H", "1", "L", "0", or "Z"
    
    Returns a string for the inverted value. The values
    returned will be respectively "L", "L", "H", "H", or "Z". ::

        new_state = ta_utils.invert(signal.getStartState())

.. function :: get_voltage(state)

    This function is used to convert a binary value to a voltage. The
    voltage value returne is for 5 volt logic.  The input can be 
    "H", "1", "L", "0", or "Z"
    
    Returns a double for the voltage value. The values
    returned will be respectively 5.0, 5.0, 0.0, 0.0, or 2.5. ::

        new_voltage = ta_utils.get_voltage(signal.getStartState())


.. function :: get_end_time(timing_diagram)

    This function returns the end time of the specified timing diagram. 

    Returns a double for the end time value. ::

        td_end_time = ta_utils.get_end_time(td)

.. function :: get_ls_bit(bus_name)

    This function is used to get the lsb of the bus name.  In the 
    example below, this function would return 0. 

    Returns the least significant bit of the bus. ::

        ls_bit = ta_utils.get_ls_bit("addr[15:0]")


.. function :: get_ms_bit(bus_name)

    This function is used to get the msb of the bus name.  In the 
    example below, this function would return 15. 

    Returns the most significant bit of the bus. ::

        ls_bit = ta_utils.get_ms_bit("addr[15:0]")


.. function :: hex2bin(hex_value)

    This function converts a hexidecimal number into binary integer. 

    Returns the binary value equal to the hex input. ::

        binary_bus_value = ta_utils.hex2bin(FFAC)


.. function :: convert_format(state, old_format, new_format, num_bits)

    This function converts a String state from "Hex" or
    "Dec" to binary integer.  The num_bits input specifies the output word size. 
   
    Valid state formats are hexidecimal "Hex" and decimal "Dec".  

    Returns an integer that is the binary equal to the state value. ::

        binary_bus_value = ta_utils.convert_format("017A", "Hex", "Bin", 16)

