# lumerical-functions-lib
A library of helpful functions for Lumerical scripting (.lsf) files

Importing the _MODE or _DEVICE library (respectively for Ansys Lumerical Mode or Device) will also import the _general library.

Examples of usage are:

- `print2(my_cell);` actually prints the contents of a cell, unlike print(my_cell)
- `plotmodeE2` plots (and saves) E2 of a given mode
- `all_overlaps(ref_mode)` calculates field overlaps of all modes with a given reference mode on the d_card
- `integrate_E(mode_n, x0, x1, y0, y1)` integrates the E-field for a given rectangle [[x0,y0],[x1,y1]].
## Motivation
There's no sugar coating it, the in-built Lumerical scripting language lacks in every way imaginable.
```
x = {"TE0","TE1"};
print(x); # built-in function
-----> Cell array with 2 elements
print2(x); # function from this library
----->
      TE0
      TE1
```

## Launch
Import to your .lsf file via:
```
addpath("C:\Users\path_to_lib..\lumerical-functions-lib);
function_lib_MODE;
```
See inline comments for functions.
