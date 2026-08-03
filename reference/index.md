# Package index

## All functions

- [`areUnitsIdentical()`](areUnitsIdentical.md) : Check whether units
  are identical following a specified list

- [`checkFixUnits()`](checkFixUnits.md) : Check units in IIASA
  submission by comparing mifdata to a project template

- [`checkIIASASubmission()`](checkIIASASubmission.md) : Check IIASA
  submission by comparing mif data to a template file (xlsx or yaml)
  provided by IIASA

- [`checkMissingVars()`](checkMissingVars.md) : Check whether all
  variables required by mapping are present in mifdata for given source

- [`checkNGFS()`](checkNGFS.md) : Check NGFS submission by comparing mif
  data to a template file (xlsx or yaml) provided by IIASA

- [`checkSummations()`](checkSummations.md) : Checks for a run if the
  variables sum up as expected and logs spotted gaps

- [`checkSummationsRegional()`](checkSummationsRegional.md) : Checks for
  a run if the regions for selected variables sum up as expected

- [`checkUnitFactor()`](checkUnitFactor.md) : Check unit factor in
  template

- [`checkVarNames()`](checkVarNames.md) : checkVariablesNames checks
  reporting and mappings on inconsistency in variable names

- [`convertHistoricalData()`](convertHistoricalData.md) : Converts data
  in historical.mif to match project-specific variables and regions so
  that it can be used for comparison in an intermodel comparison project

- [`extractReferenceYear()`](extractReferenceYear.md) : Extract
  reference year for price indices from unit

- [`fillMissingSummations()`](fillMissingSummations.md) : Recursively
  calculate additional variables based on given summations and add them
  to the given mif file

- [`fillSummationPairs()`](fillSummationPairs.md) : add missing variable
  values if the value can be obtained from two other reported results.

- [`fixOnRef()`](fixOnRef.md) : Checks for a run if it is correctly
  fixed on the reference run for t \< startyear

- [`generateIIASASubmission()`](generateIIASASubmission.md) :
  generateIASASubmission

- [`getMapping()`](getMapping.md) : getMapping

- [`getMappingVariables()`](getMappingVariables.md) : Retrieves all
  variables allocated to source potentially used in mappings to project
  variables

- [`getREMINDTemplateVariables()`](getREMINDTemplateVariables.md) :
  legacy function to be used by remind2

- [`getSummations()`](getSummations.md) : Retrieves latest summation
  group file for a given project

- [`getTemplate()`](getTemplate.md) : for backwards compatibility

- [`loadIIASATemplate()`](loadIIASATemplate.md) : Loads IIASA template
  (xlsx or yaml)

- [`mappingNames()`](mappingNames.md) : Retrieves mapping file names

- [`piamInterfaces`](piamInterfaces-package.md)
  [`piamInterfaces-package`](piamInterfaces-package.md) :
  piamInterfaces: Project specific interfaces to REMIND / MAgPIE

- [`plotIntercomparison()`](plotIntercomparison.md) : Model
  intercomparison plots: area plots based on summation groups, line
  plots for further variables. Creates a PDF for each model and scenario
  in the outputDirectory

- [`priceIndicesAdd()`](priceIndicesAdd.md) : Add price index

- [`priceIndicesFix()`](priceIndicesFix.md) : Fixes price indices with
  wrong reference year

- [`priceIndicesIIASA()`](priceIndicesIIASA.md) :

  Add Price\|*\|Index variables requested in iiasatemplate but missing
  in data, if Price\|* is present in data. Extracts reference year
  automatically from unit

- [`readMifs()`](readMifs.md) : Pass a character vector containing
  filenames and directories. Returns data from all files and all '.mif'
  files in the directories.

- [`removePlus()`](removePlus.md) : Remove \|+\|, \|++\| etc. from
  variable names

- [`renameOldInMappings()`](renameOldInMappings.md) :
  renameOldInMappings

- [`renameOldVariables()`](renameOldVariables.md) : add variables that
  are missing based on a list of formulas

- [`setLogFile()`](setLogFile.md) : Generate valid path to logFile and
  make sure the outputDirectory exists. If logFile is just a file name
  without any further path info, put logFile in outputDirectory

- [`sumNamesWithFactors()`](sumNamesWithFactors.md) : From mappingData,
  return the piam_variable sum as a string for a given exportname

- [`summationsNames()`](summationsNames.md) : Retrieves summation group
  file names

- [`templateNames()`](templateNames.md) : for backwards compatibility

- [`updatePlusUnit()`](updatePlusUnit.md) : updatePlusUnit

- [`variableInfo()`](variableInfo.md) : Provide information on variable,
  its mappings and summation groups

- [`writeMapping()`](writeMapping.md) : writeMapping
