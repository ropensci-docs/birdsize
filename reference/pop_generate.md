# Simulate body masses for a population

Draws body mass measurements for a population of birds (of all the same
species) given the population size and either (1) the species AOU or (2)
the mean and potentially standard deviation of body mass for that
species.

## Usage

``` r
pop_generate(
  abundance = NA_integer_,
  AOU = NA_integer_,
  scientific_name = NA_character_,
  mean_size = NA_real_,
  sd_size = NA_real_,
  sim_species_id = 1
)
```

## Arguments

- abundance:

  integer number of individuals to draw. *Required*.

- AOU:

  the numeric AOU code used for this species in the Breeding Bird Survey

- scientific_name:

  as "Genus species"

- mean_size:

  numeric, mean body mass (in grams) for this species.

- sd_size:

  numeric, standard deviation of body mass for this species.

- sim_species_id:

  defaults AOU or 1

## Value

a dataframe with `abundance` rows - one record per individual - and
columns for species attributes.

Specifically:

- `AOU`: the AOU, if provided

- `sim_species_id`: the `sim_species_id` if provided

- `scientific_name`: the scientific name if provided

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

## Details

`abundance` is required, as well as *one of*: `AOU`, `scientific_name`,
or `mean_size`.

## Examples

``` r

pop_generate(abundance = 5, AOU = 2881)
#>    AOU sim_species_id individual_mass individual_bmr mean_size sd_size
#> 1 2881           2881        426.2986       787.3636     405.5      31
#> 2 2881           2881        406.4596       761.0596     405.5      31
#> 3 2881           2881        478.9239       855.4986     405.5      31
#> 4 2881           2881        485.6594       864.0600     405.5      31
#> 5 2881           2881        443.0807       809.3410     405.5      31
#>   abundance  sd_method scientific_name
#> 1         5 AOU lookup   Perdix perdix
#> 2         5 AOU lookup   Perdix perdix
#> 3         5 AOU lookup   Perdix perdix
#> 4         5 AOU lookup   Perdix perdix
#> 5         5 AOU lookup   Perdix perdix
pop_generate(abundance = 5, scientific_name = "Selasphorus calliope")
#>    AOU sim_species_id individual_mass individual_bmr mean_size   sd_size
#> 1 4360           4360        2.422483       19.73182      2.65 0.1818394
#> 2 4360           4360        2.722784       21.44637      2.65 0.1818394
#> 3 4360           4360        2.819967       21.98939      2.65 0.1818394
#> 4 4360           4360        2.564050       20.54726      2.65 0.1818394
#> 5 4360           4360        2.937854       22.64096      2.65 0.1818394
#>   abundance              sd_method      scientific_name
#> 1         5 Scientific name lookup Selasphorus calliope
#> 2         5 Scientific name lookup Selasphorus calliope
#> 3         5 Scientific name lookup Selasphorus calliope
#> 4         5 Scientific name lookup Selasphorus calliope
#> 5         5 Scientific name lookup Selasphorus calliope
pop_generate(abundance = 5, mean_size = 20, sd_size = 3)
#>   AOU sim_species_id individual_mass individual_bmr mean_size sd_size abundance
#> 1  NA              1        21.79326       94.49592        20       3         5
#> 2  NA              1        21.39825       93.27152        20       3         5
#> 3  NA              1        17.76690       81.68877        20       3         5
#> 4  NA              1        22.87717       97.82347        20       3         5
#> 5  NA              1        20.45791       90.33029        20       3         5
#>              sd_method scientific_name
#> 1 Mean and SD provided            <NA>
#> 2 Mean and SD provided            <NA>
#> 3 Mean and SD provided            <NA>
#> 4 Mean and SD provided            <NA>
#> 5 Mean and SD provided            <NA>
```
