# Provide information on variable, its mappings and summation groups

Provide information on variable, its mappings and summation groups

## Usage

``` r
variableInfo(varname, mif = NULL, mapping = NULL)
```

## Arguments

- varname:

  string with variable name

- mif:

  filename of miffile

- mapping:

  vector of mapping shortcuts (AR6, NAVIGATE) or mapping filenames. NULL
  means all

## Value

prints human-readable summary to the user

## Author

Oliver Richters

## Examples

``` r
# Simple use. prints human-readable summary to the reader on Emi|CO2:
variableInfo(
  "Emi|CO2"
)
#> 
#> ##### Search for information on Emi|CO2 in mappings
#> 
#> ### Nothing found in mapping: AR6
#> 
#> ### Nothing found in mapping: AR6_MAgPIE
#> 
#> ### Nothing found in mapping: AR6_NGFS
#> 
#> ### Nothing found in mapping: ARIADNE
#> 
#> ### Nothing found in mapping: AgMIP
#> 
#> ### Nothing found in mapping: BTC2
#> 
#> ### Nothing found in mapping: EC
#> 
#> ### Nothing found in mapping: ECEMF
#> 
#> ### Nothing found in mapping: ELEVATE
#> 
#> ### Nothing found in mapping: ESABCC
#> 
#> ### Nothing found in mapping: MAGICC7_AR6
#> 
#> ### Nothing found in mapping: NAVIGATE
#> 
#> ### Nothing found in mapping: NAVIGATE_coupled
#> 
#> ### Nothing found in mapping: NGFS6
#> 
#> ### Nothing found in mapping: PRISMA
#> 
#> ### Nothing found in mapping: SHAPE
#> 
#> ### Nothing found in mapping: ScenarioMIP
#> 
#> ### Nothing found in mapping: ScenarioMIP_historical
#> 
#> ### Nothing found in mapping: SusMIP
#> 
#> ### Nothing found in mapping: climateassessment
#> 
#> ### Renaming found in renamed_piam_variables.csv:
#> - Emi|CO2 -> Emi|CO2|w/o Bunkers
#> - Emi|CO -> Emi|CO|w/ Bunkers
```
