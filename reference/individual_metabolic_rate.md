# Estimate individual-level BMR

Given an individual's body mass (in grams), use allometric scaling
(Fristoe 2015) to estimate basal metabolic rate.

## Usage

``` r
individual_metabolic_rate(mass)
```

## Arguments

- mass:

  mass in grams

## Value

estimated basal metabolic rate

## References

- Fristoe, T. S. (2015). Energy use by migrants and residents in North
  American breeding bird communities. Global Ecology and Biogeography,
  24(4), 406–415. https://doi.org/10.1111/geb.12262

## Examples

``` r
individual_metabolic_rate(10)
#> [1] 54.22372
```
