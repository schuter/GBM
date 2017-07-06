#Raw Data
The elevation rates for July 2010 to April 2014 are located in 

```
projects/GlobalMass/WP4-LandIce/Datasets/Cryosat2
```
These were provided by Bert Wouters for 2010-2013 using the method described in Wouters et al (2015).  They are based on Cryosat-2 level 2 data, processed as described in detail in Helm et al. (2014). 

The files "AIS10_opt5... .nc" contain the data for the fit with a simple trend, "AIS10_opt6... .nc" uses a fit with acceleration. Both data sets have the R2-adjusted included. 

The acceleration is defined as:

```
h=a0+trend*t+acc*t^2+surface_fit
```

 


#Software
**_read_nc.m_** file read the .nc files and saves them as .mat variables

**_CS2_combination.m_** applies different criteria to apply (or not to) acceleration to the trends and saves the trends in the right format to be assimilated by the framework.

 We only add the acceleration term for gridpoints where: 

- surface horizontal velocities are above 25 m/yr 

-  the rate of heigh change is larger than 2 sigma the SMB driven elevation changes from RACMO.  

- ```R2_acc > R2_no_acc```

If the criteria is not met, only the linear 3-year trend is used. 

 

#Figures

[CS2 mask for accelerations](https://github.com/albamesp/GBM/tree/master/figures/AIS_CS2_mask.png)




 