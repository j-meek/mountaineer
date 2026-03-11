# `capcomm`
**c**oordinate **a**nd **p**olygon **comm**unities

### goal
Query species occurrence records (GBIF) to calculate biodiversity metrics and infer number/type of ecological communities for a geographic polygon of interest. Community inference will be based on species abundances, geographic distances between occurrences, and climate data (WorldClim). 

### dependencies
`numpy`
`pandas`
`pygbif`
`geopandas`
`PySAL`

### DOCS

- [geopandas](https://geopandas.org/getting_started/introduction.html)


### data
- GeoDataFrame with polygon or multipolygon geometry
- GeoJSON files (easy conversion from .shp to .geojson through `geopandas`)
- pandas DataFrame with species, latitude, longitude (created when querying GBIF occurrence records)
- matrix of geographic distances between each occurrence record of the same species
- raster files of climate (temp, precip) and elevation from [WorldClim](https://www.worldclim.org/data/worldclim21.html).

To build and test this package, I will primarily use polygons of all global mountain regions available from the [Global Mountain Biodiversity Assessment](https://ilias.unibe.ch/goto.php?target=file_1047348). I plan to make these shape files more readily available by storing them in a simple API that can be queried by polygon name.

Species occurrence data will be queried from the GBIF REST API using the "kingdomKey", "familyKey", "genusKey", or "speciesKey" parameters to specify desired taxonomic scope, along with the "geometry" parameter to limit the occurrence record search within a specified polygon. For example, the following code queries GBIF for the first 100 plant occurrence records within the Andes fueginos mountain range.

```
res = requests.get(
    url="https://api.gbif.org/v1/occurrence/search/",
    params={
        "kingdomKey" : 6, 
        "geometry": mountains.geometry[0],
        "hasCoordinate": "true",
        "offset": 0,
        "limit": 100,
    }
)
res.url
```

After occurrence records have been downloaded, they will be filtered into a simple dataframe to reflect species name, latitude and longitude, like below:

```
genus 			species 		latitude		longitude
Pedicularis		groenlandica		39			-100
Pedicularis		groenlandica		42			-99
Pedicularis		groenlandica		35			-102
Delphinium		occidentale		39			-114
Delphinium		occidentale		38			-110
Lupinus			argenteus		42			-120
Lupinus			argenteus		41			-119
```

### user interaction
I think a Jupyter notebook would be the best way for a user to interact with this program because it would enable customized filtering of occurrence records and  map visualization of results. For users without Python experience, a webapp would be a nice way to visualize biodiversity and community metrics of different regions of the world. I envision an app with a dropdown menu where the user could select a polygon of interest (in this case, a mountain range) and a taxonomic focus (e.g., "Plantae"), and press "Run" to return the output. 

### output
The primary output would be a contextual map of the specified polygon and the inferred ecological (or taxon specific) communities within the polygon. A simple mapping of occurrence records within the polygon would also be useful, but this functionality already exists on the GBIF website (although it's not immediately obvious) and through [Map of Life](https://mol.org/), so I need to think a little more about what would set this webapp apart from what already exists. An R package called [`ecostructure`](https://github.com/kkdey/ecostructure) similarly infers community types based on species occurrence data, but does so at a broad (continental) scale and requires user-generated data rather than querying GBIF for occurrence records. My program will enable the user to "zoom in" on a polygon of interest to understand community structure in finer detail, and make open source occurrence data more readily available.