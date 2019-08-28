## Create Map Tiles with GDAL

These are the basic steps to complete in order to create a set of map tiles from a georeferenced map. We will use the raster program We'll configure the final web map to have a slide for adjusting the transparency of the overlaid map.


### Software needed
1. GDAL (Geospatial Data Abstraction Library)    **Please install GDAL before the workshop**      
[DOWNLOAD HERE](https://gdal.org/download.html#current-releases)           
2. Internet Browser    



## Other prerequisites
1. Familiarity with (or willingness to try) command line tools.
If you're on a Mac, we'll use Terminal. If on Windows, we'll use the Windows command.
2. A GeoTiff.


## Shell Commands for this tutorial    
#### Basic Commands   
```cd``` - Change working directory      
```ls``` - List the content of the working directory

#### GDAL Commands  
```gdalinfo --version``` - Get the version of your GDAL installation     


# Let's create some tiles!
Open your command line tool (Cygwin, Terminal, etc.). Let's test out our GDAL installation. In your command line type:   
```gdalinfo --version```

The response should indicate the GDAL version and release date, like:    
```GDAL 2.4.2, released 2019/06/28```     

### Navigate to your GeoTiff

For this example, let's say you're working on a Mac, and have a project folder with the path /Users/evan/Documents/GISprojects/georeferencing/coolmaps/.  

Since my home directory is /Users/evan/, in Terminal I can use the *change directory* (```cd```) command to change my working directory to "coolmaps" by typing this at the command prompt:    
```cd Documents/GISprojects/georeferencing/coolmaps```

*(An alternative method with MacOS is to right click the folder in Finder, and select **Services > New Terminal at Folder**)*    

List the contents of that directory by typing ```ls``` at your command prompt. You should see the name of your GeoTiff or raster image. Mine's called **vanIsland.tif**

### Use gdal2tiles.py to create a tile set
Now that your working directory contains your file, you'll use the gdal2tiles.py script to create map tiles for your map.

The most basic command for this produces a new file directory which contains several folders of tiles, plus a web map template for Google Maps, OpenLayers, and Leaflet. However, there are many options we can add to our command if we need to, and you can find out more in the [gdal2tiles documentation](https://gdal.org/programs/gdal2tiles.html). We need to have gdal2tiles.py create a tileset from an input raster file (vanIsland.tif), and store them in a new file directory (tiles). Gdal2tiles.py will create the new directory for us if it doesn't yet exist with the following command structure:
```gdal2tiles.py [input file] [output-directory]   ```

At your command prompt, type:
```gdal2tiles.py vanIsland.tif tiles```

Once executed, you should see the tile creation progress.
![Wait for the tiles][tiles-loading]

If all goes as planned, this is what you should have in your working directory:
```

├── vanIsland.tif
|
├── tiles
    |
    ├── 5
    |   └── [Tiles at zoom level 5]  
    |  
    ├── 6
    |   └── [Tiles at zoom level 6]  
    |
    ├── 7
    |   └── [Tiles at zoom level 7]  
    |
    ├── 8
    |   └── [Tiles at zoom level 8]  
    |
    ├── 9
    |   └── [Tiles at zoom level 9]  
    |
    ├── 10
    |   └── [Tiles at zoom level 10]  
    |
    ├── googlemaps.html
    |
    ├── leaflet.html
    |
    ├── openlayers.html
    |
    └── tilemapresource.xml
    ```





[tiles-loading]: tiles.gif "wait for the tiles..."
