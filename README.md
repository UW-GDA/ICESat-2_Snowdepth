# ICESat-2_Snowdepth
Evaluating the efficacy of ICESat-2 data to measure snow depth over Tuolumne Meadows, CA.

Hannah Besso and Kory Swabb


## Project Title
Snow depth? S'now problem! 

## Summary
This project will be evaluating the efficacy of ICESat-2 data to measure snow depth over Tuolumne Meadows in Yosemite.

## Background
* Tuolumne Meadows is located in Yosemite National Park, CA
* The Upper Tuolumne River Watershed is a unique area for hydrologists to study, as it is one the only designated wilderness areas to provide a water source to a major city (San Francisco)
* The watershed is snow-melt dependent, and drains to the Hetch Hetchy Reservoir
 

## Problem statement, question(s) and/or objective(s)
Our project will attempt to answer the question: Can ICESat-2 be used to accurately measure snow depth in the Sierra Nevadas? We will compare snow depth measurements taken using ICESat-2 (spaceborne lidar) and ASO (airborne lidar) in terrain with low surface roughness. This evaluation will help inform whether ICESat-2 can be used to estimate snow water equivalent in watersheds where aerial lidar is not regularly flown throughout the winter.

## Datasets you will use (with links, if available)
Airborne lidar (ASO data) 
https://nsidc.org/data/ASO_50M_SWE/versions/1
https://www.airbornesnowobservatories.com/data
Snow pillow observations
https://www.wcc.nrcs.usda.gov/snow/
Spaceborne lidar (ICESat-2)
https://nsidc.org/data/icesat-2/data-sets

## Tools/packages you’ll use (with links)
Rioxarray, rasterio, xarray, geopandas, pandas, numpy, scipystats, matplotlib, etc

## Planned methodology/approach
Analyze the snow-off airborne lidar to identify locations with low surface roughness. 
Subset the spaceborne lidar to these locations (rough terrain has been shown to produce less accurate ICESat-2 measurements) and compare to the airborne lidar. 
If there is additional time, repeat 1 & 2 for snow-on data.
Determine if there is any correlation between important factors and data disagreements. Key factors include aforementioned surface roughness, varying tree density, and potential lidar penetration of the snowpack (for snow-on data).

## Expected outcomes
We expect that the ICESat-2 elevation data will be more similar to the ASO data in areas with low slope and low surface roughness. We also expect better results in areas with sparser vegetation cover.

## Any other relevant information, images/tables, references, etc.
https://github.com/UW-GDA/ICESat-2_Snowdepth/blob/main/tuolumne-river-watershed.jpg (https://www.tid.org/about-tid/current-projects/tuolumne-river-watershed/)

## References
1. https://www.sciencedirect.com/science/article/abs/pii/S0034425716302577?casa_token=jEkYG0hq1WcAAAAA:979ZLhf9CjFxWh8rQlDtYFcmEODuvcjbwXn3pasNwN8gzjqZo8g7RkW_fghlJt5fFr5wi_0Myw
2. Menounos B, Gardner A, Williamson S, Heathfield D. Assessment of Penetration Bias of ICESat-2 over Snow and Ice-covered Terrain, Western Canada. Poster session presented at: Fall Meeting of the American Geophysical Union; 2020 Dec 1-17; online.
3. Schenk T, Csatho B, Neumann T. A First Horizontal Accuracy Assessment of ICESat-2. Poster session presented at: Fall Meeting of the American Geophysical Union; 2020 Dec 1-17; online.
