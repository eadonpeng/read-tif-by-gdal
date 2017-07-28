# read-tif-by-gdal
from osgeo import gdal
from osgeo.gdalconst import *

gdal.AllRegister()
filestr ="C:\\Users\\123\\Documents\\data\\GWR_AllPara.tif"
ds=gdal.Open(filestr)

print  ds.GetDriver().ShortName
print ds.RasterXSize
print ds.RasterYSize
print ds.RasterCount

print ds.GetProjectionRef()

adf = ds.GetGeoTransform()
print adf[0]
print adf[3]

print adf[1]
print adf[5]

band1 = ds.GetRasterBand(18)#LST
band2 = ds.GetRasterBand(7)#SAVI
band3 = ds.GetRasterBand(9)#NDBI

pband1=band1.ReadAsArray(0,0,2,2)
pband2=band2.ReadAsArray(0,0,2,2)
pband3=band3.ReadAsArray(0,0,2,2)

print pband1
print pband2
print pband3
