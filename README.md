## What is TCL
- A widely used scripting tool that was developed for controlling and extending applications
- Created by John K Ousterhout at the University of California, Berkeley
- Distributed as open source software
- Used by many synopsys command shells

## Tcl Overview
- Tcl stands for Tool Command Language
- This is used as a scripting language for gluing other applications together into a new application
- Tcl is distributed with two interpreters ie "tclsh" and "wish"
- "Tclsh" is a text based interpreter and "wish" is the same interpreter with Tk graphics commands added
- Tcl interterpreter has the following advantage:
  - Multi-platform: The same script can run under Windows OS and Unix
  - Speed: Tcl scripts run faster than Perl scripts
  - Power: Tcl supports standard program flow constructs like if-else, while, for, foreach and switch
 
## Evaluating TCL scripts under Unix
- The script should be saved with a .tcl extension
- The script should have the first line as tcl interpreter as shown below"
```
user@msubuntu:~$ /bin/tclsh
%
```

- The command to run the script is
```
$tclsh file_name.tcl
```

```
user@msubuntu:~$ tclsh set_up.tcl
```

## TCL scripts are Based on Commands
- Built in Commands
  - Provided by the Tcl interpreter itself.
  Ex set, lsearch, lappend, string, expr, incr, for, if-else etc
- Application Commands
  - Provided by Synopsys tools, written as a command procedure in C or C++ using the Tcl extension mechanism
  Ex compile_ultra, initialize_floorplan, analyze, elaborate, set_top_module
- User Defined Commands
  - Provided by you, written as a command procedure in Tcl
  Ex get_TNV

## TCL Syntax
- Tcl is a position based language
- A Tcl command is a list of words
- The first word is a command name or sub-routines name
- The words that follows may be a sub-command or a variable name
- Each words is seperated from another word by a space
- Words can be grouped with double quotes "" or curly braces{}
- Commands are terminated by a new line /n or a semicolon
- A word starting with a $ sign is a variable name
- The word between the square brackets [] must be a Tcl command

## A valid Tcl script

## Count Patterns in a String
### Objectives
- State the commands for counting patterns in a string or file
- Recognize important components of a Tcl script
- Use help resources
- Apply the commands to count cells in library report
- Analyze components of an unfamiliar script

## Tcl Version
- Starting from Version 2013.12 Design Compiler, PrimeTime and IC
- Compiler are compatible Tcl Version 8.6
- TO query the Tcl version on your tool, type the following

## Important Components of a Tcl Script

```
redirect -file exmp01 {report_constraint -all_violators}
```

## The Beginnings of a Tcl Script

## The redirect command
- The redirect command will redirect all output, meaning intermediate output (eg,. error, warning or informational messages and the report itself) as well as the result of the command
- When there are errors during a redirect, a summary message will be printed to the screen

## Commands, Arguments and Grouping

{} and " " define a single argument - this is called grouping

## exmp01 Contains all Outputs

## Add Line Continuation
- Add Line Continuation
```
Count total number of setup violations
redirect -file exmp01\
{report_constraint -all_violatiors -max_delay}
```

- The characters \<<newline > are replaced with a single space and is used for line continuation
```
pt_shell> report_constraint -help
[-all_violators]     ( Show all constraint violators)
[-max_delay]         ( Only max_delay & setup)
```

## What command is used to

## exec command

## First Tcl script: Count TNC
Count total number of setup violations
redirect -file exmp01\
{report_constraint -all_violators -max_delay}
exec grep -c VIOLATED exmp01

## What command is used to

## File command

## For Completeness

## Caution with exec
- Use caution with exec:
  - May cause a large memory footprint on some systems which may result in the Synopsys tool running out of memory
  - Script execution depends on operating system
- Tcl has a comprehensive set of system commands that allow you to write you scripts 100% in Tcl
```
Lists the contents of a directory
ls
Returns total CPU time in seconds
cputime
Returns peak memory usage in Kbytes
mem
Manipulate file names and attributes
file
Manipulate strings
regexp/string/regsub
File I/O
open/close/read/puts
```

## Write scripts 100% in Tcl

## Instead of a File, Redirect to a Variable
```
Count total number of setup violations
redirect -variable rptsring {report_constraint -all_violators -nosplit}
```

## Command Output

## Return Value

## Count Patterns in a string
```
Count total number of setup violation
redirect-variable rptstring {report_constraint-all_violators -nosplit}
regexp -all VIOLATED $ rptstring
```

## Command Output


## regexp command
- Variable substitution causes the $ and the variable name to be replaced by the value of the variable

## Capture TNV for a report

## Capture TNV using a variable
- The square brackets [] cause command substitution. Everything inside the square brackets and the square brackets themselves are replaced with the return value of the embedded command execution

