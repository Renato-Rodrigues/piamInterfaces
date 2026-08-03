# Retrieves latest summation group file for a given project

Retrieves latest summation group file for a given project

## Usage

``` r
getSummations(project = NULL, format = "dataframe")
```

## Arguments

- project:

  name of the project of requested summation group, or summation group
  filename which can be a csv file of a xlsx file where the first sheet
  containing a 'variable' column is expected to have a 'components'
  column as well. If project is a https://files.ece.iiasa.ac.at/\*.xlsx
  URL, it will be automatically downloaded.

- format:

  either "dataframe" or "list", the latter ignores the factor column

## Author

Oliver Richters
