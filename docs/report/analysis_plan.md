# Title of Study

## Contributors

- Emmanuel H. Lyimo<sup>1</sup>\*, email address, [ORCID link](https://orcid.org/0000-0002-5750-8636), College of African Wildlife Management, Mweka. P.O Box 3031, Moshi, Tanzania 
- Gabriel M. Mayengo<sup>1</sup>, mayengogabriel@gmail.com
- David J. Castico<sup>2</sup>, davidcastico@gmail.com
- Damian Nguma<sup>3</sup>, damiannguma@gmail.com
- Kwaslema M. Hariohay<sup>1</sup>, kwaslema2000@gmail.com
- Alex W. Kisingo<sup>1</sup>, alexkisingo@gmail.com
- Justin Lucas<sup>4</sup>
- Niwaeli Kimambo<sup>4</sup>
- Joseph Holler<sup>4</sup>
- Alana Lutz<sup>4</sup>
- Andy Atallah<sup>4</sup>

<sup>1</sup> College of African Wildlife Management, Mweka. P.O Box 3031, Moshi, Tanzania 

<sup>2</sup>Tanzania People and Wildlife, P.O Box 11306, Arusha, Tanzania

<sup>3</sup> Tanzania Wildlife Research Institute, P.O Box 661, Arusha, Tanzania

<sup>4</sup> Middlebury College, Middlebury, Vermont 05753, USA

\* Corresponding author and creator

## Abstract

This study is a reproduction of unpublished research by Emmanual H Lyimo et al (2023), titled: Makuyuni Wildlife Corridor: Analysis of the Effects of Socioecological Interactions and Changing Land Use on Movement Patterns of Large Mammal Species. The original study evaluated the connectivity of Makuyuni Wildlife Corridor, a stretch of unprotected land between Tarangire National Park and Essmingor National Forest Reserve in Tanzania. We reproduce the first part of the study, a multifactor analysis model that approximates cost of movement through the corridor based on least cost pathway analysis. The study was originally conducted using the QGIS Model Builder, and we reproduce the workflow in R. The goal of the study is to reproduce the authors' map displaying the minimum cost of movement through each point in the study area, compare the reproduced map to the original map, and evaluate why the reproduction may differ from the original.

### Study metadata

- `Key words`: multifactor analysis, least cost pathway, wildlife corridor, movement cost, line transect sampling, Makuyuni, Tarangire National Park, Essmingor National Forest Reserve, Tanzania
- `Subject`: Social and Behavioral Sciences: Geography: Nature and Society Relations
- `Date created`: 2023-11-30
- `Date modified`: 2023-11-30
- `Spatial Coverage`: Makuyuni Wildlife Corridor, Tanzania
- `Spatial Resolution`: 10 meter resolution
- `Spatial Reference System`: EPSG 32736
- `Temporal Coverage`: 2023
- `Temporal Resolution`: Not applicable

#### Original study spatio-temporal metadata

As this is a reproduction study, all of these fields are the same as in the original study.

## Study design

This is a **reproduction study**. The part of the study which we are reproducing (the wildlife corridor ) is **observational**.

Our research question concerns whether the wildlife corridor least cost analysis can be reproduced in R. The **null hypothesis** is that there will be no difference between Figure 5 in the original study and the reproduced Figure 5 which we create using R. The **alternative hypothesis** is that there will be apparent differences between these two figures.

Our method of comparing the two figures will be visual inspection due to the scope of the project.

## Materials and procedure

We are using data shared from the original authors of the study.
We will look through their data, workflows, and models and reproduce their Figure 5 (least cost pathway) in R. We will follow the structure of the workflow as closely as possible.

### Computational environment

Hardware: MacBook Air M1 2020; MacOS 13.4 (22F66)

R Version 2023.06.2+561 (2023.06.2+561)

R packages used:
- raster
- stars
- sf

Define the hardware, operating system, and software requirements for the research.
Include citations to important software projects, plugins or packages and their versions.

### Data and variables

Describe the **data sources** and **variables** to be used.
Data sources may include plans for observing and recording **primary data** or descriptions of **secondary data**.
For secondary data sources with numerous variables, the analysis plan authors may focus on documenting only the variables intended for use in the study.

Primary data sources for the study are to include ... .
Secondary data sources for the study are to include ... .

Each of the next subsections describes one data source.

#### landcover.tif

- `Abstract`: This is a land cover raster for the entirety of Tanzania.
- `Spatial Coverage`: The data source pertains to the whole country.
- `Spatial Resolution`: 4.77m
- `Spatial Reference System`: EPSG:3857 - WGS 84 / Pseudo-Mercator
- `Temporal Coverage`: 2023
- `Temporal Resolution`: Not applicable
- `Lineage`: Sourced from the following paper: Song, L., Estes, A. B., & Estes, L. D. (2023). A super-ensemble approach to map land cover types with high resolution over data-sparse African savanna landscapes. International Journal of Applied Earth Observation and Geoinformation, 116, 103152. https://doi.org/10.1016/j.jag.2022.103152
- `Distribution`: This was shared by the original authors.
- `Constraints`: Unknown
- `Data Quality`: No planned quality assessment.
- `Variables`: Band 1 is land cover. The classification scheme is established by Song et al. (2023).
  - 1 (orange): cropland
  - 2 (dark green): forest/dense tree
  - 3 (light green): grassland
  - 4 (green): shrubland
  - 5 (blue): water
  - 6 (gray): built-up
  - 7 (tan): bareland
  - 8 (teal): wetland

#### adjusted_studysite

- `Abstract`: This is a shapefile for the study site (i.e. the Makuyuni Wildlife Corridor)
- `Spatial Coverage`: The data source pertains to Makuyuni Wildlife Corridor.
- `Spatial Resolution`: Unknown
- `Spatial Extent`: 833295.2141958434367552,9588552.1709635984152555 : 858831.0715981726534665,9615078.0293724834918976
- `Spatial Reference System`: EPSG:32736 - WGS 84 / UTM zone 36S - Projected
- `Temporal Coverage`: Unknown, presumed 2023
- `Temporal Resolution`: Not applicable
- `Lineage`: Sourced from the shared data from the original authors, presumed to be namely Justin Lucas.
- `Distribution`: This was shared by the original authors.
- `Constraints`: Unknown
- `Data Quality`: No planned quality assessment.
- `Variables`: The shapefile is filled with a Simple Fill and has no land cover data.

#### bounding_box

- `Abstract`: This is a shapefile which was "used to create [a] buffer to prevent edge effects", per Justin Lucas. It extends past the boundaries of adjusted_studysite when the shapefiles are visualized together.
- `Spatial Coverage`: The data source pertains to land surrounding Makuyuni Wildlife Corridor and the corridor itself.
- `Spatial Resolution`: Unknown
- `Spatial Extent`: 833295.2141958434367552,9585634.2357019279152155 : 860913.8547548535279930,9617039.8727052193135023
- `Spatial Reference System`: EPSG:32736 - WGS 84 / UTM zone 36S
- `Temporal Coverage`: Unknown, presumed 2023
- `Temporal Resolution`: Not applicable
- `Lineage`: Sourced from the shared data from the original authors, presumed to be namely Justin Lucas.
- `Distribution`: This was shared by the original authors.
- `Constraints`: Unknown
- `Data Quality`: No planned quality assessment.
- `Variables`: The shapefile is filled with a Simple Fill and has no land cover data.

#### secondary_roads

- `Abstract`: This is a shapefile which is described as containing "all tracks and roads that were within the study area aside from the two major highways" by Justin Lucas. The shapefile contains line geometries and has 176 total features.
- `Spatial Coverage`: The data source pertains to land surrounding Makuyuni Wildlife Corridor and the corridor itself.
- `Spatial Resolution`: Unknown
- `Spatial Extent`: 4002985.2809690786525607,-417528.5057486270670779 : 4055363.5504161105491221,-386600.4248493338818662
- `Spatial Reference System`: EPSG:3857 - WGS 84 / Pseudo-Mercator
- `Temporal Coverage`: Unknown, presumed 2023
- `Temporal Resolution`: Not applicable
- `Lineage`: Sourced from the shared data from the original authors, presumed to be namely Justin Lucas. Lucas states that this shapefile was sourced from OpenStreetMap.
- `Distribution`: This was shared by the original authors.
- `Constraints`: Unknown
- `Data Quality`: No planned quality assessment.
- `Variables`: Roads are filled with a Simple Fill and there are no associated land cover data.

#### Bomas

- `Abstract`: This is a shapefile which ostensibly contains locations of bomas, or livestock enclosures, within the wildlife corridor.
- `Spatial Coverage`: The data source pertains to land within the wildlife corridor.
- `Spatial Extent`: 4007605.1797135984525084,-412580.2386067652842030 : 4032954.7106412472203374,-387445.8448925596894696
- `Spatial Reference System`: EPSG:3857 - WGS 84 / Pseudo-Mercator
- `Temporal Coverage`: Unknown, presumed 2023
- `Temporal Resolution`: Not applicable
- `Lineage`: Sourced from the shared data from the original authors, presumed to be namely Justin Lucas. 
- `Distribution`: This was shared by the original authors.
- `Constraints`: Unknown
- `Data Quality`: No planned quality assessment.
- `Variables`: Bomas are filled with a Simple Fill and there are no associated land cover data.

#### major_roads_vector

- `Abstract`: This is a shapefile which contains "two highways that run through the study area", per Justin Lucas.
- `Spatial Coverage`: The data source pertains to the entirety of the extent of the highways, which extend far past the study site and outside of Tanzania to the north and south.
- `Spatial Extent`: 24.9389406999999999,-33.9686420999999967 : 36.7868238000000005,-1.4968789000000000
- `Spatial Reference System`: EPSG:4326 - WGS 84
- `Temporal Coverage`: Unknown, presumed 2023
- `Temporal Resolution`: Not applicable
- `Lineage`: Sourced from the shared data from the original authors, presumed to be namely Justin Lucas. Lucas states that this shapefile is sourced from OpenStreetMap. 
- `Distribution`: This was shared by the original authors.
- `Constraints`: Unknown
- `Data Quality`: No planned quality assessment.
- `Variables`: The highways are filled with a Simple Fill and there are no associated land cover data.

### Prior observations  

Prior experience with the study area, prior data collection, or prior observation of the data can compromise the validity of a study, e.g. through p-hacking.
Therefore, disclose any prior experience or observations at the time of study pre-registration here, with example text below:

At the time of this study pre-registration, the authors had no prior knowledge of the geography of the study region with regards to the phenomena to be studied.
This study is related to 0 prior studies by the authors.

For each primary data source, declare the extent to which authors had already engaged with the data:

- [ ] no data collection has started
- [ ] pilot test data has been collected
- [ ] data collection is in progress and data has not been observed
- [ ] data collection is in progress and __% of data has been observed
- [x] data collection is complete and data has been observed. Explain how authors have already manipulated / explored the data.

For each data layer, the authors have investigated extent and other properties in QGIS.

### Bias and threats to validity

Given the research design and primary data to be collected and/or secondary data to be used, discuss common threats to validity and the approach to mitigating those threats, with an emphasis on geographic threats to validity.

The main threat is boundary/edge effects, which can be mitigated by adding an extremely high cost to the land outside of the study site or buffering the start and end regions (for accumulated cost analysis). This is to avoid a pathway traveling around the study site.

### Data transformations

- Reproject land cover raster
- Clip major roads to study site
- Reproject major roads
- Rasterize major roads

### Analysis

Describe the methods of analysis that will directly test the hypotheses or provide results to answer the research questions.
This section should explicitly define any spatial / statistical *models* and their *parameters*, including *grouping* criteria, *weighting* criteria, and *significance thresholds*.
Also explain any follow-up analyses or validations.

## Results

Describe how results are to be presented.

## Discussion

Describe how the results are to be interpreted *vis a vis* each hypothesis or research question.

## Integrity Statement

Include an integrity statement - The authors of this preregistration state that they completed this preregistration to the best of their knowledge and that no other preregistration exists pertaining to the same hypotheses and research.
If a prior registration *does* exist, explain the rationale for revising the registration here.

This report is based upon the template for Reproducible and Replicable Research in Human-Environment and Geographical Sciences, DOI:[10.17605/OSF.IO/W29MQ](https://doi.org/10.17605/OSF.IO/W29MQ)

## References