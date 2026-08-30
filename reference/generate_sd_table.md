# Generate table of species-level means for the mean and standard deviation of body mass for species in the Breeding Bird Survey

Goes from the `raw_masses` dataframe (included in `bbssize`) of records
of species' mean and (where provided) standard deviation of body mass
from the CRC Handbook (Dunning 2008) to a table of species-level means
for the mean and standard deviation of body mass, incorporating
estimates for missing standard deviation records and resolving taxonomic
updates between the publication of the CRC Handbook and present releases
of the Breeding Bird Survey dataset (Paradieck et al. 2019).

## Usage

``` r
generate_sd_table(raw_size_data)
```

## Arguments

- raw_size_data:

  the `raw_masses` dataframe

## Value

a dataframe of species-level means for mean body size and standard
deviation of body size

## References

- Dunning, J. B. (2008). CRC handbook of avian body masses (2nd ed.).
  CRC Press.

- Pardieck, K. L., Ziolkowski, D. J., Lutmerding, M., Aponte, V., &
  Hudson, M.-A. (2019). North American Breeding Bird Survey Dataset
  1966—2018, version 2018.0. U.S. Geological Survey.
  https://doi.org/10.5066/P9HE8XYJ
