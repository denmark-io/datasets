
# DHM - height model

**description**

This dataset contains height information about Denmark. The raw data files
are points collected using the LiDAR technology, they are available in
the `PUNKTSKY` directory.

There are also DSM (digital surface model) in the `DSM` directory. And DTM
(digital terrain model) in the `DTM` directory. That is a processed version
of the raw data `PUNKTSKY`

**source**

ftp://ftp.kortforsyningen.dk/dhm_danmarks_hoejdemodel/

**format**

* `PUNKTSKY`: `.zip` file following a naming convention, contains multiply `.laz` files.
* `DSM` and `DTM`: `.zip` file following a naming convention, contains multiply `.tif` files.

In each directory is a shapefile (in `GRID/grid_punktsky_SHP_UTM32-ETRS89.zip`)
dividing the country up into blocks. The shapefile contains information about
the location of the block and name of the `.zip` file that contains the height
information.

The filenames have the format `${model}_${lat1}_${long1}_${format}_UTM32-ETRS89.zip`.
Each `.zip` files then contains the actual data files divided up into another
level of blocks. Those filenames have the format `${model}_1km_${lat1}${lat2}_${long1}${long2}.${format}`

The `lat2` and long `long2` forms a 10 by 10 grid. But sometimes files are
missing. We presume this is because no interesting data exists there
(just water).

For example the zipfile `DTM_605_66_TIF_UTM32-ETRS89.zip` would have the files:

```
dtm_1km_6059_660.tif dtm_1km_6059_661.tif ... dtm_1km_6059_669.tif
dtm_1km_6058_660.tif dtm_1km_6058_661.tif ... dtm_1km_6058_669.tif
.                    .                    .   .
.                    .                    .   .
.                    .                    .   .
dtm_1km_6050_660.tif dtm_1km_6050_661.tif ... dtm_1km_6050_669.tif
```

Each pixel the average height in a 40cm x 40cm rect. Each data file (`.tif` or
`.laz`) has a resolution of 2500 x 2500 pixels. Thus each data file describes
a 1km x 1km block.

**completeness**

Currently the data have only been collected for Fyn and Sjælland.
