This data is parsed directly (November 2020) from the Zürich city open data set "Fuss und Velowegnetz" (Pedestrian and Bicycle Path Network): https://data.stadt-zuerich.ch/dataset/geo_fuss__und_velowegnetz

The category mapping for "map_velo" is as follows:

```
0=keine Route in der gedruckten Karte "Map Velo"
1=empfohlene Route
2=empfohlene Route Naturbelag
3=schnelle ergänzende Route
5=Fahrverbot
6=Biketrail
```

The count of objects per category

    0 : 33,576
    1 : 4,181
    2 : 550
    3 : 1531
    5 : 31
    6 : 21
    
There is no category 4!

Using the super **[jq](https://stedolan.github.io/jq/)** command, each value for the property "map_velo" is split into a unique file.

For example:

    cat taz_mm.tbl_routennetz.json |jq '.features |= map(select(.properties.map_velo == 6))' > map_velo_6.json
   