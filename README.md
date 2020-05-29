
# Temperature data from 2001 - 2015 from ERA5Land
## Sample of 371 Latin American Cities 

Many researchers involved in SALURBAL are interested in using historical temperature reanalysis data. ERA5Land data neglects pixels that have more than 50% water. However, many cities across the world are situated next to the ocean. Since we were losing information, our team interpolated data from ERA5 (at a 30 km x 30 km resolution) and imputed it at the ERA5Land 9km x 9km resolution, filling the gaps from those "missing" pixels. (Here include Yang's workflow). 

Once we got the "complete" data for all of our 371 cities, we decided to estimate temperatures at an AD (level 2) level. In order to get temperature data at the AD city level, we weight the temperature pixels by population data (using 100m x 100m WorldPop data for 2010).

Note: Since population data is not as accurate for Panama and Peru, we weight temperature by urban footprint data instead for cities in those countries.

The workflow is as follows:  
1. Create a vector from the temperature raster (in 9km x 9km cells). 
2. Import the vector and the AD boundaries into Google Earth Engine (GEE).
3. Process WorldPop data in GEE, estimating the number of people by the 9km x 9km.
4. Export the 9km x 9km pixels with population data into R.
5. Carry out the population weight: Since both the temperature, population, and Global Urban Footprint data are at the same resolution, we can carry out the estimation. 

### Access to raw data:
- [ERA5 hourly data on single levels](https://cds.climate.copernicus.eu/cdsapp#!/dataset/reanalysis-era5-single-levels?tab=overview)
- [WorldPop data](https://www.worldpop.org/project/categories?id=3)
- [Global Urban Footprint data](https://drive.google.com/drive/folders/1_NM6c_SDAqb0LAOXt8LpbTT7eIL3HgAY)

### Access to imputed data:
- [ERA5Land imputed data](https://drive.google.com/drive/folders/1LgTT9Vd2JbJti72LqmWqFz-36Dvb7d44)

### Access to final data:
- [L1 AD and UX data](https://drive.google.com/drive/folders/1k1WdQ3k6ypDndEhkvM691z-sa7Z76sfK)
- [L2 data](https://drive.google.com/drive/folders/1domRgHFHNHCcMwFt8qp0zWi7IisA_dYM)

**Important notes**:  
- The final tables are L1_ADUX_2001_2015.csv, **L1_ADUX_wp_2001_2015.csv**, **L2_2001_2015.csv**, and **L2_wp_2001_2015.csv**. The files containing "wp" have population weighted temperature means for all cities including Panama and Peru. **L1_ADUX_2001_2015.csv** and **L2_2001_2015.csv** have population weighted temperature means for all cities except Panama and Peru that have GUF weighted temperature means for cities in those countries.  
- Leap years (2004, 2008, and 2012) are processed in alternative scripts within the *scripts* folder.

---

**Codebook for L1:**  
- SALID1: City ID. (6 digits)
- ADtemp_pw: Population weighted temperature mean at L1AD level. 
- ADtemp_x: Unweighted temperature mean at L1AD level. 
- UXtemp_pw:Population weighted temperature mean at L1UXX level. 
- UXtemp_x:  Unweighted temperature mean at L1UX level. 
- date: year-month-day.

**Codebook for L2:**  
- SALID2: City ID (8 digits). 
- L2temp_pw: Population weighted temperature mean at L2 level. 
- L2temp_x: Unweighted temperature mean at L2 level. 
- date: year-month-day. 
