1. Basics of Image Processing
2. Python and QGIS
3. Processing of Raster Images
4. Processing of Shapefiles
5. Neural Network
6. Object Detection
7. Segmentation
8. LiDAR

## Chapter 1. Processing With Aerial Image

```
# Import libraries
import numpy as np
import matplotlib.pyplot as plt
import rasterio
from rasterio.plot import show
```

Here, you are importing necessary libraries for your code. `numpy` is commonly used for numerical operations, `matplotlib.pyplot` for plotting, and `rasterio` for handling geospatial raster data.

```
# Open TIF image using rasterio
im = rasterio.open("/content/starting-computer-vision/data/palmaOrthoTotal_14cm.tif")

print(im)
```

You are using the `rasterio.open` function to open a TIF image file located at the specified path. The resulting object `im` is a `rasterio` dataset, representing the opened image. The `print(im)` statement displays information about the opened dataset.

```
# Show TIF image
fig, ax = plt.subplots(1, 1, figsize=(5,5))
show(im, transform=im.transform, ax=ax)
```

This block creates a subplot and uses `rasterio.plot.show` to display the opened TIF image. The transform parameter is used to specify the transformation to be applied to the image, and `ax=ax` ensures the image is displayed on the subplot.

The output is as follows,

![image](https://github.com/yohanesnuwara/PalmCV/assets/51282928/358e1de2-9d0d-4ff1-bc5a-7e477529dc8a)

The above is output of the raster TIF image showing oil palm plantation seen from above (aerial view). 

```
# Print CRS and coordinate bounds
print(im.crs)
print(im.bounds)
```

Here, you print the Coordinate Reference System (CRS) and the bounding box coordinates of the opened TIF image. The CRS defines how the spatial data relates to the Earth's surface, and the bounds represent the spatial extent of the image.

The output is as follows,

```
EPSG:4326
BoundingBox(left=-84.202437401, bottom=9.479328778, right=-84.199647927, top=9.482037704)
```

EPSG 4326 is a widely used geographic coordinate reference system (CRS) based on the World Geodetic System 1984 (WGS 84) datum. The bounding box defines the `left` as the minimum x coordinate, `right` as the maximum x coordinate, `bottom` as the minimum y coordinate, and `top` as the maximum y coordinate.

```
# Decode TIF file into Numpy array
im_arr = im.read()

print(im_arr)
print(im_arr.shape)
```

This block reads the TIF image data into a NumPy array using the `read` method. The resulting `im_arr` is a NumPy array representing the pixel values of the image. The two `print` statements display the array itself and its shape (dimensions).

The output is as follows,

```
[[[0 0 0 ... 0 0 0]
  [0 0 0 ... 0 0 0]
  [0 0 0 ... 0 0 0]
  ...
  [0 0 0 ... 0 0 0]
  [0 0 0 ... 0 0 0]
  [0 0 0 ... 0 0 0]]

(4, 2144, 2207)
```

The above array is a 3D array that contains 4 layers which are the B, G, R, and transparency channels, visualized in our next code. The number of pixels in the x and y-coordinate are 2144 and 2207, respectively.

