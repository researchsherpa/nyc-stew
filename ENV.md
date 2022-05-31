# Notes on the env

I use jupyter lab with a variety of python packages on linux. Here's a simple recipe to set it up from scratch.  Your mileage may vary based on OS.

  1. Make sure Anaconda is installed and `git clone` the repository from github.  cd into the nyc-stew folder.  
  
  2. In the nyc-stew folder you should see the environment.yml file.  Use this to build the env using conda:  `conda env create -f environment.yml`
  
  3. Once the create env is completed, activate the new env: `conda activate stew`
  
  4. At this point you will have a working jupyter lab with the necessary packages.  Launch the lab with `juptyer lab`.
  
  5. You're ready to explore, understand, develop, ...
  
  
  # Startup imports
  
  I am lazy with imports.  I setup a default start script in ~/.ipython/profile_default/startup so I don't think about specifics in a notebook.
  
  I have included start.py in the notebooks folder.  If you don't want to setup a default, just add a code cell (to each notebook) with %run start.py.
  
  
  # data
  
  My-o-my.  I've covered a lot of ground with the data.  In general the data flow is:
  
  **1.  Find data and save to the raw directory.**
  
  My raw directory looks like this:
  
  data/raw <br>
├── 311<br>
├── admin-boundaries<br>
├── DEM<br>
├── DEP<br>
├── NYC-2017-STEW-MAP-Public-Version2<br>
├── NYCFutureHighTideWithSLR.gdb<br>
├── NYC_STEWMAP_2017_Networks_Version2_Public.xlsx<br>
├── NYCWRP_Shapefiles_2016<br>
├── slr_metadata.pdf<br>
└── weather

8 directories, 2 files

I have some organization.  As of this time (05/31/2022), I have 31G.  Way to much for github. 

 **2.  Process the raw data and place it in data/processed.**
 
 My processed directory looks like:
  
data/processed/<br>
├── 311<br>
│   ├── dep-clean-geo.parq<br>
│   ├── dep-full.parq<br>
│   ├── dob-clean-geo.parq<br>
│   ├── dob-full.parq<br>
│   ├── dot-clean-geo.parq<br>
│   ├── dot-full.parq<br>
│   ├── dpr-clean-geo.parq<br>
│   ├── dpr-full.parq<br>
│   ├── dsny-clean-geo.parq<br>
│   ├── dsny-full.parq<br>
│   ├── hpd-clean-geo.parq<br>
│   └── hpd-full.parq<br>
├── admin-boundaries<br>
│   ├── boroughs.parq<br>
│   ├── brooklyn.parq<br>
│   ├── CDTA.parq<br>
│   ├── census-tracts-2020.parq<br>
│   └── NTA.parq<br>
├── brooklyn<br>
│   ├── brooklyn-2021-311.parq<br>
│   ├── brooklyn-311-elevation.parq<br>
│   ├── brooklyn-boundary.parq<br>
│   ├── brooklyn-catch-basins.parq<br>
│   ├── brooklyn-census-tracts.parq<br>
│   ├── brooklyn-community-districts-ta.parq<br>
│   ├── brooklyn-dem.parq<br>
│   ├── brooklyn-extreme-flood.parq<br>
│   ├── brooklyn-moderate-flood.parq<br>
│   ├── brooklyn-ms4-drainage.parq<br>
│   ├── brooklyn-ms4-outfalls.parq<br>
│   ├── brooklyn-neighborhoods-ta.parq<br>
│   ├── brooklyn-rainfall-2021.parq<br>
│   ├── brooklyn-slr-2050-08.parq<br>
│   ├── brooklyn-slr-2050-11.parq<br>
│   ├── brooklyn-slr-2050-16.parq<br>
│   ├── brooklyn-slr-2050-21.parq<br>
│   ├── brooklyn-slr-2050-30.parq<br>
│   ├── brooklyn-turfs.parq<br>
│   ├── primst-turfs-counts.parq<br>
│   └── primst-with-alters.parq<br>
├── db<br>
│   ├── popids2.p<br>
│   └── popids.p<br>
├── DCP<br>
│   ├── slr-2050-08.parq<br>
│   ├── slr-2050-11.parq<br>
│   ├── slr-2050-16.parq<br>
│   ├── slr-2050-21.parq<br>
│   ├── slr-2050-30.parq<br>
│   └── slr_metadata.pdf<br>
├── DEP<br>
│   ├── 2021-311.parq<br>
│   ├── brooklyn-extreme.parq<br>
│   ├── catch-basins.parq<br>
│   ├── Data_Dictionary_ExtremeFlood.xlsx<br>
│   ├── extreme-flood-map.parq<br>
│   ├── moderate-flood-map.parq<br>
│   ├── ms4-drainage.parq<br>
│   └── ms4-outfalls.parq<br>
├── office-locations.parq<br>
├── SN<br>
│   ├── connections.parq<br>
│   └── elements.parq<br>
└── turfs.parq

7 directories, 58 files
  
It contains 3.2G.  You can look at the notebooks and see what goes into the transformations.

Note that I am trying to use parquet files.  Much faster and more economical.

 **3.  For the first release, I am including data/processed/brooklyn/**
 
 This directory contains 72M.  Somewhat more manageable.