# Checks for a run if the variables sum up as expected and logs spotted gaps

Checks for a run if the variables sum up as expected and logs spotted
gaps

## Usage

``` r
checkSummations(
  mifFile,
  outputDirectory = ".",
  template = NULL,
  summationsFile = NULL,
  logFile = NULL,
  logAppend = FALSE,
  generatePlots = FALSE,
  mainReg = "World",
  dataDumpFile = "checkSummations.csv",
  plotprefix = NULL,
  absDiff = 0.001,
  relDiff = 1,
  roundDiff = TRUE,
  csvSeparator = ";"
)
```

## Arguments

- mifFile:

  path to the mif file to apply summation checks to, or quitte object

- outputDirectory:

  path to directory to place logFile and dataDumpFile.

- template:

  mapping to be loaded, used to print the piam_variable corresponding to
  the data variables

- summationsFile:

  in inst/summations folder that describes the required summation groups
  if set to 'extractVariableGroups', tries to extract summations from
  variables with + notation

- logFile:

  file where human-readable summary is saved. If NULL, write to stdout.
  If FALSE, don't log.

- logAppend:

  boolean whether to append or overwrite logFile

- generatePlots:

  boolean whether pdfs to compare data are generated. Requires
  outputDirectory.

- mainReg:

  main region for the plot generation

- dataDumpFile:

  file where data.frame with the data analysis is saved. Requires
  outputDirectory. If NULL, result is returned.

- plotprefix:

  added before filename

- absDiff:

  threshold for absolute difference between parent variable and
  summation

- relDiff:

  threshold (in percent) for relative difference between parent variable
  and summation

- roundDiff:

  should the absolute and relative differences in human-readable summary
  and dataDumpFile be rounded? The returned object always contains
  unrounded values.

- csvSeparator:

  separator for dataDumpFile, defaults to semicolon

## Author

Falk Benke, Oliver Richters
