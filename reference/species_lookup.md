# Species lookup

Given either AOU or scientific name, looks up a species' taxonomic
information and mean and standard deviation of body size in
[sd_table](https://docs.ropensci.org/birdsize/reference/sd_table.md).

## Usage

``` r
species_lookup(AOU = NA_integer_, scientific_name = NA_character_)
```

## Arguments

- AOU:

  the numeric AOU code used for this species in the Breeding Bird Survey

- scientific_name:

  the species' scientific name, as "Genus species"

## Value

data frame with columns AOU, genus, species, mean_mass, mean_sd,
contains_estimates, scientific_name

## Examples

``` r
species_lookup(AOU = 2881)
#>     AOU  genus species mean_mass mean_sd contains_estimates scientific_name
#> 51 2881 Perdix  perdix     405.5      31              FALSE   Perdix perdix
species_lookup(scientific_name = "Selasphorus calliope")
#>      AOU       genus  species mean_mass   mean_sd contains_estimates
#> 163 4360 Selasphorus calliope      2.65 0.1818394               TRUE
#>          scientific_name
#> 163 Selasphorus calliope
```
