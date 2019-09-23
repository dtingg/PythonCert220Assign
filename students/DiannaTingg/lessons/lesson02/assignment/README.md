# Assignment

One of the challenges with the existing code base at HP Norton is the lack
of the necessary debug information when issues occur.

One such case is the *charges_calc* script. Its purpose is to convert a list of
existing rentals of individual inventory items (for example, table lamps),
including number of units rented, price charged per day and rental start / end dates,
and return the same list with the total cost of the rental (based on the number of
days the item or items have been rented), as well as total cost per item (in the 
case of multiple items). It also calculates the square root of the total cost of the
rental for statistical purposes. Both the input and the output of the script are JSON files.

The problem at this point is that, using the included JSON input file, the script 
is not working. There is no error message or anything else indicating what is
going on and no output file is being produced.

Your goal this week is twofold: You need to use the Python debugger to figure out
why the script is not working and you also need to incorporate logging into the code
so that someone doing debug can follow the flow of the script.

Here is what you need to do:
----------------------------

1. Download the *charges_calc.py* code and review it. Make sure you also download *source.json*, which contains the sample source data (that will be your input file).
2. Try as best as you can to understand what the code is doing.
3. Using the debugger, try to understand what is going on with the
   expected command line parameters. See if from the code and through
   watching variables and creating dummy parameters you can infer enough
   to get the program to run. Capture your debug work to a text file.
4. Now, enable logging and start inserting logging statements to track the code's execution.
5. Add comments that describe your discoveries, and additional things you need.
6. Add warnings for things missing in the source data that are expected but that impede some of the calculations (for example, unreturned items do not have a *rental_end* value).
7. Add error messages for inconsistencies in the source data that could make your program crash or return incorrect data.

Requirements:
-------------

1. Your script needs to deal with data inconsistencies that could make it crash or return incorrect data (handle the exception and issue an error message for these and let the script continue) and issue warnings for missing data. 
2. Capture you debug work in a text file called charges_calc.log. You will need that for your submission.
3. Setup logging messages so that they are disabled by default and can by enabled by using *-d 1* or *--debug 1* from the command line. Use the *argparse* module for this. You will have the following debug levels:
    #. 0: No debug messages or log file.
    #. 1: Only error messages.
    #. 2: Error messages and warnings.
    #. 3: Error messages, warnings and debug messages.
4. You need to implement three types of logging messages:
    #. Debug: General comments, indicating where in the script flow we are. Should be shown on screen only (i.e., never saved to logfile).
    #. Warning: Used for missing elements in the source data that force a change in the flow. Shown on screen and on the log file.
    #. Error: Used for inconsistencies in the source data that will cause the script to crash or report incorrect results. Shown on screen and on the log file.
5. Use the following format for your log messages: 


    log_format = "%(asctime)s %(filename)s:%(lineno)-3d %(levelname)s %(message)s"

6. Use the following filename format to timestamp your log files:


    log_file = datetime.datetime.now().strftime("%Y-%m-%d")+'.log'

Other requirements:
-------------------
- Your code should not trigger any warnings or errors from Pylint.

Submission:
-----------

Your submission should include the following:

- Updated version of *charges_calc.py* (keep the same filename).
- Your Python debugger logfile. Include it as *debugger_log.txt*.
- Logfile created by running your updated script on the source data. Include it as *charges_calc.log*.
- Output JSON file created with the updated script. Include it as *output.json*.

Tips
----
- Think about what a developer would need by way of logging to help trace what
  has happened and gone wrong when the module is running.
- Add details of your approach to logging to the module docstring to assist
  anyone who maintains the module.
- Be sure to document details of your fix from the debugging activity in
  your pull request.
