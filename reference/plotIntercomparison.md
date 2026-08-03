# Model intercomparison plots: area plots based on summation groups, line plots for further variables. Creates a PDF for each model and scenario in the outputDirectory

Model intercomparison plots: area plots based on summation groups, line
plots for further variables. Creates a PDF for each model and scenario
in the outputDirectory

## Usage

``` r
plotIntercomparison(
  mifFile,
  outputDirectory = "output",
  summationsFile = "AR6",
  renameModels = NULL,
  lineplotVariables = TRUE,
  areaplotVariables = TRUE,
  interactive = FALSE,
  mainReg = "World",
  plotby = c("model", "scenario"),
  diffto = NULL,
  yearsBarPlot = c(2030, 2050),
  postfix = format(Sys.time(), "_%Y-%m-%d_%H.%M.%S")
)
```

## Arguments

- mifFile:

  path to the mif or xlsx file to apply summation checks to, or quitte
  object

- outputDirectory:

  path to directory to place one PDF for each model and scenario

- summationsFile:

  in inst/summations folder that describes the required summation
  groups. set to "extractVariableGroups" to extract it automatically
  from data based on \|+\| notation

- renameModels:

  vector with oldname = newname

- lineplotVariables:

  vector with variable names for lineplots or filenames of files
  containing a 'variable' column (or both)

- areaplotVariables:

  vector with variable names for areaplot or filenames of files
  containing a 'variable' column. Only those available in the
  summationsFile can be plotted.

- interactive:

  allows to select various settings interactively: subset of
  c("variable", "model", "scenario", "region", "period", "plotby",
  "diffto", "yearsBarPlot") or set to TRUE to select all of them

- mainReg:

  region name of main region to be passed to mip

- plotby:

  whether you would like to have everything plotted by scenario, model
  and/or onefile. set to NULL to be asked.

- diffto:

  if specified, the difference to this scenario is calculated and
  plotted

- yearsBarPlot:

  years for which bar plots are to be made.

- postfix:

  to the filename, defaults to something like "\_2024-09-05_12.47.28"

## Author

Oliver Richters

## Examples

``` r
if (FALSE) { # \dontrun{
plotIntercomparison(quitte::quitte_example_dataAR6,
                    lineplotVariables = c("Temperature|Global Mean", "Population"))
} # }
```
