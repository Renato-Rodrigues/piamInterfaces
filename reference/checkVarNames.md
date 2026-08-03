# checkVariablesNames checks reporting and mappings on inconsistency in variable names

Pass a vector of variable names (including the units if withunits=TRUE)
or a quitte object. Get warnings if inconsistencies are found for the
reporting

## Usage

``` r
checkVarNames(vars, withunits = TRUE)
```

## Arguments

- vars:

  vector with variable names (and units such as "PE (EJ)")

- withunits:

  should the var vector contain units in paranthesis?

## Value

vector with all variables that show issues

## Author

Oliver Richters
