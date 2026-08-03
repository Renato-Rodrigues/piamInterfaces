# Checks for a run if it is correctly fixed on the reference run for t \< startyear

Checks for a run if it is correctly fixed on the reference run for t \<
startyear

## Usage

``` r
fixOnRef(
  data,
  refscen,
  startyear,
  ret = "boolean",
  failfile = NULL,
  relDiff = 1e-12
)
```

## Arguments

- data:

  quitte object or mif file

- refscen:

  scenario name of reference scenario, or file or quitte object with
  reference data

- startyear:

  first time step for which scenarios and reference scenario are
  expected to differ

- ret:

  "boolean": just return TRUE/FALSE if check was successful "fails":
  data frame with mismatches between scenario and reference data
  "fixed": quitte object with data correctly fixed on reference data
  "TRUE_or_fixed": TRUE if check was successful, fixed object otherwise

- failfile:

  csv file to which mismatches are written to

- relDiff:

  threshold for acceptable relative difference

## Value

see parameter 'ret'

## Author

Oliver Richters
