# Reconcile taxonomic updates between 2008 and 2019

Six species have undergone name changes or other minor taxonomic
rearrangements between 2008 and 2019, resulting in name mismatches
between data from the Breeding Bird Survey (Paradieck et al. 2019) and
the CRC Handbook (Dunning 2008). This function resolves those mismatches
such that all species in the Breeding Bird Survey are associated with
the appropriate size records from the CRC Handbook.

## Usage

``` r
clean_sp_size_data(raw_size_data)
```

## Arguments

- raw_size_data:

  dataframe of species' mean and standard deviation body sizes; use the
  included `raw_masses` data table.

## Value

dataframe of species' mean and standard deviation body sizes, with name
mismatches resolved.

## References

- Dunning, J. B. (2008). CRC handbook of avian body masses (2nd ed.).
  CRC Press.

- Pardieck, K. L., Ziolkowski, D. J., Lutmerding, M., Aponte, V., &
  Hudson, M.-A. (2019). North American Breeding Bird Survey Dataset
  1966—2018, version 2018.0. U.S. Geological Survey.
  https://doi.org/10.5066/P9HE8XYJ
