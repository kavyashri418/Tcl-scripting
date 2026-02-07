## Read and Write log files

_Objective: Use the commands for file I/O and defining procedure attributes 
Use help resources to create a command group_

### Relevant Files & Directories
```
Scripts - Current working directory
orca.v - rtl netlist
tcl_procs - reference files
run.tcl - run script for orca
```

## Task 1: Assess the Task
- Start the Tcl procedure clean_log by accepting an incoming log file and writing out exactly the same log file to a different file name
- The name of the command you will create is clean_log
- Has two required arguments - the first is the incoming log file name and the second is the file name for the resulting clean log file
- Open the incoming log file in read mode
- Open the clean log file in write mode
- Read the incoming log file one line at a time until the EOF character is reached
- As each line is read, write out the same line to the clean log file
- Close both files when complete

## Task 2: Read and Write a Log file with file I/O
- Modify the starting point to complete the task described above
- Open file ./scripts/clean_log.tcl in a text editor and create a Tcl procedure to accomplish the steps outlined in task 1 above
- Invoke either PrimeTime or Design Compiler to test the Tcl procedure
Note: Execute dc_shell from a Unix prompt to invoke Design Compiler. Source the file ./scripts/run.tcl
```
Execute the following lines in either Design Compiler or PrimeTime to test the successful completion of this first step
source ./scripts/clean_log.tcl
clean_log ./log/timing.log./log/clean.log
If the files are equivalent the following command returns nothing
exec diff./log/timing.log./log/clean.log
```

_If you overwrite the timing.log file accidently, then run PrimeTime using ./scripts/runtiming.tcl and log the run to./log/timing.log to re-create this file_
- Do not quit the Synopsys tool

## Task 3: Define Procedure Attributes
- Expand the Tcl procedure clean_log by adding help information and placing this procedure in the My_procs command group by defining procedure attributes
- Confirm the default help information for Tcl procedures by executing the following commands in Synopsys tool
```
help-verbose clean_log
Execute the next line and search for clean_log
help procedures
```

- Use your available help resources to find a command
- Create a command group called My_procs. Add this line to the file./scripts/clean_log.tcl
- Define help information for the Tcl procedure you just created, clean_log, and place your command in the command group My_procs
- Follow the example shown below. Add this line, which will define procedure attributes, to the file ./scripts/clean_log.tcl
```
pt_shell> help -verbose clean_log
clean_log   Removes duplicate timing reports
infile (Log file to be cleaned)
outfile (Clean log file name)
pt_shell> help My_procs
My_procs:clean_log     Removes duplicate timing reports
```

- Test the above steps by sourcing the completed file ./scripts/clean_log.tcl and using help
- Quit the Synopsys tool


