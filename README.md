# Animations-in-the-time-of-Coronavirus

The details of the codeset and plots are included in the attached Microsoft Word Document (.docx) file in this repository. 
You need to view the file in "Read Mode" to see the contents properly after downloading the same.

A Brief Introduction
=======================

The first four months of 2020 have been dominated by the Coronavirus pandemic (aka COVID-19), which has transformed global life in an unprecedented way. Societies and economies struggle to adapt to the new conditions and necessary contraints. A reassuringly large fraction of governments around the world continue to take evidence-based approaches to this crisis that are grounded in large scale data collection efforts. Most of this data is being made publicly available and can be studied in real time. This post will describe how to extract and prepare the necessary data to animate the spread of the virus over time within my native country of Germany.

I have published a pre-processed version of the relevant data for this project as a Kaggle dataset, together with the geospatial shape files you need to plot the resulting map. This post outlines how to build that dataset from the original source data using a set of tidyverse tools. Then we will use the gganimate and sf packages to create animated map visuals.

Those are the packages we need:

libs <- c('dplyr', 'tibble',      # wrangling
          'stringr', 'readr',     # strings, input
          'lubridate', 'tidyr',   # time, wrangling
          'knitr', 'kableExtra',  # table styling
          'ggplot2', 'viridis',   # visuals
          'gganimate', 'sf',      # animations, maps
          'ggthemes')             # visuals
invisible(lapply(libs, library, character.only = TRUE))

The COVID-19 data for Germany are being collected by the Robert Koch Institute and can be download through the National Platform for Geographic Data (which also hosts an interactive dashboard). The earliest recorded cases are from 2020-01-24. 

DataSet
============
1. https://www.kaggle.com/headsortails/covid19-tracking-germany
2. https://npgeo-corona-npgeo-de.hub.arcgis.com/
