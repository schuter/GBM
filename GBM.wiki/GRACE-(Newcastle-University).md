#Raw data

The mascon solutions over AIS were provided by Stuart Andrews (ex-University of Newcastle). They are monthly and 10-day solutions based on Level 1B GRACE data for 2003-2013.

Data and software to process the annual trends can be found in the following RDSF directory 
```
projects/GlobalMass/WP4-LandIce/Datasets/GRACE-Newcastle
```

The monthly mascon solutions are named by year and month. The 10 day solutions are also named by the year and month, followed by the modified Julian date of the centre day of the solution. The month of the 10 day solution is assigned by the month in which the centre day of the solution falls.
 
In breif, these solution have 
 
1)      Left in the GIA signal
2)      Corrected the degree  1 terms – the C20 has not been changed as we do not explicitly estimate this
3)      Provided solutions for Jan 2003 to December 2013     
 
for more details about the processing see Andrews et al. (2015) Geophys. JInt. Mass change from GRACE: a simulated comparison of Level-1B analysis techniques

The solutions are provided on a 1 degree by 1 degree grid.

#Software
We regrid the raw data to match Scott Luthcke's mascons and reproject to polar stereographic using the script **setdata.m**

To estimate the linear trends we run the code **trends_linearseasonal_gracephil_0313-polifit.m**. This also applies a seasonal correction to the data and writes the output with the appropriate format to be loaded into the framework.

#**Figures**:
For an idea of how the output trends look like see:

[Annual mass trends](https://github.com/albamesp/GBM/tree/master/figures/GRACE-NC-annual.pdf) 
