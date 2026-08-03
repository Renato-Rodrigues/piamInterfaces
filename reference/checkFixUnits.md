# Check units in IIASA submission by comparing mifdata to a project template

Check units in IIASA submission by comparing mifdata to a project
template

## Usage

``` r
checkFixUnits(mifdata, template, logFile = NULL, failOnUnitMismatch = TRUE)
```

## Arguments

- mifdata:

  quitte object or filename of mif file

- template:

  object provided by loadIIASAtemplate() or getMapping() interprets it
  as a mapping if 'piam_variable' and 'piam_unit' columns exist

- logFile:

  filename of file for logging

- failOnUnitMismatch:

  boolean whether to fail in case of unit mismatches recommended for
  submission, not used for generating mappings

## Value

quitte object with adapted mif data

## Author

Oliver Richters
