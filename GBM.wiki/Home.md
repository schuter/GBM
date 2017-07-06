Welcome to the wiki for the WP4 of the GlobalMass project!

Datasets index. 

*Not public dataset. Responsible persons should be contacted before using the data.

- #ICESat 
         ## release 33 from NSIDC  
          - data version:  release 33 Level 2 NSIDC  
          - temporal coverage:  Feb 2003 - Oct 2009
          - spatial coverage:  global
          - contact person:   
          - Software developed: software calculate dh/dt and estimate annual trends (based on 3-yr moving window) + applies Centroid-Gaussian correction + ICB correction
          - products derived: annual trends of elevation changes (2003-2009)
         
       
         ## release 34 NSIDC  
          - data version:  release 34 level 2 NSIDC (includes C-G correction)
          - temporal coverage:  02/2003 - 10/2009
          - spatial coverage:  global
          - contact person:   
          - Software developed:  
          - products derived:  

- #Envisat *
          - data version: Along-track processing (Flament and Rémy, 2012) of elevation changes
          - temporal coverage: 09/2002 - 10/2010
          - spatial coverage: AIS and GRIS 
          - contact person:  Thomas Flament and Frédérique Rémy from LEGOS (Toulouse)
          - Software developed: Software to estimate annual trends (based on 3-yr moving window) 
          - products derived: annual trends of elevation changes (2003-2009)

- #Cryosat2 *
          - data version: "AWI in house" ESA Level 1b + TFRMA filter   
          - temporal coverage: 07/2010 - 06/2015
          - spatial coverage: AIS 
          - contact person: Veit Helm and Bert Wouters  
          - Software developed:  
          - products derived: annual trends of elevation changes (2010-2013) 

- #GRACE   
          ## RL01
          - data version: RL01  
          - temporal coverage: 01/2003- 11/2010
          - spatial coverage: AIS 
          - contact person:   Scott Luthcke (from Goddard space flight center)
          - Software developed: Software to estimate annual trends, software for merging mascons into lower resolution  (uncorrelated)  
          - products derived: Annual mass trends

          ## RL02v13
          - data version: RL02v13
          - temporal coverage: 2003-2013 monthly solutions
          - spatial coverage: AIS 
          - contact person:   Scott Luthcke (from Goddard space flight center)
          - Software developed: Software to estimate annual trends, software for merging mascons into lower resolution  (uncorrelated)  
          - products derived: Annual mass trends

          ## RL02v15
          - data version: RL02v15 with wiener filter
          - temporal coverage: 2003-2015 monthly solutions
          - spatial coverage: AIS 
          - contact person:   Scott Luthcke (from Goddard space flight center)
          - Software developed: Software to estimate annual trends, software for merging mascons into lower resolution  (uncorrelated)  
          - products derived: Annual mass trends

          ## Newcastle Univ (S.Andrews and P.Moore) *
          - data version: as in Andrews et al. (2015) Geophys. J. Int.
          - temporal coverage: 2003-2015 monthly and 10-day solutions
          - spatial coverage: AIS 
          - contact person:   Philip Moore (NewCastle University)
          - Software developed: Software to estimate annual trends, software for merging mascons into lower resolution  (uncorrelated)  
          - products derived: Annual mass trends
 
- #GPS  
         ## NewCastle*
          - data version: --  
          - temporal coverage:  1995-2013.7
          - spatial coverage: AIS (only located on rock)  
          - contact person: Liz Petrie (now in Glasgow) 
          - Software developed: estimating annual trends from time series of vertical velocites 
          - products derived: bedrock vertical velocities, annual trend 2003-2009

          ## King *
          - data version: compiled from public archives (international GNSS Service and UNAVCO) 
          - temporal coverage: 2009-2014  
          - spatial coverage: AIS (only located on rock)  
          - contact person: Matt King (Univ. Tasmania)  
          - Software developed: -- 
          - products derived: bedrock vertical velocities, trend 2009-2014 (see Martin-Español et al. 2016b for details)          

- #RACMO outputs   
          - data version: RACMO27\ANT, RACMO2.3, RACMO 2.4(unreleased) 
          - temporal coverage: 1979-2010, 1979-2013, 1979-2015 
          - spatial coverage: AIS  
          - contact person: Melchior van Wessem and Michiel van der Brooke (IMAU)   
          - Software developed: Software to estimate SMB anomalies
          - products derived: annual SMB anomalies (2003-2013)

- #Firn model outputs   
          - data version: FM_ANT3K27_1979-2011.nc
          - temporal coverage: 1979-2011  
          - spatial coverage: AIS  
          - contact person: S. Ligtenberg  
          - Software developed: Software to estimate firn anomalies
          - products derived: annual firn anomalies (2003-2009)
                 

- #GIA model outputs 
          - spatial coverage: AIS  
          - Riva 2009 (contact: Riccardo Riva)
          - AGE1b (contact: Ingo Sasgen)
          - Regina (contact: Ingo Sasgen)
          - Gunter 2013 (contact: Brian Gunter)
          - IJ05 (contact: Erik Ivins)
          - W12 and W12a (contact: Pippa Whitehouse)
          - Global model A 2013
          - Global model ICE-6G_C (VM5a) revised version (contact: D. Peltier)

- #Surface velocities
   ## CCI Ice Sheets - Greenland (ESA) from Sentinel-1 SAR data 
          - temporal coverage: 2015-10-15 to 2016-10-15
          - spatial coverage: GRIS
          - downloaded from: http://products.esa-icesheets-cci.org/products/details/greenland_ice_velocity_map_winter_2015_2016_v1.0.zip/

  ## MEASURES/NSIDCv2 
          - temporal coverage: 2008-2009 and 2009-2010
          - spatial coverage: GRIS
          - contact person: Dr. Ian Joughin.  
          - downloaded from: http://nsidc.org/data/docs/measures/nsidc-0478/
  
   ## Antarctica - Rignot INSAR & Bamber Balance velocities
          - data version: combination (in-house)
          - temporal coverage: 1996 - 2011 
          - spatial coverage: AIS  
          - contact person: Eric Rignot and Jonathan Bamber
     
- #Elastic model 
   To correct for the elastic deformation I used the Regional ElAstic Rebound calculator (REAR) available at 
   https://github.com/danielemelini/rear

   REAR runs on any UNIX environment with a Fortran compiler, including Windows systems running the Cygwin layer
   A description of the model can be found https://eos.org/project-updates/on-the-rebound-modeling-earths-ever-changing-shape


   