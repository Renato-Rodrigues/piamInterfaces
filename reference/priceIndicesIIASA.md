# Add Price\|*\|Index variables requested in iiasatemplate but missing in data, if Price\|* is present in data. Extracts reference year automatically from unit

Add Price\|*\|Index variables requested in iiasatemplate but missing in
data, if Price\|* is present in data. Extracts reference year
automatically from unit

## Usage

``` r
priceIndicesIIASA(mifdata, iiasatemplate, scenBase = NULL)
```

## Arguments

- mifdata:

  file or data that can be converted into quitte object

- iiasatemplate:

  filename of xlsx or yaml file provided by IIASA

- scenBase:

  optional scenario name of baseline scenario used to calculate index

## Author

Oliver Richters
