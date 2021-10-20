# MAP675 Exercise 01 - Command Line GIS and Cartographic Visual Hierarchies
## Manhattan Bike Lane Map  

### Mission Statment
In this project my goal was to symbolize bike paths in Manhatten using a visual hierarchy like outlined in the lesson. I'm going to have a dark base map underneath the bike paths symbolized by class they represent.

### Data Source - NYC Open Data
- Street centerlines with bike lane information: https://data.cityofnewyork.us/City-Government/NYC-Street-Centerline-CSCL-/exjm-f27b
- NYC Borrough Polygons: https://data.cityofnewyork.us/City-Government/Borough-Boundaries/tqmj-j8zm

### Process Outline
1. After downloading the data into shapefile format, I'll jump righ into converting them to GeoJSON since they are already in WGS84:
    - `ogr2ogr -f "GeoJSON" ../nycStreetCenterline.geojson geo_export_0da9bc6e-13cb-48ee-bc68-117b8c1badc2.shp` (centerlines)
    - `ogr2ogr -f "GeoJSON" boroughs.geojson geo_export_0886f076-a62d-4f42-8938-87bd7c8b4478.shp` (boroughs)
2. Next I need to filter out only the Manhattan borough:
    - `ogr2ogr -f "GeoJSON" -where "boro_name='Manhattan'" manhattan-borough.geojson boroughs.geojson`