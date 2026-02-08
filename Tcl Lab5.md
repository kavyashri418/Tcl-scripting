## Add Non-Positional Arguments

_Objective: Create and use basic examples to explore Tcl arrays
Add non-positional arguments and validation by parsing procedure arguments_

### Relevant Files & Directories
```
Scripts - Current working directory
orca.v - rtl netlist
tcl_procs - Reference files
run.tcl - Run script for orca
```

## Task 1: Modify a procedure for Run Time Metrics
- Create and use basic examples to learn about Tcl arrays
  - Invoke either PrimeTime or Design Compiler
  - Create an array of clocks and their frequencies in MHz; execute the following lines:
```
set clk(pci_clk) 50
set clk(sys_clk) 100
set clk(sys_2x_clk) 200
```

- Return the number of array elements by executing the following line:
```
array size clk
```

- Return a list of the array elements (or indices) by executing the following line:
```
array names clk
```

- Determine if a specific array element exists using globbing-style pattern matching
```
array names arrayName pattern
array names clk pci_clk

