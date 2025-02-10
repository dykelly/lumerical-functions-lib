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
**Example 1:**
```
x = {"TE0","TE1"};
print(x); # built-in function
-----> Cell array with 2 elements
```
Instead we can use: 
```
print2(x); # function from this library
----->
      TE0
      TE1
```
**Example 2:**
```
?getresult; # print out the possible outputs of the 'getresult' built-in function
----->
FDE::data::material
FDE::data::mode1
FDE::data::mode2
FDE::data::mode3
```
Now, what on Earth is the data we have obtained? Is it a cell (array) that we can loop over to subsequently extract data for each mode? No. Is it a string with a new-line character (`endl`) separating the modes? Yes. Why? Only God knows. Is this Documented in Lumerical documentation? Absolutely not. 

So if we try:
```
results_found = getresult;
for (result = results_found) {
    ?result;   
}
```
the output is 
-----> *Error: Argument of for loop must be a matrix or a cell*

Consider this for debugging: 

```
results_found = getresult; 
?getdtype(results_found);
-----> str
```
Now we know it's a string, and can adapt accordingly:

```
results_cell = splitstring(results_found, endl);
for (result = results_cell) {
    ?result;   
}
```
which works correctly. 


## Launch
Import to your .lsf file via:
```
addpath("C:\Users\path_to_lib..\lumerical-functions-lib);
function_lib_MODE;
```
See inline comments for functions.
