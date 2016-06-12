Jython
=============


Jython is a Python Interpreter written completely in Java.  There are 2 ways to execute TimingAnalyzer Python scripts.

  * Select the script file from the script dialog window that is displayed when you select the File Menu -> Script.
  * From a dos command line window if you run the Windows OS,  or from a shell command line window if you run a Linux or Unix OS.   

Using the Script File Dialog from the TimingAnalyzer program.
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

  * Start the TimingAnalyzer
  * File Menu -> Script or Ctrl T.  This brings up the Script selector dialog window.
  * Select the script,  dff.py,  then click the execute button.  

The interpreter is started, then both the os and sys modules are imported, then the script is executed.

Using the Command Line
^^^^^^^^^^^^^^^^^^^^^^^^^^^


  * Change directory to the install directory of the program. 
  * Start Jython.
  * Start the application
  * Execute scripts 


The listing below shows that I started Jython in the install directory ::

    Directory of C:\Apps\TimingAnalyzer_b9894

    08/17/2009  07:59 PM    <DIR>          .
    08/17/2009  07:59 PM    <DIR>          ..
    08/07/2009  11:40 AM    <DIR>          examples
    08/07/2009  11:40 AM    <DIR>          jlib
    08/07/2009  11:40 AM    <DIR>          scripts
    07/19/2009  10:53 PM             1,107 start_app.py
    08/07/2009  11:34 AM           536,901 TimingAnalyzer.jar
                   2 File(s)        538,008 bytes
                  12 Dir(s)  41,963,491,328 bytes free

                  
                  
    C:\Apps\TimingAnalyzer_b9894>java -jar jlib\jython.jar
    Jython ...
    [Java HotSpot(TM) Client VM (Sun Microsystems Inc.)] on java1.6.0_20
    Type "help", "copyright", "credits" or "license" for more information.
    >>>

Now execute the start_app.py script.  This initializes the Jython interpreter 
so you can use all the TimingAnalyzer classes and methods. ::  
  
    >>>execfile('./start_app.py')
    >>>execfile('./scripts/dff.py')

