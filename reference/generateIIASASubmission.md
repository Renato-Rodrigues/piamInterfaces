# generateIASASubmission

Generates an IIASA submission from REMIND or MAgPIE runs by applying a
project-specific mapping. The script starts from 'mifs' which can be a
directory with mif files, a vector of files or a quitte object. In
outputDirectory/outputFilename, you will get the data in a joint xlsx or
mif file.

## Usage

``` r
generateIIASASubmission(
  mifs = ".",
  mapping = NULL,
  model = NULL,
  removeFromScen = NULL,
  addToScen = NULL,
  dropRegi = "auto",
  outputDirectory = "output",
  outputFilename = "submission.xlsx",
  logFile = if (is.null(outputFilename)) NULL else paste0(gsub("\\.[a-zA-Z]+$",
    "_log.txt", outputFilename)),
  iiasatemplate = NULL,
  generatePlots = FALSE,
  timesteps = seq(2005, 2100, 1),
  checkSummation = TRUE,
  mappingFile = NULL,
  naAction = "na.omit"
)
```

## Arguments

- mifs:

  path to mif files or directories with mif files of a REMIND run, or
  quitte object

- mapping:

  mapping names such as c("AR6", "AR6_NGFS") or a vector of mapping file
  names. If NULL, the user is asked. Multiple mappings are concatenated.

- model:

  name of model as registered with IIASA

- removeFromScen:

  regular expression to be removed from scenario name (optional).
  Example: '\_d50\|d95'

- addToScen:

  string to be added as prefix to scenario name (optional)

- dropRegi:

  regions to be dropped from output. Default is "auto" which drops
  aggregate regions for REMIND EU21. Set to NULL for none. Set c("auto",
  "World") for dropping EU21 aggregate plus World

- outputDirectory:

  path to directory for the generated submission (default: output). If
  NULL, no files are written and `logFile` and `outputFilename` have no
  effect.

- outputFilename:

  filename of the generated submission. Must be mif or xlsx file. If
  NULL, submission data is returned. If `outputDirectory` is set to
  NULL, this parameter has no effect.

- logFile:

  path to the logfile with warnings as passed to generateMappingfile,
  checkIIASASubmission (default: outputDirectory/submission_log.txt).
  Set to FALSE for none. If `outputDirectory` is set to NULL, this
  parameter has no effect.

- iiasatemplate:

  optional filename of xlsx or yaml file provided by IIASA used to
  delete superfluous variables and adapt units

- generatePlots:

  boolean, whether to generate plots of failing summation checks. Needs
  outputDirectory not NULL.

- timesteps:

  set of timesteps used to filter the data for the submission file. For
  variables that have the 'interpolation' column filled, steps between
  start and end of the data are added.

- checkSummation:

  either TRUE to identify summation files from mapping, or filename, or
  FALSE

- mappingFile:

  has no effect and is only kept for backwards-compatibility

- naAction:

  a function which indicates what should happen when the data contain NA
  values.

## Details

To provide the mapping, two options exist:

- If you want to generate the mapping from one or more mappings from the
  inst/mappings folder, set mapping = c("AR6", "AR6_NGFS") or so.

- Alternatively, you can provide a path or a vector of paths to mapping
  files. If you provide your own mapping files, make sure they follow
  the standard format (see `getTemplate` for more information)

- It is also possible, to mix both options, e.g. c("AR6",
  "/path/to/mapping_file.csv")

In any case, multiple mapping files will be concatenated.

iiasatemplate is a xlsx or yaml file provided by IIASA with the
variable + unit definitions that are accepted in the database. The
function 'priceIndicesIIASA' will be called to calculate price indices
that are missing or with the wrong base year. 'checkIIASASubmission'
will be called to remove all variables that are not accepted in the
database.

For all elements of the parameter mapping that contain a summation file
in inst/summations, the function 'checkSummations' is called to verify
variable summation checks.

To alter the data, you can use those parameters: model, addToScen,
removeFromScen and timesteps.

For a broader overview of the submission process, consult
https://github.com/remindmodel/remind/blob/develop/tutorials/13_Submit_to_IIASA_database.md

## Author

Falk Benke, Oliver Richters

## Examples

``` r
if (FALSE) { # \dontrun{
# Simple use. Generates submission file in output folder:
generateIIASASubmission(
  mifs = "/path/to/REMIMD/mifs",
  model = "REMIND-MAgPIE 2.1-4.2",
  mapping = "NAVIGATE"
)
} # }
```
