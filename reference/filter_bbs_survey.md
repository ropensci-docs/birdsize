# Clean raw Breeding Bird Survey survey data

The raw data for the Breeding Bird Survey includes unidentified species
and some species that are not well-sampled by the BBS methods. This
function filters a dataframe to remove those species.

## Usage

``` r
filter_bbs_survey(bbs_survey_data)
```

## Arguments

- bbs_survey_data:

  data frame with columns for species and AOU

## Value

bbs_survey_data with unidentified species, nightbirds, waterbirds,
non-targets removed

## Examples

``` r
head(filter_bbs_survey(demo_route_raw))
#>   record_id   routedataid countrynum statenum route rpid year  AOU count10
#> 1    900000 9009911011994        900       99     1  101 1994 4730       8
#> 2    900001 9009911011995        900       99     1  101 1995 4730      13
#> 3    900002 9009911011996        900       99     1  101 1996 4730       8
#> 4    900003 9009911011997        900       99     1  101 1997 4730       9
#> 5    900004 9009911011998        900       99     1  101 1998 4730      10
#> 6    900005 9009911011999        900       99     1  101 1999 4730      12
#>   count20 count30 count40 count50 stoptotal speciestotal
#> 1      12      15      12      15         5           62
#> 2       9      11      10      10         5           53
#> 3      11       9      13      15         5           56
#> 4      13      16       9      12         5           59
#> 5       6      12       8       7         5           43
#> 6      13       5       9       5         5           44
```
