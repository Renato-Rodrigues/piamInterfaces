# Converts data in historical.mif to match project-specific variables and regions so that it can be used for comparison in an intermodel comparison project

Converts data in historical.mif to match project-specific variables and
regions so that it can be used for comparison in an intermodel
comparison project

## Usage

``` r
convertHistoricalData(mif, project, regionMapping = NULL, mainReg = "World")
```

## Arguments

- mif:

  quitte object with historical data or path to historical.mif

- project:

  name of the project, determines the mapping to be loaded

- regionMapping:

  (optional) csv file with mapping of REMIND regions or ISO to project
  regions, must contain two columns: One can be called 'REMIND' or
  'CountryCode' and contains the regions in the data. The second can be
  called 'project_region' or 'RegionCode', to which the first is mapped.
  You can also specify the filename part before the .csv from
  inst/regionmapping

- mainReg:

  if regionMapping is specified, additional main region that is kept as
  is

## Author

Falk Benke

## Examples

``` r
if (FALSE) { # \dontrun{
data <- convertHistoricalData(
  mif = "path/to/historical.mif",
  project = "NAVIGATE",
  regionMapping = "path/to/region_mapping_NAVIGATE.csv"
)
} # }
```
