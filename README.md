# Recycling Effectiveness in MA
#### *final project overview and updates*
---
## Problem Statement

This project will explore the effectiveness of recycling in the state of Massachusetts.
Factors of interest:
* effect of recycling municipal waste handling program (service type, collection fequency, etc)
* effect of trash and general municipal waste handling program (pay-to-throw, buildings served, etc)
* effect of municipality demographics (education level, types of homes, etc)
* trends over time

### Hypothesis, Goals, and Scope

The key features for recycling success may differ depending on municipality type. Factors like population of the municipality, how much waste they generate per household and other demographic information may cause some municipalities to have positive correlations with certain attributes and other municipalities to show completely opposite correlations.

The goals of this project are to cluster municipalities into different classifications and determine--within each classification--how can recycling rates be maximized. This data could help direct local policy and service deployment.

To make the data more approachable, only standard recycables are considered (e.g. no hazardous materials like batteries are included). Handling of compostables are also not considered but this analysis could be extended to this waste stream. This dataset does not include any information on "leakage", either in the form of illegal dumping of waste or the loss of waste in transit. The data also does not look at the purity of recyclables (also known as the contamination rate) as this data was not available for every municipality. Thus, this analysis assumes that all materials that are collect for recycling are recycled. This assumption could be risky because it is annecdotally known that participants of recycling can make "emotional" generation of recyclables; when they aren't sure if something is recycable, they assume it is, often when it is not.

## Content

### Notebooks (as of 02/13/2020)

Please note that some notebooks or files are just for my reference. If a file or folder is not listed below, it's because it's not relevant at this stage in my project. **important note**: please do not share the any information found in `data/Residue_Rates`. This is not for public consumption.

* `part1.ipynb` -- initial EDA of municipal recycling and trash tonnage generated per county in MA, along with some initial service information.
* `census.ipynb` -- importing, trimming and formatting of census data from the ACS in 2019. Resulting tables to be used in further clustering analysis.
* `cleanvoterdata.ipynb` -- short notebook to format and clean voter information per municipality. Not super important to understanding this project, so there is little commentary.
* `indexmatching.ipynb` -- getting census data, voter data, and recycling survey data to match up by index. Not super important for understanding the project, so there is little commentary.
  * output was `data/combined_municipality_characteristics.csv` to be used in part 2
* `part2.ipynb` (75% complete) -- clustering of municipalities based on primarily census data. Several clustering algorithms are explored in addition to feature importance using PCA.
  * output was `data/cluster_data.csv` to be used in part 4
* `part3.ipynb` (50% complete) -- setting up the service data for regression and model comparison within separate labels later (in part 4).
* `part4.ipynb` (25% complete)-- statistical assessment of recycling distributions within clusters as compared to the population. further comparison of trends within regression models of the clusters compared to the population
* data/..
  * `MA_MSW_Collection_Data` -- includes all the csv's I created from the municipal recycling and trash services survey. This includes the tonnages of waste generated.
  * `census_data` -- the csv's I generated from the Census API in the `census.ipynb` notebook
  * `MA_voting_info` -- voter registration per party per municipality


### Data Sources

Data I've collected related to recycling (`[u]` denotes what data has been used so far):
* [EPA historic national statistics on end-of-life (EOL)](https://edg.epa.gov/metadata/catalog/search/resource/details.page?uuid=C9310A59-16D2-4002-B36B-2B0A1C637D4E) for various types of municipal solid waste (MSW)
  * figures available [here](https://www.epa.gov/facts-and-figures-about-materials-waste-and-recycling/national-overview-facts-and-figures-materials)
* `[u]` [MA municipal survey data](https://www.mass.gov/lists/recycling-solid-waste-data-for-massachusetts-cities-towns) for years 2009 through 2019
  * Program and services description
  * Trash Disposal & Recycling Tonnage collected through municipal program, including materials collected from residents, municipal buildings, schools, and businesses
  * 2019 data EDA in `part1.ipynb`
* [MA Combustor Overall Waste Composition](https://www.mass.gov/guides/solid-waste-master-plan#-waste-characterization-&-capacity-studies-) By Primary Material Category for 2010, 2013, 2016, and 2019
* [MA Combustor and Disposal Rate](https://www.mass.gov/guides/solid-waste-master-plan) updates per year
  * NOT per material
  * per county
  * export and import processing
* [MA MSW Capacity](https://www.mass.gov/guides/solid-waste-master-plan#-waste-characterization-&-capacity-studies-) data
* [MA participation Survey Results](https://www.mass.gov/lists/recycling-solid-waste-data-for-massachusetts-cities-towns)
* Cambridge Residue Rates from recent 3-year audit (raw data not for public distribution)
* `[u]` Census ACS data for 2019, by "place" in the state of MA
  * various columns from groups DP02, DP03, DP04, and DP05
  * data cleaning and formatting can be see in `census.ipynb`
* [2019 Voter registration data](https://www.sec.state.ma.us/ele/eleregistrationstats/registrationstats.htm) for MA