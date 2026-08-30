# species

The `species_define` function works mostly behind the scenes to set up
the parameters needed to simulate individual body size measurements.
Given any of: (1) the [AOU as used in the North American Breeding Bird
Survey](https://www.pwrc.usgs.gov/bbs/specieslist.html) (Pardieck et
al. 2019), (2) the scientific name, (3) the species’ mean body size, or
(4) the species’ mean *and standard deviation* body size,
`species_define` returns the parameters used by `pop_generate` and
`community_generate` to simulate individual size measurements for
individuals of that species, or returns an error message asking for more
or different information. In most instances, `species_define` is called
under-the-hood by the `generate` functions, and users do not need to
interact with it directly.

## Species known to `birdsize`

`birdsize` includes species-level parameters for 443 species of birds
common in the North American Breeding Bird Survey. To view the list of
species included, examine the `known_species` data table, included:

``` r

head(known_species)
#> # A tibble: 6 × 3
#>     AOU genus      species    
#>   <int> <chr>      <chr>      
#> 1  2881 Perdix     perdix     
#> 2  2882 Alectoris  chukar     
#> 3  2890 Colinus    virginianus
#> 4  2920 Oreortyx   pictus     
#> 5  2930 Callipepla squamata   
#> 6  2940 Callipepla californica
```

Species included in `known_species` can be retrieved via either their
AOU or scientific name. For example, the hummingbird *Selasphorous
calliope* has an AOU of `4360`.

### AOU lookup

``` r

hummingbird_AOU_parameters <- species_define(AOU = 4360)

hummingbird_AOU_parameters
#> $AOU
#> [1] 4360
#> 
#> $scientific_name
#> [1] "Selasphorus calliope"
#> 
#> $mean_size
#> [1] 2.65
#> 
#> $sd_size
#> [1] 0.1818394
#> 
#> $sd_method
#> [1] "AOU lookup"
#> 
#> $sim_species_id
#> [1] 4360
```

### Scientific name lookup

``` r

hummingbird_name_parameters <- species_define(scientific_name = "Selasphorus calliope")

hummingbird_name_parameters
#> $AOU
#> [1] 4360
#> 
#> $scientific_name
#> [1] "Selasphorus calliope"
#> 
#> $mean_size
#> [1] 2.65
#> 
#> $sd_size
#> [1] 0.1818394
#> 
#> $sd_method
#> [1] "Scientific name lookup"
#> 
#> $sim_species_id
#> [1] 4360
```

Note that the `sd_method` field tells us which method we used to look up
the parameters. This field propagates throughout the `pop_generate` and
`community_generate` functions to keep track of the underlying
methodology.

### Unknown species or AOUs

Attempting to use `species_define` with an AOU or species not known to
`birdsize` will return an error:

``` r

try(species_define(AOU = 100))
#> Error in species_lookup(AOU = AOU) : `AOU` is invalid.
```

``` r

try(species_define(scientific_name = "Swiftus Taylor"))
#> Error in species_lookup(scientific_name = scientific_name) : 
#>   Scientific name is invalid.
```

## Species not known to `birdsize`

Some users may want to use this methodology with species not included in
`known_species`, or to use different species-level parameters than those
built-in to `birdsize` (for example, to explore intraspecific variation
in body size over time or space). To do this, supply `species_define`
with mean, or mean and standard deviation, values for each species. To
help keep track of species-parameter matches, use the `sim_species_id`
field to assign a species identifier to each novel species.

### Manually supplying species parameters

Suppose we want to work with a hypothetical species with a mean body
size of 40g and a standard deviation of 2.5. Because this species
doesn’t have a scientific name or AOU included in `birdsize`, we label
it using the arbitrary `sim_species_id` of 1.

``` r

hypothetical_species_parameters <- species_define(mean_size = 40, sd_size = 2.5, sim_species_id = 1)

hypothetical_species_parameters
#> $AOU
#> [1] NA
#> 
#> $scientific_name
#> [1] NA
#> 
#> $mean_size
#> [1] 40
#> 
#> $sd_size
#> [1] 2.5
#> 
#> $sd_method
#> [1] "Mean and SD provided"
#> 
#> $sim_species_id
#> [1] 1
```

This can be particularly useful when working with multiple new species.
For example, if we have 3 new species, we can store their information in
a separate table and iterate over `sim_species_id` to generate
parameters for each species. This happens under the hood in
`community_generate`.

``` r

multiple_species_info <- data.frame(
  mean_size = c(10, 40, 50),
  sd_size = c(1, 2.5, 3),
  sim_species_id = 1:3
)


pmap_df(multiple_species_info, species_define)
#> # A tibble: 3 × 6
#>     AOU scientific_name mean_size sd_size sd_method            sim_species_id
#>   <int> <chr>               <dbl>   <dbl> <chr>                         <int>
#> 1    NA NA                     10     1   Mean and SD provided              1
#> 2    NA NA                     40     2.5 Mean and SD provided              2
#> 3    NA NA                     50     3   Mean and SD provided              3
```

If the standard deviation is not provided, `species_define` will
estimate it (see the `scaling` vignette):

``` r

multiple_species_info_no_sd <- data.frame(
  mean_size = c(10, 40, 50),
  sim_species_id = 1:3
)


pmap_df(multiple_species_info_no_sd, species_define)
#> # A tibble: 3 × 6
#>     AOU scientific_name mean_size sd_size sd_method              sim_species_id
#>   <int> <chr>               <dbl>   <dbl> <chr>                           <int>
#> 1    NA NA                     10   0.693 SD estimated from mean              1
#> 2    NA NA                     40   2.80  SD estimated from mean              2
#> 3    NA NA                     50   3.51  SD estimated from mean              3
```

## Order of operations

If multiple sets of information are provided (e.g. both `AOU` and
`scientific_name`), `species_define` will use it in this order of
preference:

1.  AOU
2.  Scientific name
3.  Manually provided mean and standard deviation
4.  Manually provided mean and estimated standard deviation

## References

Pardieck, K.L., Ziolkowski Jr., D.J., Lutmerding, M., Aponte, V., and
Hudson, M-A.R., 2019, North American Breeding Bird Survey Dataset 1966 -
2018 (ver. 2018.0): U.S. Geological Survey, Patuxent Wildlife Research
Center, <https://doi.org/10.5066/P9HE8XYJ>.
