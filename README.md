# Marine landscape composition and biodiversity drive the distribution of gadoid nursery areas

[![DOI](https://zenodo.org/badge/788506086.svg)](https://doi.org/10.5281/zenodo.14996684)

## Project summary
Survival during species juvenile stages may potentially be the most important factor in a population’s recruitment. Using a combination of environmental variables gathered in the field with imaging and predictive mapping, this study predicted the nursery habitat of three commercially important juvenile gadoid species; Atlantic cod (<em>Gadus morhua</em>), haddock (<em>Melanogrammus aeglefinus</em>) and whiting (<em>Merlangius merlangus</em>). 

Stereo baited remote underwater video (SBRUV) surveys were used to gather presence/absence data within the South Arran Marine Protected Area (MPA) between 2013 and 2019 and probability of presence was modelled using binomial generalised additive mixed models. Increased presence with demersal and epibenthic biodiversity observed in all three species. Juvenile <em>G. morhua</em> presence was driven by increased proportional coverage of macroalgae, gravel containing maerl, and higher rugosity. <em>M. aeglefinus</em> were associated with depths between 20-30 metres, areas of low algae coverage, and lower current velocity. <em>M. merlangus</em> had a higher probability of presence away from areas of gravel but bordering algae patches with low rugosity and current velocity and a depth of over 30 metres. This study provides evidence that the most effective way to confer improvements to juvenile gadoid habitat across multiple species is the conservation and restoration of benthic and epibenthic biodiversity.

## Data Structure
Raw data for all species recorded are in .csv format and contain the maximum number of any given species recorded from SBRUV footahe (MaxN), this was subsequently used to calcualte Inverse Simpson's Diversity. All landscape metadata is also in .csv format, and contains data on depth, location (latitude/longitude), proportional substrata coverage, main substratum at each station, mean current velocity, distance to shore, substratum patch perimeter to area ratio, substratum patch area, and sitance to edge of each catagory of substratum patch. All details on calculation of these statics can be found [here](https://github.com/NWMilne/Seascape_mapping).

### Data analysis
Species distribution modelling of presence/absence (PA) for each of the three gadoid species was underaken with a binomial Generalised Additive Mixed Models (GAMM) using the [gamm4](https://github.com/cran/gamm4) package, with marine protect area (MPA) zone as a random effect to account for spatial autocorrelation. 
The area under receiver operating curve (AUROC) was calculated for the model of best fit, as was model sensitivity, and specificity, R2 and True Skill Statistics (TSS) using the [ROCR](https://github.com/cran/ROCR) R package. Model accuracy testing was conducted on a 25% split of the data and results of a confusion matrix using the [caret](https://github.com/topepo/caret/) R package.

Prediction of PA was visualised via rasters produced from GAMM models predicting onto a 100 x 100 m grid and interpolated using [akima](https://github.com/cran/akima).
Error maps were produced by calculating the model fit for each grid point and subtracting the binominal presence absence of the species. Predicted error of species presence/absence was mapped using ordinary kriging using [automap](https://github.com/cran/automap).
Examination of the degree of extrapolation of each model prediction was undertaken via Multivariate environmental similarity surfaces (MESS) using the [dismo](https://github.com/cran/dismo)

