(this has been all inherited from previous postdocs)

#Raw data
We are using GPS from Newcastle, the person responsible is Liz Petrie (now at Glasgow).
We treat stations differently depending on the data quality.

1)	For campaign stations, and stations with mediocre quality (gaps and/or  jumps) we let Liz calculate a linear trend estimate for the whole time series. 

2)	The same goes for stations which are not contemporaneous. But, we only use non-contemporaneous stations if they are in an area where we do not expect a lot of variability from ice or SMB as this would cause elastic signals that alias the GIA signal. 

3)	For good quality continuous data with no gaps or jumps, we calculate annual trends. This is done using an algorithm Andrew developed to avoid spurious trends from a noisy time series. You can read about the problem in his blog: 

http://andrewzm.wordpress.com/2013/12/12/estimating-yearly-trends-with-an-em-algorithm-in-r/

#Software 

To run this algorithm use the script given in 
```
projects/GlobalMass/WP4-LandIce/Datasets/GPS-newcastle/GPS_ATM/ATM/atmosphere-downloads/R_processing
```
The script **all_stations_piecewise.sh** reads the station names and lat/lon from the file 

       site_lat_lon_elastic_2013-08-06.txt

the R script: **GPSpiecewise_noAtm.r** applies Andrew’s algorithm to the data. The output files are called

        XXXX_trends.dat

Where XXXX is the station name.

The script **cat_all_trends.sh** concatenates all the files that are given in the file

	good_annual_gps.txt

i.e. this file “defines” which stations are good and should be used for the annual estimation, together with the years for which the trends should be used. Here is the place to change the dates of the observation period if you need to (by changing the start or end date).

The script will concatenate everything into a file called all_good_annual_gps_trends.dat in the format name, lat, lon, trend, error, year. Now you only have to reproject the stations to x/y polar stereographic and you’re all set. 
This can be done using the IDL script **make_gps_trends_spattemp.pro**. Keep the input file as the IDL script removes the station names and you might need them.

I would advise to manually check that you have all the stations, either as annual or as linear trends over the whole period, some time series are dodgy and resist automation so for these you will either have to run the R script manually, or use the linear trend from Liz. Also check that you are not using stations twice ie both annual and linear trends.
You will also need to check if what you see makes sense, so it’s a good way to plot the stations.

You can use the script **plot_GPS_stations_with_labels.r** as a basis for that.

The stations with only one linear trend (not annual) are in 
```
projects/GlobalMass/WP4-LandIce/Datasets/GPS-newcastle/GPS_onetrend/RATES_seriestrendserrs2014-04-14
```
in the file 
         finalrateserrscoords.txt

Read the READme in this folder, and remember to remove the stations you used for annual trends.