## Echo a report to the screen 
- echo outputs a new line character after the string
- The characters \n and \t are substituted with a newline and tab respectively

## Capture all outputs
```
redirect -variable rptstring {report_constraint -all_violators -nosplit}
regexp -all VIOLATED $rptstring
```
- redirect captures all output of a file
- The {} characters are used for grouping - to identify a single argument for the redirect command in the example above

## Command Ouput


## Capture only the return value
```
Set myresult [report_constraint -all_violators]
```

- The [] delimit an embedded command -report_constraint is executed and replaced with its result
- The {} characters are used for grouping -to identify a single argument for the redirect command in the example above
- redirect captures all output of a command
```
redirect -var rptstring {report_constraint -all}
regexp -all VIOLATED $rptstring
```

## Capture only the Return Value
- The [] delimit an embedded command - report_constraint is executede and replaced with its result

## Control Flow, Math Functions and Procedures
### Objectives
- State the commands for
  - Adding control flow to script
  - Creating user defined commands
  - Executing arithmetic functions

## Branching Construct
- if construct is a single choice conditional branch
```
if {expr1}{
   st1;
   } elseif {expr2}{
   st2;
   } else {
   st3:
   }
```

## Adding control flow to script

## Use control flow commands

## If command

## Logical Expressions and Operators
- 0 is interpreted as false
- Any number other than 0 is interpreted as true

## expr command

## Add to the previous example

## Add in error catching
- What must info return if the variable TNV does NOT exists

## Arithmetic Operations
- Math Operations
  - expr
  - incr
- expr provides an interface to a general purpose interface engine. It can perform math operations as well Boolean operations.
  - expr math_expression

## Other control flow command
```
To check conditions
If{expr} {body}
Execute the body until expr is false
while {expr} {body}
Execute start
Execute body + next until expr is false
for {start} {expr} {next} {body}
```
- Break: Abort looping command
- Continue: Skip to the next iteration of a loop

## Math Expressions
- Everything in Tcl is a string
- No arithmetic is performed by the interpreter
```
set a 5
set b 5
puts "a+b=$a+$b"
>a+b=5+5
```
- Use expr command
```
puts "a+b=expr$a+expr$b"
>a+b=10
```

## Details on Arithmetic Computations
- Integers are used until a floating-point number is introduced, after which floating-point is used
```
pt_shell>expr 10+5
15
pt_shell>expr 10.0+5
15.0
pt_shell>expr 12/7
1
pt_shell>expr 12/7+3.0
4.0
pt_shell>expr 12.0/7+3
4.71428571429
```

## get_TNV command
- How to create own command to calculate?
```
If {[get_TNV]<20}
{report_timing}
else {
compile -incr-map_effort high
}
Proc get_TNV {} {
redirect-variable rptstring \
                     {report_constraint-all_violators-max_delay}
regexp-all VIOLATED $ rptstring
}
```

## More Details on Tcl Procedures

## Adding Arguments
```
pt_shell>source get_TNV.tcl
pt_shell>get_TNV-max_delay
pt_shell>get_TNV-min_delay
```
```
proc get_TNV {max_or_min} {
          redirect-variable rptstring
                    {report_constraint-all_violators $max_or_min}
regexp-all VIOLATED $rptstring
}
```

## Specifying Default values for Arguments
```
proc get_TNV {{max_or_min-max_delay}} {
redirect-variable rptstring
{report_constraint-all violators $max_or_min}
regexp-all VIOLATED $rptstring
}
```
```
pt_shell>source get_TNV.tcl
pt_shell>get_TNV
28
```

## Default Arguments
- Default arguments, if any must be the last arguments for the procedure. If a default is not specified, the argument is required.

## Procedure variables are local
```
pt_shell>source get_TNV.tcl
pt_shell>get_TNV
pt_shell>printvar rptstring
-> Information: No variables matched 'rptstring'
```
```
proc get_TNV {} {
redirect-variable rptstring
         {report_constraint-all violators -max_delay}

regexp -all VIOLATED $rptstring
}
```

## Global Versus Local Namespace
- A namespace is an encapsulation of commands and variables to avoid interference with other namespaces

## Accessing Global Variables In a Procedure
```
proc silly_TNV {} {
global rptstring
redirect-variable rptstring
{report_constraint-all_violators -max_delay}
regexp -all VIOLATED $rptstring
}
```
```
pt_shell>set rptstring "hello world"
pt_shell>source get_TNV.tcl
pt_shell>get_TNV
28
pt_shell>printvar rptstring
```

