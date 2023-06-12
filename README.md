
# Opportunistic: Routing Distribution, Broadcasts, Transmissions and Receptions in an Opportunistic Network

This repository contains the Opportunistic R package, which provides
user-friendly functions to access the methods proposed in the research
work titled “A novel theoretical probabilistic model for opportunistic
routing with applications in energy consumption for WSNs” by Galarza et
al. (2021) \[1\].

## Installation

To use the Opportunistic R package, you need to have R software
installed on your system. If you don’t have it, you can download it from
the [R project website](https://cloud.r-project.org/). Alternatively,
you can compile R online using platforms such as [RStudio
cloud](https://rstudio.cloud/) or [Google Colab](https://colab.to/r).

Once you have R installed, you can install the Opportunistic package by
running the following code in the R console:

``` r
# Install from CRAN
library(Opportunistic)

# Or the development version from GitHub
# install.packages("devtools")
devtools::install_github("chedgala/Opportunistic")
```

## Usage

After installing the package, you can load it using the following
command:

``` r
library(Opportunistic)
```

The package provides three main functions:

1.  `routes(p, delta)`: This function returns the different possible
    routes, their frequency, and their respective probabilities when
    considering uncertain probabilities lying on the interval
    `p ± delta`. It is based on the theoretical framework developed in
    the research work.

2.  `Expected(p)`: This function calculates the probability of
    successful transmissions and the expected number of transmissions,
    receptions, and broadcasts for the given vector of probabilities
    `p`.

3.  `MonteCarlo(p, M)`: This function estimates the probability of
    successful transmissions, as well as the expected number of
    transmissions, receptions, and broadcasts using Monte Carlo
    simulations. The parameter `M` specifies the number of simulations
    to perform.

For more information on the usage and capabilities of the Opportunistic
R package, please refer to the package documentation and the original
research work \[1\].

## Tutorial

En esta sección se muestra cómo acceder a los métodos propuestos en este
trabajo a través de funciones de usuario disponibles.

``` r
library(Opportunistic)
#An N=5 Opportunistic system with probabilities
p <- c(0.85, 0.72, 0.50, 0.28, 0.05)
routes(p) # routes distribution

           Freq Probability   Value
route 1       1        p1^5 0.44371
route 2       4     p1^3*p2 0.44217
route 3       3     p1*p2^2 0.44064
route 4       3     p1^2*p3 0.36125
route 5       2       p2*p3    0.36
route 6       2       p1*p4   0.238
route 7       1          p5    0.05
Total        16
```

``` r
#An N=5 Opportunistic system with probabilities
p <- c(0.85, 0.72, 0.50, 0.28, 0.05)
True = Expected(p)

###########################################
Opportunistic Model - Theoretical results
###########################################

Number of Hops N:   5
Probabilities:      0.85, 0.72, 0.5, 0.28, 0.05

                       1     2     3       4     5
Success Probability 0.85 0.922 0.958  0.974  0.979
Exp Transmissions   1.00 2.850 6.143 11.773 21.135
Exp Receptions      0.85 2.293 4.631  8.362 14.226
Exp Broadcast       1.00 1.850 3.293  5.631  9.362
```

``` r
#An N=5 Opportunistic system with probabilities 
p <- c(0.85, 0.72, 0.50, 0.28, 0.05)
> Estimated = MonteCarlo(p,M=10^6)

###########################################
Opportunistic Model - Monte Carlo results
###########################################

Number of Hops N:   5
Probabilities:      0.85, 0.72, 0.5, 0.28, 0.05
Simulations M:      1e+06

|===========================================| 100%

Monte Carlo
Probability System       0.979
Exp Transmissions       21.129
Exp Receptions          14.220
Exp Broadcast            9.358
```

## Authors

The Opportunistic R package was developed by Christian E. Galarza
(maintainer) and Jonathan M. Palma.

## Contributions

Contributions to the software are welcome. If you find a bug or have an
idea for an enhancement, please open an issue or submit a pull request.

## Contact

If you have any questions, feel free to open an issue or send an email
to the repository owner.

## License

This software is open source under the MIT License. Please see the
LICENSE file for more information.

### References

\[1\] Galarza, C. E., Palma, J. M., Morais, C. F., Utria, J., Carvalho,
L. P., Bustos, D., & Oliveira, R. C. (2021). A novel theoretical
probabilistic model for opportunistic routing with applications in
energy consumption for WSNs. Sensors, 21(23), 8058.
