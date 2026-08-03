# Check unit factor in template

This function checks whether the piam_factor in a mapping fits unit and
piam_unit. It does the following:

1.  check whether the units are identical based on areUnitsIdentical()
    and piam_factor is 1 or -1.

2.  based on scaleConversion defined below, check whether manually added
    factors are satisfied This works based on regex matching, so for
    example 1000 TW = 1 PW is matched by the c("1000", "T", "P") line.
    If the tests fail because of a new unit, you can add them below. If
    the units are really identical except for spelling, better add them
    to areUnitsIdentical.R

## Usage

``` r
checkUnitFactor(template, logFile = NULL, failOnUnitMismatch = TRUE)
```

## Arguments

- template:

  object provided by loadIIASAtemplate()

- logFile:

  filename of file for logging

- failOnUnitMismatch:

  boolean whether to fail in case of unit mismatches recommended for
  submission, not used for checking mapping

## Value

quitte object with adapted mif data

## Author

Oliver Richters
