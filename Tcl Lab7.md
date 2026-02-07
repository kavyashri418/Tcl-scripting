## Remove Duplicate Timing Reports

_Objective: Apply the skills and concepts taught thus for in building the procedure clean_log_

### Relevant Files & Directories
```
Scripts - Current working directory
orca.v - rtl netlist
tcl_procs - reference files
run.tcl - run script for orca
```

## Task 1: Remove the Duplicate Reports
- This final task will complete the procedure clean_log. Do not forget to utilize all of the job aids!
- The final step is to only write the unique reports to the outfile. If there are duplicate reports, the in and out files will no longer be equivalent
- Modify your procedure to include the following:
  - After each complete timing report is found from the in file, compare the new timing report string with a list of unique timing report strings that were previously found. If there is a match, then ignore the new timing report string and continue. IF there is no match, add this new timing report string to the list and write it to the out-file log
  - If the list of unique timing reports does not exit create it and write the new timing report to the out-file log
  - IF the -verbose switch is provided the command should output the suggested summary shown below. The command should return the number of duplicate reports
  - Source the modified procedure into either Design Compiler or PrimeTime and verify the following
```
Execute the following lines in either Design Compiler or PrimeTime
pt_shell> clean_log-in./log/timing.log-out./log/clean.log-v
There were 200 timing reports in the original log file of these, 120 were unique timing reports
80 timing reports were cleaned
80
```

- Quit the Synopsys tool