## Global Variable in a Procedure
- Procedure names are global
- Variable inside procedure are local
- Variable defined outside of any procedures are global
- Global variables not automatically visible inside procedures. They are accessed inside the procedure, using the following command
```
%global varname1 varname2...
```

## Command Result versus Output

## Output and Return Values of Procedures

## Provide Explicit Return values

## Return Command

## what happens without an Explicit Return?
```
proc get_TNV {} {
redirect-vi variable rptstring
{report_constraints-all_violators-max_delay}
regexp-all VIOLATED $rptstring
}
```

- The return value is the return value of the executed command in the procedure body

## Gathering Information on Procedures
```
pt_shell>source get_TNV.tcl
pt_shell>info body get_TNV
 redirect -variable rptstring \
       {report_constraint -all_violators $max_or_min}
 regexp -all VIOLATED $rptstring
pt_shell>info args get_TNV
 max_or_min
```

## The Complete Metrics Command

## Strings, Lists and Pattern Matching
## Data Types
- Strings
- List
- Associative array
- Strings are basic data items in Tcl
  - A Tcl string can contain alphanumeric, pure numeric, boolean or even binary data
  - Alphanumeric can include any letter, number or punctuation
  - Format specifiers like %s, %f, %o, %x are used to display the strings
```
set y "abcdef"
set d 1.23
set o 075
set h 0xab4

puts (format "Values : %s\t%2.3f\t%o\t%x" $y $d $o $h]
```

## What are Strings?
- Strings are a sequence of characters

## Strings Commands
- string
- Basic syntax: string operation string_value otherargs
- Operation
- match: the string match command searches a target string for a match to a pattern
- The pattern is matched using the global match rules
```
% string match {*TCL*} {This is Tcl session}
1
```

- Glob match rules
- * Matches 0 or more characters
- ? Matches a single character
- [] Matches a character in the set defined within the brackets

## Strings Commands
- tolower
- The string tolower command converts a string to lowercase letters
```
set str "This is a tcl session"
set lower [string tolower $str]
puts "$str\t $lower"

- toupper
- The string toupper command converts strings to uppercase using the same syntax
```
set str "This is a tcl session"
set upper [string toupper $str]
puts "$str\t $lower"

- length
- The string length command returns the number of characters in the string
```
set s1 "This is Tcl session"
set length [string length $s1]
puts "$length"
```

- first/last
- Returns the index of the first (or last) occurrence of substr in string
```
set str "This is a Tcl session"
set st_first [string first TCL $str]
puts "$st_first"
```

- range
- Returns the characters in string between first and last
```
set str "This is a Tcl session"
set st_first [string first TCL $str]
puts "$st_first"
set st_last [string last session $str]
puts "$st_last"
set subset [string range $str $st_first $st_last]
puts "$subset"
```

- format
- The string format generates formatted strings and can perform some data conversions
- It is similar to sprint command in C language
- format formatstring data1
  - formatstring is the format of the string being returned
  - data1 is the data to substitute into the formatted string
```
set str [expr 2.3/4]
set str_format [format {%6.3f} $str]
puts "$str_format"
```

- %f:Floating point
- %c: ASCII Character value
- %d: Decimal Integer
- %o: Octal value
- %x: Hexadecimal value

## Lists
- A list is a set of elements enclosed within curly braces as shown: {abc,def,apple}
- The first element is indexed at 0
- Lists processing commands
  - list element1 element2 element3
  - lappend command appends new data to a list towards the end of the list
```
set list_var [list Python Perl TCL]
puts "$list_var"
```

```
set list_var [list Python Perl TCL]
lappend list_var Ruby
puts "$list_var"
```

## What are Lists?
- Lists are an ordered group of elements (Strings, Embedded Lists)
```
set mylist "red blue green" (spaces are used to separate each element)
```

```
pt_shell> set mylist "red blue green"
red blue green
```

## Lists processing commands
- split command return the string as a list
```
set list_var1 1.2.3.abc
set split_var1 [split $list_var1.]
puts "$split_var1"
```

- join command joins the elements of a lists into a string
```
set numbers [list 1 2 3 4]
set join_num [join $numbers :]
puts "$join_num"
```

- llength command returns the length of the list
```
set numbers [list 1 2 3 4]
set list_num [llength $numbers]
puts "$list_num"
```

## 3 Types Pattern Matching on Strings or Lists
- Pattern matching is an essential component for a variety of useful tasks

- Regular Expressions (regexp -all)
```
pt_shell> regexp -all -inline (\s+) $mylist
red blue green
```

## Globbing versus exact Pattern Matching

```
analyze-format verilog [glob risc_rtl/*.v]
```

## Pattern Matching for Strings
- The commands used to perform pattern matching for strings
    
## Globbing and Special Characters


