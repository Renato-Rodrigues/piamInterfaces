# Recursively calculate additional variables based on given summations and add them to the given mif file

Recursively calculate additional variables based on given summations and
add them to the given mif file

## Usage

``` r
fillMissingSummations(mifFile, summationsFile, iteration = 1, logFile = NULL)
```

## Arguments

- mifFile:

  path to mif file or a quitte object

- summationsFile:

  in inst/summations folder that describes the required summation
  groups, or path to summations file

- iteration:

  keeps track of number of recursive calls, leave to default

- logFile:

  path to logFile. if NULL, write to stdout, if FALSE don't write

## Author

Falk Benke, Renato Rodrigues
