# Check IIASA submission by comparing mif data to a template file (xlsx or yaml) provided by IIASA

Check IIASA submission by comparing mif data to a template file (xlsx or
yaml) provided by IIASA

## Usage

``` r
checkIIASASubmission(
  mifdata,
  iiasatemplate,
  logFile = NULL,
  failOnUnitMismatch = TRUE
)
```

## Arguments

- mifdata:

  quitte object or filename of mif file

- iiasatemplate:

  filename of xlsx or yaml file provided by IIASA

- logFile:

  filename of file for logging. Set to NULL for stdout, set to FALSE for
  none.

- failOnUnitMismatch:

  boolean whether to fail in case of unit mismatches recommended for
  submission

## Value

quitte object with adapted mif data

## Author

Oliver Richters

## Examples

``` r
if (FALSE) { # \dontrun{
# Simple use. Generates submission file in output folder:
checkIIASASubmission(
  mifdata = "file.mif",
  iiasatemplate = "template.xlsx",
  logFile = "logFile.txt"
)
} # }
```
