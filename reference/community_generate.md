# Simulate individual measurements for many populations

For a community (i.e. a collection of populations of different species,
or of the same species at different points in time or locations, etc),
simulate individual-level size and metabolic rate measurements.

## Usage

``` r
community_generate(
  community_data_table,
  abundance_column_name = "speciestotal"
)
```

## Arguments

- community_data_table:

  dataframe containing at least one of `AOU`, `scientific_name`, or
  `mean_size` and a column for species abundances

- abundance_column_name:

  character, the name of the column with species abundances. Defaults to
  "speciestotal".

## Value

a dataframe one row per individual, all columns from
`community_data_table`, and additional columns for species attributes.

Specifically:

- `AOU`: the AOU, if provided

- `sim_species_id`: the `sim_species_id` if provided

- `genus`: the genus associated with the AOU if provided, or the genus
  if provided

- `species`: the species associated with the AOU if provided, or the
  species if provided

- `individual_mass`: the simulated body mass (in grams) for this
  individual

- `individual_bmr`: the simulated basal metabolic rate for this
  individual

- `mean_size`: the mean body mass for this species (i.e. the parameter
  used for simulation)

- `sd_size`: the standard deviation of body mass for this species (i.e.
  the parameter used for simulation)

- `abundance`: the number of individuals simulated of this species (i.e.
  parameter used for simulation)

- `sd_method`: the method for finding the standard deviation for body
  mass for this species

- `scientific_name`: the scientific name

## Examples

``` r

demo_community <- community_generate(demo_route_clean)
head(demo_community)
#>   record_id   routedataid countrynum statenum route rpid year count10 count20
#> 1    900000 9009911011994        900       99     1  101 1994       8      12
#> 2    900000 9009911011994        900       99     1  101 1994       8      12
#> 3    900000 9009911011994        900       99     1  101 1994       8      12
#> 4    900000 9009911011994        900       99     1  101 1994       8      12
#> 5    900000 9009911011994        900       99     1  101 1994       8      12
#> 6    900000 9009911011994        900       99     1  101 1994       8      12
#>   count30 count40 count50 stoptotal speciestotal  AOU sim_species_id
#> 1      15      12      15         5           62 4730           4730
#> 2      15      12      15         5           62 4730           4730
#> 3      15      12      15         5           62 4730           4730
#> 4      15      12      15         5           62 4730           4730
#> 5      15      12      15         5           62 4730           4730
#> 6      15      12      15         5           62 4730           4730
#>   individual_mass individual_bmr mean_size  sd_size abundance  sd_method
#> 1        32.85400       126.6242    37.475 3.300613        62 AOU lookup
#> 2        38.31770       141.3036    37.475 3.300613        62 AOU lookup
#> 3        29.43054       117.0691    37.475 3.300613        62 AOU lookup
#> 4        37.45661       139.0321    37.475 3.300613        62 AOU lookup
#> 5        39.52651       144.4677    37.475 3.300613        62 AOU lookup
#> 6        41.26546       148.9713    37.475 3.300613        62 AOU lookup
#>   scientific_name
#> 1 Alauda arvensis
#> 2 Alauda arvensis
#> 3 Alauda arvensis
#> 4 Alauda arvensis
#> 5 Alauda arvensis
#> 6 Alauda arvensis
```
