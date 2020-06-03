# memusage

This package computes the memory usage of a gretl object. The package comprises seven public functions for computing memory usage (in megabytes) of either a series, a list of series, a matrix, an array of matrices, a string, an array of strings and all items of a bundle comprising different data types.


# Commented sample script

## Install the package from gretl's package server
```
pkg install memusage    # download from package server
```

## Compute memory usage in megabytes for gretl objects
```
clear
set verbose off
include memusage.gfn    # load functions into memory

# Define various objects differing in their data types
strings S = defarray("S1", "S2")
matrix m = ones(10^5, 32)
matrices M = defarray(ones(10^5, 32), ones(3,2))
string web_page = readfile("http://gretl.sourceforge.net/")
bundle b = defbundle("S", S, "m", m, "web_page", web_page, "LRM", LRM)
list L = LRM LRY IDE IBO

# Call the generic function consuming a bundle with various variables
scalar mem = memusage(b, TRUE)		# returns total memory of all bundle items
print mem
```

The printout is as follows: 
```
Info: Size of strings : 1.52588e-05 MB.

Info: Size of matrix : 24.4141 MB.

Info: Size of series : 0.000419617 MB.

Info: Size of string : 0.133804 MB.

Info: Size of bundle b: 24.5483 MB.
24.548302
```
and scalar ```mem``` refers to the value ```24.5483```.



Public functions
----

-----------------------------------------------------------------------
Function: *memusage()*

Arguments:
1. bundle, input bundle
2. bool, print value in megabytes
		
Output:
* scalar, memory use in megabytes

Return:
* Computes the memory usage of all items of a bundle in megabytes.

-----------------------------------------------------------------------
Function: *memusage_matrix()*

Arguments:
1. matrix, input matrix
2. bool, print value in megabytes

Output:
* scalar, memory use in megabytes

Return:
* Computes the memory usage of a matrix in megabytes.

-----------------------------------------------------------------------
Function: *memusage_matrices()*
Arguments:
1. matrices, input array of matrices
2. bool, print value in megabytes

Output:
* scalar, memory use in megabytes

Return:
* Computes the memory usage of an array of matrices in megabytes.

-----------------------------------------------------------------------
Function: *memusage_series()*
Arguments:
1. series, input series
2. bool, print value in megabytes

Output:
* scalar, memory use in megabytes

Return:
* Computes the memory usage of a series in megabytes.

-----------------------------------------------------------------------
Function: *memusage_list()*

Arguments:
1. list, list of series
2. bool, print value in megabytes

Output:
* scalar, memory use in megabytes

Return:
'Computes the memory usage of a list of series in megabytes.

-----------------------------------------------------------------------
Function: *memusage_string()*

Arguments:
1. string, input string
2. bool, print value in megabytes

Output:
* scalar, memory use in megabytes

Return:
* Computes the memory usage of a string in megabytes. Note: If unicode formats is ASCII, the memory usage is one byte per character; if UTF-8 it depends, at least one byte but up to 4 per character. We will always assume one by per character.

-----------------------------------------------------------------------
Function: *memusage_strings()*

Arguments:
1. strings, array of input strings
2. bool, print value in megabytes

Output:
* scalar, memory use in megabytes

Return:
* Computes the memory usage of an array of strings in megabytes. Note: If unicode formats is ASCII, the memory usage is one byte per character; if UTF-8 it depends, at least one byte but up to 4 per character. We will always assume one by per character.


Changelog:
- v1.0, June 2020:
	+ initial release
