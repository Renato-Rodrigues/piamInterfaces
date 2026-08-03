# getMapping

Retrieves latest mapping for a given project. Mappings must contain the
columns "variable", "unit", "piam_variable", "piam_unit", "piam_factor".
Mappings are csv files with semicolon as a separator and no quotation
marks around fields, see main README.Rd file

## Usage

``` r
getMapping(project = NULL, requiredColsOnly = FALSE)
```

## Arguments

- project:

  name of requested mapping, or file name pointing to a mapping

- requiredColsOnly:

  whether only the mandatory 5 columns are return set to TRUE if you
  want to concatenate mappings

## Author

Falk Benke, Oliver Richters

## Examples

``` r
if (FALSE) { # \dontrun{
getMapping("ECEMF")
getMapping("/path/to/mapping/file")
} # }
```
