## Count Timing Reports

_Objective: Apply the skills in building the procedure clean_log_

### Relevant Files & Directories
```
Scripts - Current working directory
orca.v - rtl netlist
tcl_procs - reference files
run.tcl - run script for orca
```

## Task 1: Count Timing Reports in timing.log
- Modify clean_log to count the total number of timing reports in timing.log
- Count the total number of timing reports in timing.log (The in and out files should still remain exactly the same)
- Modify the procedure to include the following three bullets:
  - Within the while loop, capture each complete timing report from the in file as a single string. Each line in the timing report must be separated by a newline
  - Identify the first line of a timing report using the characters *startpoint* and use *slack* to identify the last of timing report (the *represents a wildcard, matching any sequence of characters)
  - After each complete timing report is captured, write the complete report to the out file
  - The command clean_log should return the total number of timing reports in the file
  - Source the modified procedure into either Design Compiler and PrimeTime and verify the following:
```
Execute the following lines in either Design Compiler or PrimeTime
pt_shell> clean_log_in ./log/timing.log-out./log/clean.log
-> 200
The two log files should once again be equivalent
pt_shell>exec diff timing.log clean.log
```

- Quit the Synopsys tool

