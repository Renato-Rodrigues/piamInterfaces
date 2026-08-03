# Check NGFS submission by comparing mif data to a template file (xlsx or yaml) provided by IIASA

Check NGFS submission by comparing mif data to a template file (xlsx or
yaml) provided by IIASA

## Usage

``` r
checkNGFS(mifdata, iiasatemplate, logFile, generatePlots = TRUE)
```

## Arguments

- mifdata:

  quitte object or filename of mif file

- iiasatemplate:

  filename of xlsx or yaml file provided by IIASA

- logFile:

  filename of file for logging. Set to NULL for stdout, set to FALSE for
  none.

- generatePlots:

  boolean whether to plot failing summations

## Value

quitte object with adapted mif data

## Author

Oliver Richters
