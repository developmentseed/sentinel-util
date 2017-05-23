# Sentinel Util
Sentinel Util is a command line utility to create a mosaic from Sentinel images.

### Install
1. Install GDAL and Gippy v1.0.0b8
2. Download the repo

### Use
`python sentinel-util.py out bbox username password [-m mission] [-b beginning] [-e end] [-t type] [-p maxProducts]`

**out**
    The folder where the image file will be written (i.e. ```/path/to/your/folder```).
    
**bbox**
    Defines the bounding box in the form lat1,lon1,lat2,lon2, where each value is in decimal degrees. lat1 must be greater than lat2 and lon1 must be less than lon2 (i.e. the coordinate lat1,lon1 is the top left corner of the bounding box and lat2,lon2 is the bottom right corner).

**username**
    Your username for Copernicus Open Access Hub. Can be created [here](https://scihub.copernicus.eu/dhus/#/self-registration).

**password**
    Your password for Copernicus Open Access Hub. Can be created [here](https://scihub.copernicus.eu/dhus/#/self-registration).

**-m mission**
    The mission to download images from. 1, 2, or 3. Defaults to 1.

**-b beginning**
    If included, the mosaic will not incorporate images ingested before this date. Of the form yyyy-mm-dd (i.e. 1999-12-31).

**-e end**
    If included, the mosaic will not incorporate images ingested after this date. Of the form yyyy-mm-dd (i.e. 1999-12-31).

**-t type**
    For Sentinel-1 only, defaults to GRD.

**-p maxProducts**
    Default 100. Must be a positive integer ≤ 100. Limits the number of products downloaded.'

Alternatively, to run in the background and continue even after closing your terminal window (helpful for running on servers), run like ```nohup python sentinel-util.py [args] &amp;```
### What will happen
1. It will download up to 100 products that match the search criteria
2. Each of the images in the products will be reduced from 16bit to 8bit and switched to WebMercator
3. All the images will be stitched into a mosaic
