## Count Patterns in a String
_Objective: Analyze the components of an unfamiliar script by recognizing the significance of special characters and visually distinguishing the commands, variables and arugments
Count the number of muxes and xor gates available in a technology library
Use help resources when writing scripts including: help-verbose; man; and the provided job aid_

### Relevant Files & Directories
```
Scripts - Current working directory
orca.v - rtl netlist
tcl_procs - reference files
run.tcl - run script for orca
```

Task 1: Use the help resources
- Invoke either Design Compiler or PrimeTime and read the ORCA design using the script run.tcl
```
unix%dc_shell-f scripts/run.tcl
dc_shell>
```
```
unix%pt_shell-f scripts/run.tcl
pt_shell>
```

_All subsequent instructions are generic for either tool - Design Compiler or PrimeTime_

 - Gather command syntax information
```
help -v redirect
```

- Use man pages for more detailed explanations and example usuage
```
man redirect
```

## Task 2: Count Library Cells
- On job aid #1. visually identify the commands that are useful in counting patterns in a string or a file
- Count the number of muxes (the answer should be 36) and xor gates (=24) available in the technology library core_slow.db
- Give that
  - Library cells can be reported using the following command
  ```
  report_lib core_slow.db
  ```
  - All mux cells begin with the letters mux (eg mx2a1)
  - All xor gates begin with the letters xor (eg xor3b15)

## Task 3: Analyse an Unfamiliar script
- Visually identify and count each command in the following script
```
exec cat ./tcl_procs/clock_domain.tcl
```

- Visually identify and count where variable substitution is occurring

## Task 4: Counting pattern matches using regxp
- Counting pattern matches using the regexp commamnd
- Assume the string as: abc icc snps icc def icc
- A timing report has the following line "clock v_CLK (rise edge) 7.50. Write a Tcl script using string processing commands to match the string "v_CLK" and replace it with "v_PCI_CLK"
- Quit Synopsys tool
  
