# From mappingData, return the piam_variable sum as a string for a given exportname

From mappingData, return the piam_variable sum as a string for a given
exportname

## Usage

``` r
sumNamesWithFactors(mappingData, exportname, width = NULL)
```

## Arguments

- mappingData:

  mapping data as obtained by getMapping()

- exportname:

  name to be matched in 'variable' column

- width:

  can be NULL so everything is pasted after each other, or the width
  argument from checkSummations such that every element gets its own
  line

## Author

Oliver Richters
