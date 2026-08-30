# Raw data for a hypothetical Breeding Bird Survey route.

A toy dataset for use in vignettes and function testing. It contains all
the same column names as would be expected for a Breeding Bird survey
route dataset downloaded, e.g. from ScienceBase or the Data Retriever
(Pardieck et al. 2019). However, the actual data values are simulated
data.

## Usage

``` r
demo_route_raw
```

## Format

A data frame with 1160 rows and 15 variables:

- record_id:

  inherited from data downloaded through the Data Retriever

- routedataid:

  inherited from Pardieck et al. 2018 (as are all following fields).
  Unique data identification number.

- countrynum:

  inherited. Three-digit numerical code for country. In these data, the
  toy countrynum is 900.

- statenum:

  inherited. Two-digit numerical code for state, province, or territory.
  For these data, the toy number is 99.

- route:

  inherited. Three-digit code identifying the route, unique within
  states. For this dataset, 1.

- rpid:

  inherited. Three-digit run protocol identifier. Here, set to 101.

- year:

  inherited. Four-digit year of the survey.

- AOU:

  inherited. Five-digit species identification number.

- count10:

  inherited. Total individuals of the species recorded on stops 1-10.

- count20:

  inherited. Total individuals of the species recorded on stops 11-20.

- count30:

  inherited. Total individuals of the species recorded on stops 21-30.

- count40:

  inherited. Total individuals of the species recorded on stops 31-40.

- count50:

  inherited. Total individuals of the species recorded on stops 40-50.

- stoptotal:

  inherited. Total number of stops (of 50), where the species was
  recorded.

- speciestotal:

  inherited. Total individuals of the species recorded across the entire
  run of the route (sum of stops).

## Details

Nearly all column names are inherited from Pardieck et al. (2019) and
are further explained in the Files and Fields Definitions document
included as part of the Breeding Bird Survey data release.

## References

- Pardieck, K. L., Ziolkowski, D. J., Lutmerding, M., Aponte, V., &
  Hudson, M.-A. (2019). North American Breeding Bird Survey Dataset
  1966—2018, version 2018.0. U.S. Geological Survey.
  https://doi.org/10.5066/P9HE8XYJ
