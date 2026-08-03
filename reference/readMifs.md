# Pass a character vector containing filenames and directories. Returns data from all files and all '.mif' files in the directories.

Pass a character vector containing filenames and directories. Returns
data from all files and all '.mif' files in the directories.

## Usage

``` r
readMifs(...)
```

## Arguments

- ...:

  path to mif files or directories with mif files of a REMIND run or
  quitte object

## Author

Falk Benke, Oliver Richters

## Examples

``` r
if (FALSE) { # \dontrun{
# Simple use. Generates submission file in output folder:
readMifs(
  mifs = "/path/to/REMIMD/mifs",
)
} # }
```
