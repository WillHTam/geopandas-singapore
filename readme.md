## On Fiona
* Fiona breaks very easily as a result of mixing versions, not to mention Anaconda's version mixing.
* Even restricting the channel to conda*forge still breaks it
* To use Fiona reliably, create an environment
* I used 'conda create **name GeoAnalysis *c conda*forge python=3.5 fiona jupyter geopandas pandas shapely geocoder future geojsonio'
* Then do 'source activate GeoAnalysis' / 'source deactivate'
* While the env is active, you can do conda installs and they will only apply to the environment.

## On using Google Maps with Anaconda
* Wasn't happy with any of the Google Maps packages on the Conda package manager since all the builds are either super old, for R, or not available
* Used 'pip3 googlemaps==2.4.6', since 'pip' was overridden to use the  Anaconda version and couldn't find googlemaps for some reason
* In your Jupyter Notebook, 'import sys' and then 'print(sys.path)' to see where your Anaconda packages are located
* Copied the two GMaps related folders from the pip3 lib folder to the Anaconda one
* Restart Anaconda to load GMaps into the environment (I think this is necessary)
* Test with 'import googlemaps'. I don't think I would want to add my pip3 path to Anaconda even if it were possible because it seems like a real pain to keep both updated and it would cause a lot of conflicts

 ## in regards to get_gdf() method
* b/c GeoDataFrame points are just arbitrary points, need a CRS (coordinate reference system) to tell Python how those points are related to places on Earth
* http://geopandas.org/projections.html
* 'epsg:4326' uses WGS84 as its reference
    * very interesting: http://gisgeography.com/wgs84-world-geodetic-system/
