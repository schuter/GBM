# Raw data
Envisat data was provided by Thomas Flament and Frédérique Rémy from LEGOS (Toulouse).
For detailed information of the along-track processing algorithm they used see Flament and Rémy (2012).

Data is located at 
```
projects/GlobalMass/WP4-LandIce/Datasets/Envisat/Greenland-OR-Antarctica"/
```
(the GlobalMass folder in RDSF). 
The processed annual trends are in the **_\out\_** folder within each of the previous directories.

## AIS data
The original dataset comes as a Matlab file (Envisat_AIS.mat). I will introduce here the most relevant variables. A full description of the datasets is in "readme_Envisat_Antarctica.txt".

**_processout_** contains x y coordinates in km in stereographic polar projection, mean elevation (m),  dh/dt (m/year), slope in x and y directions (m/km), variance of elevation and residual and track numbers.

**_resretrend_** contains the time series corresponding to locations given in processout(:,1:2). Each line is a different location, each column is a cycle. Column 1 is cycle 9, column 2 is cycle 10 and so on. Also provided are the dates for each point in "datesapprox" which are reestimated based on the track number and cycle number. These dates are accurate to within ~1 h (half an orbit).

**_numres_** contains for each cycle, at each location, the number of raw measurements that where used for the fit.

**_stdestim_** contains an estimation of the stdandard deviation of the fitted parameters, as given by the lscov matlab function.

## GRIS data
The original dataset comes as a Matlab file (Greenland_relocated.mat). Dates for the time series were not given. I estimated the dates (see below) and stored them in approxdates.mat. I will introduce here the most relevant variables. A full description of the datasets is in "readme_Envisat_Greenland.txt".

Time series relocated to the point of closest approach using the GIMP 90 m DEM (variables relocx, relocy)
For all variables, one line equals one position, the line number is the index.
 
Variable **_stocknvgro_** contains the main outputs from the processing (similar to the variable **_processout_** above). See documentation for a complete description of the variables. 

**_stockstdnvgro_** contains the formal error estimates (from the least square fit). 

**_stockresretrendnvgro_** contains the time series. The time series are the residuals from the least square fit to which  the temporal trend is re-added (hence the name "retrend"). This makes them times series corrected of topography variation (second order, including curvature) and radiometric effects (BSC, TES and LEW). Each of the 85 columns contain the data for one Envisat cycle, from cycle 9 to 93.

**_approxdates_** contains the approximate dates (within one half-orbit, i.e. better than 1h) estimated from the cycle number and the track number. Knowing that cycle 9 started on August 27, 2002, that each cycle lasts exactly 35 days and that there are 1002 half-orbits per cycle, the date in days from 27/08/2002 is then ```35 * (cyclenumber - 9) + 35/1002*tracknumber```.


#**Software**:
There are two **matlab** files called **_writeout_envitimes.m_** and **_writeout_envivars.m_** that read in and write the main outputs, formatting them to the right format to process annual trends in idl.

These are then read into IDL with the script **_regina_envisat_trends_mit_quadrat_full_mod.pro_**.
This is a script I have used for different projects (RATES and REGINA). 
To estimate annual trends from a 3-year moving window you need to set up the following parameters:
```
RATES_3ways =1; RATES=0; REGINA=0

Seas=1   ;Seasonal correction on/off 

oneK=0; tenK=1 ;One K or 10 K resolution

oldout =0; newout=1 ;New output  format 

calctrend=1 ;Calculate trends
```
Additionally, you need to set up the number of points contained in the initial file (which differs between GRIS and AIS) and the domain to get the grid in the final interpolation.

#**Figures**:
For an idea of how the output trends look like see:

[Greenland dh/dt in 2006](https://github.com/albamesp/GBM/tree/master/figures/envisat_GRIS_2006.png)

[Antarctica dh/dt in 2006](https://github.com/albamesp/GBM/blob/master/figures/envisat_AIS_2006.png)
 