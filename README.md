# movement

[![Build Status](https://travis-ci.org/SEEG-Oxford/movement.svg?branch=master)](https://travis-ci.org/SEEG-Oxford/movement)
[![codecov.io](https://codecov.io/github/SEEG-Oxford/movement/coverage.svg?branch=master)](https://codecov.io/github/SEEG-Oxford/movement?branch=master)

## R package containing useful functions for the analysis of movement data in disease modelling and mapping

This package is a collaborative effort between a group of researchers to foster research into the analysis of human and animal movement for epidemiology. It's still in the very early stages of development, so expect the content to change a great deal in the future.

### installing and loading the package

You can install the package from github with [devtools package][devtools]:

```
devtools::install_github('SEEG-Oxford/movement')
library(movement)
```

### Usage

The most common use of the package is to parameterize a movement model based on observed population movements, and then use this model to predict _de novo_ population movements.

```
m <- movement(locations = df_locations$location, coords = df_locations[, c('lon','lat')], population = df_locations$pop, movement_matrix = observed, model = 'radiation with selection')
```
Where df_locations is a data.frame containing location, lon, lat and pop columns corresponding to location ids, coordinates and populations respectively. movement_matrix is a square matrix of observed population movements between the location_ids, and model is the selected movement model (valid models are radiation with selection, original radiation, gravity, intervening opportunities and uniform selection).

This returns an optimisedmodel object which can be used by predict() to predict population movements from a RasterLayer, or a dataframe formatted as df_locations above.

```
prediction <- predict(m, raster)
prediction <- predict(m, df_locations)
```

### Contributors

[Nick Golding][Nick] @ [Spatial Ecology and Epidemiology Group, Oxford][seeg]

Andrew Schofield @ [Tessella][tessella]

Moritz Kraemer @ [Spatial Ecology and Epidemiology Group, Oxford][seeg]

### Reporting Bugs

You can report bugs, issues and suggestions for extra functions using the issues button on the right hand side of this page.


#### Funding

Development of this software package is partly funded by the Research for Health in Humanitarian Crises (R2HC) Programme, managed by ELRHA. The Research for Health in Humanitarian Crises (R2HC) programme aims to improve health outcomes by strengthening the evidence base for public health interventions in humanitarian crises. Visit www.elrha.org/work/r2hc for more information. The £8 million R2HC programme is funded equally by the Wellcome Trust and DFID, with Enhancing Learning and Research for Humanitarian Assistance (ELRHA) overseeing the programme’s execution and management.

[Nick]: http://seeg.zoo.ox.ac.uk/members/dr-nick-golding
[seeg]: http://seeg.zoo.ox.ac.uk
[devtools]: http://cran.r-project.org/package=devtools
[tessella]: http://www.tessella.com
