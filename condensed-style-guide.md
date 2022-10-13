# RAMP Condensed Style Guide

### Basic Style Elements

* Use SystemVerilog-2012 conventions, files named as module.sv, one file
  per module
* Only ASCII, **100** chars per line, **no** tabs, **two** spaces per
  indent for all paired keywords.
* C++ style comments `//`
* For multiple items on a line, **one** space must separate the comma
  and the next character
* Include **whitespace** around keywords and binary operators
* **No** space between case item and colon, function/task/macro call
  and open parenthesis
* Line wraps should indent by **four** spaces
* `begin` must be on the same line as the preceding keyword and end
  the line
* `end` must start a new line

### Construct Naming

* Use **lower\_snake\_case** for instance names, signals, declarations,
  variables, types
* Use **UpperCamelCase** for tunable parameters, enumerated value names
* Use **ALL\_CAPS** for constants and define macros
* Main clock signal is named `clk`. All clock signals must start with `clk_`
* Reset signals are **active-low** and **asynchronous**, default name is
  `rst_n`
* Signal names should be descriptive and be consistent throughout the
  hierarchy

### Suffixes for signals and types

* Add `_i` to module inputs, `_o` to module outputs or `_io` for
  bi-directional module signals
* The input (next state) of a registered signal should have `_d` and
  the output `_q` as suffix
* Pipelined versions of signals should be named `_q2`, `_q3`, etc. to
  reflect their latency
* Active low signals should use `_n`. When using differential signals use
  `_p` for active high
* Enumerated types should be suffixed with `_e`
* Multiple suffixes will not be separated with `_`. `n` should come first
  `i`, `o`, or `io` last

### Language features

* Use **full port declaration style** for modules, any clock and reset
  declared first
* Use **named parameters** for instantiation, all declared ports must
  be present, no `.*`
* Top-level parameters is preferred over `` `define`` globals
* Use **symbolically named constants** instead of raw numbers
* Local constants should be declared `localparam`, globals in a separate
  **.svh** file.
* `logic` is preferred over `reg` and `wire`, declare all signals
  explicitly
* `always_comb`, `always_ff` and `always_latch` are preferred over `always`
* Interfaces are discouraged
* Sequential logic must use **non-blocking** assignments
* Combinational blocks must use **blocking** assignments
* Use of latches is discouraged, use flip-flops when possible
* The use of `X` assignments in RTL is strongly discouraged, make use of SVAs
  to check invalid behavior instead.
* Prefer `assign` statements wherever practical.
* Use `unique case` and always define a `default` case
* Use available signed arithmetic constructs wherever signed arithmetic
  is used
* When printing use `0b` and `0x` as a prefix for binary and hex. Use
  `_` for clarity
* Use logical constructs (i.e `||`) for logical comparison, bit-wise
  (i.e `|`) for data comparison
* Bit vectors and packed arrays must be little-endian, unpacked arrays
  must be big-endian
* FSMs: **no logic** except for reset should be performed in the process
  for the state register
* A combinational process should first define **default value** of all
  outputs in the process
* Default value for next state variable should be the current state
