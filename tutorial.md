# Tutorial

To improve the tutorial, edit [`tutorial.md`](./tutorial.md).

- To understand how to submit to the IIASA database, read this [REMIND
  tutorial](https://github.com/remindmodel/remind/blob/develop/tutorials/13_Submit_to_IIASA_database.md).
- In the following, we differentiate templates (list of variables and
  corresponding units used in a project) and mappings (specifying which
  PIAM variable will be mapped to a project variable).

## Mappings

Mappings found in the
[`inst/mappings`](https://github.com/pik-piam/piamInterfaces/tree/master/inst/mappings)
folder serve to map variables from the PIAM framework to variables
needed for the submission to databases. The mappings are `;`-separated
files, using `#` as comment character, with the following mandatory
columns:

- `variable`: name of the variable in the project template
- `unit`: unit corresponding to `variable`. If the IIASA template has no
  unit, use `unitless`: an empty cell will fail the tests to avoid
  unintentially forgetting units.
- `piam_variable`: name of the variable in REMIND / MAgPIE / EDGE-T etc.
  reporting. Please use `|+|` notation and try to remain consistent with
  a REMIND mif to facilitate debugging for humans, but from a technical
  point of view it is completely irrelevant. You can use
  [`updatePlusUnit()`](./R/updatePlusUnit.R) to update the correct `|+|`
  spelling and the unit based on a model data file.
- `piam_unit`: unit corresponding to `piam_variable`
- `piam_factor`: factor with which the `piam_variable` has to be
  multiplied for units to match

Recommended columns: - `description`: description text defining the
`variable`. Never use `"` and `;` in the text. - `source`: abbreviation
of the PIAM part where the `piam_variable` comes from. Use `B` = Brick,
`C` = MAGICC, `M` = MAgPIE, `R` = REMIND, `S` = SDP postprocessing, `T`
= EDGE-Transport. This column is used to select the variables passed to
[remind2](https://github.com/pik-piam/remind2/blob/master/tests/testthat/test-convGDX2mif.R)
and [coupling
tests](https://github.com/remindmodel/remind/blob/develop/tests/testthat/test_20-coupled.R).
If the variable is not normally reported, add a small `x` after the
model abbreviation for it to be skipped in those tests. New source
abbreviations should be explained here and must be added to
[`inst/sources.csv`](./inst/sources.csv).

Additionally, some mappings use those columns: - `idx`: serial number of
`variable` - `tier`: importance of variable, with 1 being most
important - `comment`: place for internal comments - `interpolation`:
sets the interpolation method for the `variable` (i.e. not
`piam_variable`) (currently only supports `linear`). When set to
`linear`, adds yearly values between 2005 and 2100 through linear
interpolation for the selected output variables. - `piam_weight`:
calculates a weighted average of multiple entries of `piam_variable`.
Provide a different `piam_variable` in this column, and
[`generateIIASASubmission()`](reference/generateIIASASubmission.md) will
split the data on the rows which contain weight pointers, resolve these
weights into numerical values (via a join operation between the
submission and the input data) and then modify the value based on the
weighting. This takes place in the private .resolveWeights method.

### Editing a mapping

You can use a text editor, `R` or a spreadsheet editor to adjust the
mappings.

For `R`, use:

    mappingdata <- getMapping("AR6")
    ... whatever data.frame operations you want ...
    writeMapping(mappingdata, "inst/mappings/mapping_yourproject.csv")

Using `Excel` can be problematic, as it sometimes changes values and
quotation marks, depending on how it is set up. You can easily check if
your setup poses problems by opening one of the mappings in excel,
changing a line, saving it, and then running `git diff`. If only your
changes in the one line are shown/marked (instead of eg all lines being
displayed with changed separators or so), all is fine and you can use
excel to adjust the mapping.

For `LibreOffice Calc`, use these settings:

    Text Import:
      - Character set: Unicode (UTF-8)
      - Separated by: Semicolon.
    Save -> Edit filter settings:
      - Character set: Unicode (UTF-8)
      - Field Delimiter: ;
      - String Delimiter: (none)

The github diff on a large semicolon-separated file is often unreadable.
For a human-readable output, save the old version of the mapping and
run:

    remind2::compareScenConf(fileList = c("oldfile.csv", "mappingfile.csv"), row.names = NULL, expanddata = FALSE)

On the PIK cluster, you can run `comparescenconf mapping_AR6.csv` in the
`inst/mappings` folder and it will compare to a recent `master` version.

After you adjusted the mapping, run `make test` on Linux (incl. the
cluster) or `Rscript -e 'devtools::test(show_report = TRUE)'` on
Windows, and various tests will be performed.

### Renaming a piam_variable

If a variable used as `piam_variable` has to be renamed, please add it
with its `old_name` to
[`inst/renamed_piam_variables.csv`](./inst/renamed_piam_variables.csv).
Like this, if someone arrives with a dataset that contains the old name
but not the new, [`renameOldVariables()`](./R/renameOldVariables.R)
makes sure the data is automatically adjusted.
[`test-renameOldVariables.R`](./tests/testthat/test-renameOldVariables.R)
enforces that the old variable name is not used anywhere in the
mappings. To adjust the mappings automatically, make sure you commit the
current state to be able to reset its results, and then run
`Rscript -e "devtools::load_all(); renameOldInMappings()"`. Check the
`diff` carefully, for example using `comparescenconf`, see above.

### piam_factor and unit checks

While running the tests, an extensive check of the compatibility of
`piam_unit`, `unit` and `piam_factor` is performed in each mapping. It
helps to find mismatches, for example mapping `Mt` to `Gt` with a factor
of `1` or mapping `US$2005` to `US$2017` without accounting for
inflation. These checks are performed using
[`checkUnitFactor()`](./R/checkUnitFactor.R). It first calls
[`areUnitsIdentical()`](./R/areUnitsIdentical.R) where a number of
identical units are specified (such as `Mt CO2` = `Mt CO2eq`, where
`piam_factor` is 1). Then,
[`checkUnitFactor()`](reference/checkUnitFactor.md) compares a list of
accepted factors against the mappings. In case your tests fails,
carefully check whether the `piam_factor` is correct, and if you a
certain, add it to one of the functions so it will be accepted.

### Price indices

While running
[`generateIIASASubmission()`](reference/generateIIASASubmission.md), if
`Price|*|Index` variables are part of the `iiasatemplate` and `Price|*`
is part of the data, the missing price indices will be calculated
automatically by [`priceIndicesIIASA()`](./R/priceIndicesIIASA.R). Price
indices with wrong reference year (the year where the index is 1) are
corrected automatically by [`priceIndicesFix()`](./R/priceIndicesFix.R).

### Creating a new mapping

First consider whether you need a new mapping or whether we can reduce
redundancy. For example, if your project just uses a subset of an
established mapping, using that mapping together with `iiasatemplate` to
filter automatically just the variables you need is sufficient. If you
additionally need some project-specific variables, create a mapping with
just those and combine the mappings for submission, for example calling
`mapping = c("ScenarioMIP", "PRISMA")`.

If you need to set up a new mapping: Since templates contain between
several hundreds and a few thousand variables, relying on existing
mappings can save substantial amounts of work compared to setting up a
new mapping from scratch. Since the template itself is most likely built
based on earlier templates from other projects, chances are good that
existing mappings already provide parts of the required new mapping.
Using `R`, we describe a simple way to create a new mapping
`mapping_NEW.csv` based on existing mappings.

1.  Identify which existing mappings are most relevant for your new
    mapping. Criteria might include the time at which the existing
    mapping was created and the proximity of the templates
    (e.g. follow-up project). If you are unsure, ask your experienced
    colleagues for advice. This provides you with a list of existing
    mappings that is ordered by relevance, say `mapping_OLD1.csv`, … ,
    `mapping_OLD9.csv`.
2.  Use `read.csv2` to get the template as a dataframe `template`.
3.  Looping over the existing mappings in descending order of relevance,
    - use `getMapping` to get the existing mapping `mapping_OLDi` as a
      dataframe,
    - `filter` `mapping_OLDi` for variables which are contained in
      `template` and which have not yet been added to `mapping_NEW`,
    - `left_join` (by variable) the filtered `mapping_OLDi` with
      `template` to add the information from the template (consider
      using `str_to_lower` for case-insensitive matching when filtering
      and joining),
    - `select`/`mutate` the columns of the joined dataframe to keep the
      desired columns for the new mapping (see above for description of
      mandatory and recommended columns),
    - `bind_rows` to `mapping_NEW`
4.  Use [`writeMapping()`](reference/writeMapping.md) to export
    `mapping_NEW` as `mapping_NEW.csv`. It is recommended to make a few
    checks (e.g. by looking at all variables for which the description
    or the unit does not agree between the existing mapping and the
    template).

## Summation checks

Templates often have a structure where some ‘parent’ variable has to be
the sum of its ‘childs’, such as `Emissions|CO|Energy` =
`Emissions|CO|Energy|Demand` + `Emissions|CO|Energy|Supply`. This can be
checked using summation files that are placed in the
[`inst/summations`](https://github.com/pik-piam/piamInterfaces/tree/master/inst/summations)
folder. The first column contains the parent, the second all its childs.
If you want further groups for a single parent, use
`Emissions|CO2|Energy 2` etc. with a single-digit number. The
[`checkSummations()`](./R/checkSummations.R) function allows to check
your data based on a summation file and a mapping, for example like
this:

    d <- generateIIASASubmission("remind.mif", mapping = "ScenarioMIP", outputDirectory = NULL, checkSummation = FALSE)
    checkSummations(d, template = "ScenarioMIP", summationsFile = "ScenarioMIP", outputDirectory = NULL)

You can also simply pass a IIASA snapshot xlsx or csv file to
checkSummations.

A starting point for a new summation file based on a mapping can be
generated like this:

    library(tidyverse); library(piamInterfaces)
    vars <- grep("^Lifetime|^Price|^OM Cost|^Capital Cost", unique(piamInterfaces::getMapping("ScenarioMIP")$variable), invert = TRUE, value = TRUE)
    liste <- mip::extractVariableGroups(vars)
    tbl <- tibble()
    for (l in sort(names(liste))) {
      childs <- grep("\\*$", liste[[l]], invert = TRUE, value = TRUE)
      if (length(childs) > 1) {
        tbl <- rbind(tbl, tibble(parent = l, child = childs, factor = 1), tibble(parent = "", child = "", factor = ""))
      }
    }
    writeMapping(tbl, "summation_group_ScenarioMIP.csv")

This will put all childs into a single summation group, so you will have
to split them up when needed and remove some nonsensical ones.

In REMIND, summation checks can be performed automatically after every
run if added to
[`checkProjectSummations.R`](https://github.com/remindmodel/remind/blob/develop/scripts/output/single/checkProjectSummations.R).

## Model intercomparison plots

- To compare the results of different models, pass as `modeldata` a
  [quitte](https://github.com/pik-piam/quitte/) object or a csv/xlsx
  file. You get a PDF document for each scenario and each model with
  area plots for all the summation groups in `AR6` (or `NAVIGATE`)
  [summation
  files](https://github.com/pik-piam/piamInterfaces/tree/master/inst/summations)
  plus line plots for each variable in the `lineplotVariables` vector
  you supplied. It takes some time, better use a `slurm` job for:

      plotIntercomparison(modeldata, summationsFile = "AR6", lineplotVariables = c("Temperature|Global Mean", "Population"))

- If your `modeldata` is not well filtered such that for example model
  regions are not too different, you can use `interactive = TRUE` which
  allows to select models, regions, scenarios and variables that you
  like in your PDF. As `lineplotVariables`, you can also specify mapping
  names.

      plotIntercomparison(modeldata, summationsFile = "AR6", lineplotVariables = c("AR6", "AR6_NGFS"), interactive = TRUE)
