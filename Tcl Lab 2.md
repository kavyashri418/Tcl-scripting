## Create a Command Metrix
_Objective: Expand an existing Tcl procedure to generate runtime metrics

### Relevant Files & Directories
```
scripts - current working directory
orca.v - rtl netlist
tcl_procs - reference files
run.tcl - run script for orca
```

## Task 1: Modify a procedure for Run Time Metrics
- In order to optimize tool performance, identify the part of a run script that consumes the most CPU time or memory
- We will create a command called metrics. The first time this procedure is called, it generates metrics from the beginning of the process. All subsequent calls to this procedure generate the "delta" metrics for CPU usuage. (note that peak memory usuage is always shown from the beginning of the process)

- Invoke either Design Compiler or PrimeTime and read all ORCA design using the script run.tcl
```
unix%dc_shell -f scripts/run.tcl
dc_shell>
```

```
unix%pt_shell -f scripts/run.tcl
pt_shell>
```

_All subsequent instructions are generic for either tool - Design Compiler or PrimeTime
- Look at the starting point, an initial procedures has been provided and is shown
- Source the file ./scripts/metrics.tcl, which contains this initial procedure and execute the command metrics using an arbitrary header message

## Task 2: Complete the Command Metrics
- Use this flow diagram and text editor to modify the initial procedure in ./scripts/metrics.tcl. As we modify the procedure, source it and try it until we are satisfied that the procedure is correct

_For testing new procedure, it will be helpful to remove the user defined global variable. Use the unset command to do this_
- Quit the Synopsys tool
- Use the script ./script/runmetrics.tcl as a final test for procedure in either Design Comipler or PrimeTime. The run time results will be redirected to a file called ./metrics.log
```
unix% dc_shell -f scripts/runmetrics.tcl
(or)
unix% pt_shell -f scripts/runmetrics.tcl
unix% more ./metrics.log
```

- Visually identify the commands learned in lecture and applied in this lab on job aid #1 that are useful for adding control flow to scripts, performing mathematical functions and creating user defined commands

