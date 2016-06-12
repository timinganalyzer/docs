Python API 
=============


The TimingAnalyzer class is the main application class. 
It is assigned to the variable taApp automatically as the interpreter is initialized.
It controls most all of the GUI related functions in the main window like multiple tabs for 
timing diagrams, the menus, the toolbar, and the status bar.  It also controls 
switching from the timing diagram view to the image view and other views 
that might be added in the future. Possibly a "transaction editor" diagram view, 
or "analysis reports" view.  


TimingDiagram
------------------

.. autofunction:: app.get_timing_diagram(taApp)

.. autofunction:: app.new_timing_diagram(taApp, dir=None, file_name=None)

.. autofunction:: commands.get_time_scale(td)

.. autofunction:: commands.set_end_time(td, end_time)

.. autofunction:: commands.set_start_time(td, start_time)

.. autofunction:: commands.start_script(td)

.. autofunction:: commands.stop_script(td)


File I/O
----------------

.. autofunction:: app.get_file_name(taApp)

.. autofunction:: app.file_save(taApp)


Signals 
---------------

.. autofunction:: commands.add_digital_clock(td, name, start_state, freq, duty_cycle=50)

.. autofunction:: commands.add_digital_bus(td, name, start_state, format='Hex')

.. autofunction:: commands.add_digital_signal(td, name, start_state)

.. autofunction:: commands.get_signal_list(td):

.. autofunction:: commands.get_edit_signal_list(td)

.. autofunction:: commands.get_state_at_time(sig, state_time)

.. autofunction:: commands.get_name(sig)

.. autofunction:: commands.get_start_state(sig)

.. autofunction:: commands.set_rise_time(sig, rise_time)

.. autofunction:: commands.set_fall_time(sig, fall_time)


Edges
---------

.. autofunction:: commands.add_edge(sig, edge_time, edge_state)

.. autofunction:: commands.add_edge_margin(sig, edge_time_min, edge_time_max, edge_state)

.. autofunction:: commands.get_edge(sig, edge_num)

.. autofunction:: commands.get_edge_list(sig)

.. autofunction:: commands.get_last_state(ed)

.. autofunction:: commands.get_next_state(ed)

.. autofunction:: commands.get_pt(ed, pos, case)

.. autofunction:: commands.get_pt1_min(ed)

.. autofunction:: commands.get_pt2_min(ed)

.. autofunction:: commands.get_pt3_min(ed)


Pulse Width Labels
--------------------------

.. autofunction:: commands.add_pulse_width_label(td, e1, e2, label, label_pos='Center')


StateBars
--------------

.. autofunction:: commands.add_statebar(td, edge, label, line_style, xoffset, yoffset)


Delays 
-----------

.. autofunction:: commands.add_part_delay(td, name, min, typ, max, desc)

.. autofunction:: commands.add_delay(td, part_delay, edge_from, edge_to)


Constraints
-------------------

.. autofunction:: commands.add_part_constraint(td, name, min, max, desc) 

.. autofunction:: commands.add_constraint(td, part_constraint, edge_from, edge_to)


JitterMargins
---------------------

.. autofunction:: commands.add_part_jitter_margin(td, name, pos_jitter, neg_jitter, desc)

.. autofunction:: commands.add_jitter_margin(ed, jitter_margin)



