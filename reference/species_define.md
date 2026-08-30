# Define a species

Creates a list with taxonomic/identifying information and parameters for
mean and standard deviation of body mass.

## Usage

``` r
species_define(
  AOU = NA_integer_,
  scientific_name = NA_character_,
  mean_size = NA_real_,
  sd_size = NA_real_,
  sim_species_id = 1
)
```

## Arguments

- AOU:

  the numeric AOU code used for this species in the Breeding Bird Survey

- scientific_name:

  the species' scientific name, as "Genus species"

- mean_size:

  mean body size

- sd_size:

  sd of body size

- sim_species_id:

  identifier; if using taxonomic info, defaults to AOU. If not, defaults
  to 1. Supplying other values can be useful for simulation models.

## Value

list with species parameter information

## Details

The identifying information used depends on which parameters are
provided, with the following order of preference: AOU \> scientific name
\> user provided mean and sd \> user provided mean and estimated sd.

## Examples

``` r
species_define(AOU = 2881)
#> $AOU
#> [1] 2881
#> 
#> $scientific_name
#> [1] "Perdix perdix"
#> 
#> $mean_size
#> [1] 405.5
#> 
#> $sd_size
#> [1] 31
#> 
#> $sd_method
#> [1] "AOU lookup"
#> 
#> $sim_species_id
#> [1] 2881
#> 
species_define(scientific_name = "Perdix perdix")
#> $AOU
#> [1] 2881
#> 
#> $scientific_name
#> [1] "Perdix perdix"
#> 
#> $mean_size
#> [1] 405.5
#> 
#> $sd_size
#> [1] 31
#> 
#> $sd_method
#> [1] "Scientific name lookup"
#> 
#> $sim_species_id
#> [1] 2881
#> 
species_define(mean_size = 400, sd_size = 30)
#> $AOU
#> [1] NA
#> 
#> $scientific_name
#> [1] NA
#> 
#> $mean_size
#> [1] 400
#> 
#> $sd_size
#> [1] 30
#> 
#> $sd_method
#> [1] "Mean and SD provided"
#> 
#> $sim_species_id
#> [1] 1
#> 
species_define(mean_size = 400)
#> $AOU
#> [1] NA
#> 
#> $scientific_name
#> [1] NA
#> 
#> $mean_size
#> [1] 400
#> 
#> $sd_size
#> [1] 28.55916
#> 
#> $sd_method
#> [1] "SD estimated from mean"
#> 
#> $sim_species_id
#> [1] 1
#> 
```
