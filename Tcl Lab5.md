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
array names clk pci*
array names clk sdram_clk
```

- Calculate the period for pci_clk

## Task 2: Play with Tcl Dictionaries
- Create a dictionary of clocks and their frequencies in MHz and assign it to a variable "my_clk"
Note: Clocks are pci_clk, SYS_CLK, SYS_2x_CLK, Corresponding frequencies are: 100, 100, 200

## Task 3: Play with Parsing Procedure Arguments
- Use a simple example to gain an understanding of parsing procedure arguments before applying this command to procedure clean_log
- Source the Tcl procedure in ./scripts/play.tcl and execute help
```
help -verbose play
info body play
info args play
```

- Discover what happens if all options are specified
```
play -fruit apple-veggie carrot-verbose
```

- Discover what happens if the argument positions are changed
```
play -veggie spinach-verbose-fruit banana
```

- The command parse_proc_arguments not only parse the arguments into an array, it also performs argument validation and processes the -help option
```
play -help
play -bad_switch
```

- Open the file ./scripts/play.tcl in a text editor
- There are three procedure arguments for the command play, thus the option -define_args is a group of three lists. Each list has the following format:
```
{arg_name option_help value_help data_type attributes}
```



