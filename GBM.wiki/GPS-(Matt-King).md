#Raw data
The data is located in 

```
projects/GlobalMass/WP4-LandIce/Datasets/GPS-King
```
containing bedrock vertical velocities from a compilation of GPS stations in Antarctica (2009-2014) after removing the elastic component. Each data set uses a different surface loading to correct for the elastic
...250km_post2009.dat uses the mass balance output from RATES setting the minimum lengthscale for GIA to 250 km 
...500km_post2009.dat uses the mass balance output from RATES setting the minimum lengthscale for GIA to 500 km
...CS2_post2009.dat uses the mass balance output from cryosat-2 elevation changes using a simple density assumption based on surface velocities (v>25 km/yr is ice, otherwise we use firn model from RACMO)

See Martin-Español et al (2016b) for information about the processing
