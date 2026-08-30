# Draw individuals to make a population.

This is not a user-facing function; it is the random number generator
under-the-hood for
[pop_generate](https://docs.ropensci.org/birdsize/reference/pop_generate.md).

## Usage

``` r
ind_draw(
  species_mean = NA_real_,
  species_sd = NA_real_,
  species_abundance = NA_integer_
)
```

## Arguments

- species_mean:

  mean body size

- species_sd:

  standard deviation of body size

- species_abundance:

  number of individuals to draw

## Value

vector of individuals' simulated body masses
