# Snow Depth? S'now Problem!
Evaluating the efficacy of ICESat-2 data to measure snow depth over Tuolumne Meadows, CA.

Hannah Besso and Kory Swabb 

## Summary
This project will be evaluating the efficacy of ICESat-2 data to measure snow depth over Tuolumne Meadows in Yosemite.

## Background
* Tuolumne Meadows is located in Yosemite National Park, CA
* The Upper Tuolumne River Watershed is a unique area for hydrologists to study, as it is one the only designated wilderness areas to provides power and water source to a major city (San Francisco)
* The watershed is snow-melt dependent, and drains approximately 2,000 square miles to the Hetch Hetchy Reservoir
* Predicting Snow Water Equivalent (SWE) in snow-melt dependent watersheds is important for reservoir managers to both ensure enough water availability throughout the summer, and to avoid downstream flooding
* Most snow-melt dependent watersheds do not have regular aerial lidar flights throughout the winter to provide this information. ICESat-2 provides a promising spaceborne lidar dataset that could be leveraged to provide SWE information in understudied watersheds.

## Problem statement, question(s) and/or objective(s)
Our project will attempt to answer the question: Can ICESat-2 be used to accurately measure snow depth in the Sierra Nevadas? We will compare snow depth measurements taken using ICESat-2 (spaceborne lidar) and ASO (airborne lidar) in terrain with low surface roughness. This evaluation will help inform whether ICESat-2 can be used to estimate snow water equivalent in watersheds where aerial lidar is not regularly flown throughout the winter.

## Datasets you will use (with links, if available)
* Airborne lidar (ASO data)
   * ATL08
   * https://nsidc.org/data/ASO_50M_SWE/versions/1
   * https://www.airbornesnowobservatories.com/data
* Snow pillow observations
   * Utilized daily snow depth data from 11/1/2019 - 6/30/2020, for the Tuolumne Meadows, Slide Canyon, and Dana Meadows Sites.
   * https://info.water.ca.gov/snow/current/snow/index.html
   * http://cdec.water.ca.gov/dynamicapp/selectQuery
   
* Spaceborne lidar (ICESat-2)
   * https://nsidc.org/data/icesat-2/data-sets

## Tools/packages you’ll use (with links)
GDAL, Rioxarray, rasterio, xarray, geopandas, pandas, numpy, scipystats, matplotlib, etc

## Planned methodology/approach
1. Analyze the snow-off airborne lidar to identify locations with low slope (we defined this as <20 degrees). 
2. Subset the snow-off spaceborne lidar to these locations (rough terrain has been shown to produce less accurate ICESat-2 measurements) and compare to the airborne lidar. 
3. If there is additional time, repeat 1 & 2 for snow-on data. Compare snow-on ICESat-2 data to snow pillow data at similar elevations.
5. Determine if there is any correlation between important factors and data disagreements. Key factors include aforementioned surface roughness, varying tree density, and potential lidar penetration of the snowpack (for snow-on data).

## Expected outcomes
We expect that the ICESat-2 elevation data will be more similar to the ASO data in areas with low slope and low surface roughness. We also expect better results in areas with sparser vegetation cover.

## Any other relevant information, images/tables, references, etc.

Figure 1. Overview of Watershed
![alt text](https://github.com/UW-GDA/ICESat-2_Snowdepth/blob/main/images/tuolumne-river-watershed.jpg)
(https://www.tid.org/about-tid/current-projects/tuolumne-river-watershed/)

Figure 2. ASO DEM for the Upper Tuolumne Watershed (m)

![alt text](https://github.com/UW-GDA/ICESat-2_Snowdepth/blob/main/ASO_SnowOff.png)

Figure 3. Snow Pillow Sites (5)

![alt text](https://github.com/UW-GDA/ICESat-2_Snowdepth/blob/main/images/IMG_Snow_Pillows_Locations.JPG)

## Notebook Workflow
   * Data_Access_Icesat2.ipynb
   * ATL08_simplifier.ipynb
   * Create_ICESat2_GDF_premask.ipynb
   * Difference_ICESat-2_ASO.ipynb
   * SnowDepthComparison_CalcVSPillow.ipynb
   * Summer_2020_DataAnalysis.ipynb

## Actual Outcomes
The regression analysis between the snow-off ASO and ICESat-2 data yielded an R value of 1. This is likely due to the difference in magnitude between the elevation values and the difference values between the two datasets. The maximum difference between the datasets was around 15 meters, while the mean was -0.038419. The standard deviation was 2.3 meters. This was less acurate than we would like for measuring snow depth, because the ICESat-2 snow-on values need to be differenced from the snow-off DEM to obtain snow depth values. When we repeated our analysis for snow-on ICESat-2 data, we found a large spread of snow depth values, with many negative values that are likely due to disagreements between the ICESat-2 and ASO data. However the mean of the ICESat-2 derived snowdepths followed a general trend of increased snow depth during the accumulation season and decrease in snow depth during the ablation season.

## Future Work

We would like to complete a similar analysis for roughness values instead of slope, including different scales at which roughness is calculated so as to account for what we think of as 'microscale', 'hillscale', and 'mountainscale'. We would also include a spatial analysis with vegetation cover density to determine how canopy cover affects ICESat-2 accuracy. Finally, we think subsetting the ICESat-2 data to more closely match the attributes of the snow pillow sites would decrease the spread of the ICESat-2 snowdepth data.

## References
1. Thomas H. Painter, Daniel F. Berisford, Joseph W. Boardman, Kathryn J. Bormann, Jeffrey S. Deems, Frank Gehrke, Andrew Hedrick, Michael Joyce, Ross Laidlaw, Danny Marks, Chris Mattmann, Bruce McGurk, Paul Ramirez, Megan Richardson, S. McKenzie Skiles, Felix C. Seidel, Adam Winstral, The Airborne Snow Observatory: Fusion of scanning lidar, imaging spectrometer, and physically-based modeling for mapping snow water equivalent and snow albedo, Remote Sensing of Environment, Volume 184, 2016, Pages 139-152, ISSN 0034-4257, https://doi.org/10.1016/j.rse.2016.06.018. (https://www.sciencedirect.com/science/article/pii/S0034425716302577)
2. Menounos B, Gardner A, Williamson S, Heathfield D. Assessment of Penetration Bias of ICESat-2 over Snow and Ice-covered Terrain, Western Canada. Poster session presented at: Fall Meeting of the American Geophysical Union; 2020 Dec 1-17; online.
3. Schenk T, Csatho B, Neumann T. A First Horizontal Accuracy Assessment of ICESat-2. Poster session presented at: Fall Meeting of the American Geophysical Union; 2020 Dec 1-17; online.
4. Riley, Shawn & Degloria, Stephen & Elliot, S.D.. (1999). A Terrain Ruggedness Index that Quantifies Topographic Heterogeneity. International Journal of Science. 5. 23-27. https://www.researchgate.net/publication/259011943_A_Terrain_Ruggedness_Index_that_Quantifies_Topographic_Heterogeneity
5. Malek SA, Bales RC, Glaser SD. Estimation of Daily Spatial Snow Water Equivalent from Historical Snow Maps and Limited In-Situ Measurements. Hydrology. 2020; 7(3):46. https://doi.org/10.3390/hydrology7030046
