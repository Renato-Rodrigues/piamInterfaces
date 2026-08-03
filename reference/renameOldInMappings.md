# renameOldInMappings

Loads "renamed_piam_variables.csv" and replaces all instances of
old_name in the piam_variable columns of all mapping files Handle with
care, better commit your changes before using it Best run this in your
piamInterfaces folder: Rscript -e 'devtools::load_all();
renameOldInMappings()'

## Usage

``` r
renameOldInMappings(folder = ".")
```

## Arguments

- folder:

  piamInterfaces folder

## Author

Oliver Richters
