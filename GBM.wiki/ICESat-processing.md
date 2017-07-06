#Raw data
We are using release 33(sometimes called 633) ICESat data from NSIDC. We have applied the following corrections to the raw data: Centroid-Gaussian correction and ICB correction (Hofton et al. 2013).

There is a newer release (634) which includes the C-G correction. I have downloaded it (following instructions given below) BUT NOT USED in the papers. It can be found at
```
projects/GlobalMass/WP4-LandIce/Datasets/ICESAT634/
```

#Software

## Using a new release
If you use a new release, follow the instructions given in the subset_icesat.pro IDL script. These are:

1) Download the new data from NSIDC and run the qulity control scripts they provide (ngat)

2) Run proc_icesat, which calls altered read_glas_file.pro and gla12_pv6_0__define.pro

3) Run subset_icesat.pro to cul the data using quality checks from Ben Smiths 2005 paper.

## Calculating annual trends
Data is located in **_projects/GlobalMass/WP4-LandIce/Datasets/ICESAT/"Antarctica-OR-Greenland"/_**
The filenames end in *.OUT.

The script to calculate dh/dts is called **icesatprocessing_newICB_acc.pro**, it’s in the same place. Again, it has been also for different projects, so it contains different parameters that can be turned on/off to set it up.

Everything is commented in some detail but just to give you an overview:

First, the program goes through all the files and determines a pointmask. This will save time & memory later.

The point mask is stored in **_projects/GlobalMass/WP4-LandIce/Datasets/ICESAT/_** named **ICESat_"Antarctica-OR-Greenland"-pointmask.sav**. This takes a while so once you have the pointmask, you can switch is off by setting the flag **newproc=0**.

Then, the data is gridded into a 1km resolution and only cells with more than 10 footprints are used (but once in the framework, it is downscaled to 10k res).
Again, this only needs to be done once and you can switch it off by setting **newmask=0**.

Now, the actual dh/dt processing starts.

ICB correction can be switched on and off (**flag ICB**).

The dh/dts are determined for a "short" (2003-2006), "long" (2003-2009) and "annual" periods. Make sure to adjust the time range the time the tracks will have to span) if you switch from annual to long and back. For the long period, I have put in a quadratic term that can be co-estimated. This can also be used for the annual files if you want.
If you do the annual files, you can choose between 3-year moving window or single year trends. For the RATES project we used 3-yr moving window with the flags **dot_trend=0** and **annual=1**. To estimate a single trend (the "long" period) set **dot_trend=1**, **annual=0**

The output files have the format: x,y, dh/dt, sterr.

#Figures
For an idea of how the output trends look like see:

[Antarctica dh/dt in 2006](https://github.com/albamesp/GBM/blob/master/figures/icesat_2006.png)
[Greenland dh/dt in 2006](https://github.com/albamesp/GBM/tree/master/figures/icesat_GRIS_2006.png)

 
