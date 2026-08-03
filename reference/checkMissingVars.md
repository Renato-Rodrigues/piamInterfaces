# Check whether all variables required by mapping are present in mifdata for given source

Check whether all variables required by mapping are present in mifdata
for given source

## Usage

``` r
checkMissingVars(mifdata, mapping = TRUE, sources = TRUE)
```

## Arguments

- mifdata:

  data that can be read with as.quitte

- mapping:

  name of the project of requested mappings such as c('AR6', 'AR6_NGFS')
  or 'mapping.csv'. Use TRUE for all mappings.

- sources:

  model abbreviation(s) used in 'source' column. R = REMIND, M = MAgPIE,
  T = EDGE-T, B = Brick, C = Climate/MAGICC, TRUE = all

## Value

an invisible vector with missing variables

## Author

Oliver Richters
