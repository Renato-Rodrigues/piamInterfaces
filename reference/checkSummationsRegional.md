# Checks for a run if the regions for selected variables sum up as expected

Checks for a run if the regions for selected variables sum up as
expected

## Usage

``` r
checkSummationsRegional(
  mifFile,
  parentRegion = NULL,
  childRegions = NULL,
  variables = NULL,
  skipUnits = c("", "arbitrary unit", "arbitrary unit/yr"),
  skipBunkers = NULL,
  intensiveUnits = TRUE,
  absDiff = 1e-04,
  relDiff = 0.1
)
```

## Arguments

- mifFile:

  path to the mif file to apply summation checks to, or quitte object

- parentRegion:

  region to sum up to. Defaults to World or GLO

- childRegions:

  regions that should sum up to `parentRegion`. Default to all except
  parentRegion

- variables:

  list of variables to check. Defaults to all in mifFile

- skipUnits:

  units to be skipped. Add TRUE to add the list of units pointing
  towards their variable being intensive.

- skipBunkers:

  set to TRUE to skip AR6 variables that contain bunkers only at the
  global level

- intensiveUnits:

  intensive units where the global value should not be the sum, but
  instead lie between the regional values. Set to TRUE to get list of
  units pointing towards their variable being intensive. You can also
  use c(TRUE, "additionalunit").

- absDiff:

  threshold for absolute difference between parent variable and
  summation

- relDiff:

  threshold (in percent) for relative difference between parent variable
  and summation

## Author

Falk Benke

## Examples

``` r
if (FALSE) { # \dontrun{
checkSummationsRegional(
  mifFile = "path/to/file",
  childRegions = c("R5ASIA", "R5LAM", "R5MAF", "R5OECD90+EU", "R5REF"),
  parentRegion = "World",
  variables = c("Final Energy|Industry", "Emissions|CO2|Energy|Demand|Industry")
)
} # }
```
