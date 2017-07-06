Data and software are located in 
```
projects/GlobalMass/WP4-LandIce/Datasets/GRACE-NASAGSFC
```

#Raw Data

## RL01
upsm.SouthPole-ICE_v2_Jan03-Nov10_v05_w30000_d100_t10_pcg1_i1-100+DEG1+Paulson_rm161_fit20031201-20101201_scaledAISv09v12.h5
  - mascon solution from -57->-90 degrees latitude
  - AIS high/low elevation constraint included
  - solution is scaled to replicate effect of iteration


upsm.SouthPole-ICE_v2_Jan03-Nov10_v05_w30000_d100_t10_pcg1_i1-100_noaislo+DEG1+Paulson_rm161_fit20031201-20101201_scaledAISv09v12.h5
  - mascon solution from -57->-90 degrees latitude
  - no high/low elevation constraint
  - solution is scaled to replicate effect of iteration

global_mascon_L3_HDF5.pdf - data format document

lib/ - Matlab functions to load HDF5 data files


This mascon solution has the hydrology removed, the Swenson geocenter correction applied, and
a 161-day signal removed from every mascon. The GIA signal is not removed.


When using this data please reference the paper: Luthcke, S. B., T. J. Sabaka, B. D. Loomis, et al. 2013.
"Antarctica, Greenland and Gulf of Alaska land ice evolution from an iterated GRACE global mascon solution."
J. Glac. 59 (216), 613-631.

Contact information: Scott Luthcke <scott.b.luthcke@nasa.gov>; Bryant Loomis <bryant.d.loomis@nasa.gov>

##RL02v12
This is the new release 2 mascon product (RL02) which differs from the previous version in:

1) Uses our latest RL02 processing

2) Contains mascons for the south pole (oceans surrounding AIS and AIS mascons)

3) Contains monthly mascon solutions form Jan03 through Jun14

4) This has the GIA signal in the mascons, that is the GIA has not been removed

5) The solution is corrected for C20 and degree 1.

6) Contains filtered mascon values, these are the mascon solutions optimally de-noised (those to use).

##RL02v15

The data has two time series provided for each mascon, where one is the Wiener filtered solution and the other is the EEMD filtered where the sub-annual components have been removed. This is described in the pdf that can be found in the RL02v15 folder.

The version used for the final RATES paper (Martin-Español et al (2016a)) is RL02v15 with EEMD filter.

#Software
Although we have different versions of the mascon solutions provided by S. Luthcke (NASA/GSFC), the software used for processing the trends is common to all of them.

We use GRACE Mascons – mass concentrations derived from Level 1b data. The data product is a MATLAB workspace .
For the earlier versions we have two data sets, one with the high/low elevation constraint (see paper) removed and one  normal – we use the one WITHOUT the constraint. 

1)	Read in the data in MATLAB using the **run_read_mascon.m** script provided by Scott. This calls a few other functions which are provided.

2)	Write out the single mascons in our desired format by running **write_mascons_to_old_format_singlemascons.m**.
 
3)	Write out the mascon time series  in our desired format by running **write_mascons_to_old_format.m**.
 
4)	In IDL, run the script **readmascons_newrl_2014_noseasonal.pro**. This reads in the mascons, reprojects them to polar stereographic, and determines coordinates of the corners of the polygon encompassing each mascon. This is an important step as the polar stereographic projection is not area conserving. The output of the script is a locations file which tells you the number and coordinates of each mascon. Test plots help you check that all mascons are in the right place and the polygons actually surround them. 

5)	The trend calculations and the seasonal correction is done in Matlab – the script is called **trends_linearseasonal_grace2_linearmodel.m** (This script need the Islands and coastlines for plotting).  It reads in the locations file and the time series file, then does the deseasoning, calculates the annual trends, writes the data into files and plots the annual trend maps. 

NOTE that the latest version RL02v15 contains one set of mascons with an EEMD filter to remove the subannual cycles, therefore no extra seasonal correction need to be applied (this is the one used in the paper). 

Some values here are hardcoded – like the number of months in the icesat period, the number of mascons,  the number of years, and so on. The output file is called “mascon_annualtrends_newrl_april2014_ newformat_seasonalcorr.dat” (without the seasonalcorr part if there was no seasonal correction).

The format is "id", "year", "trend_cmweq", "std", "n", "t".  
