# Estimate parameters for scaling of standard deviation with mean body size

Calculates parameters for a (log-log linear) scaling relationship
between the mean and standard deviation of a species' mean body size.
Given a table of species with known mean and standard deviation body
sizes, fits a linear model of the form
`log(var(body_size)) ~ log(mean(body_size))` and extracts parameter
estimates, which can then be used to estimate the standard deviation of
body mass for a species based only on its mean body mass. See also
Thibault et al. (2011) for this method applied to the Breeding Bird
Survey.

## Usage

``` r
get_sd_parameters(raw_size_data)
```

## Arguments

- raw_size_data:

  dataframe of species' mean and standard deviation body sizes; use the
  included `raw_masses` data table.

## Value

list of `$slope` and `$intercept` from the linear model fit

## References

- Thibault, K. M., White, E. P., Hurlbert, A. H., & Ernest, S. K. M.
  (2011). Multimodality in the individual size distributions of bird
  communities. Global Ecology and Biogeography, 20(1), 145–153.
  https://doi.org/10.1111/j.1466-8238.2010.00576.x
