### Terrain 3D demo

### 参考
以 Mapbox Terrain-RGB 模型发布高程数据
https://beginor.github.io/2021/01/11/publish-dem-data-with-mapbox-terrain-rgb.html
https://rasterio.readthedocs.io/en/stable/installation.html
https://gdal.org/programs/gdalinfo.html#gdalinfo
https://github.com/syncpoint/terrain-rgb
https://water-gis.com/en/setups/terrain-rgb/create_terrainrgb/
https://gist.github.com/tmcw/4954720 


brew install gdal
pip3 install --upgrade pip
pip3 install gdal
gdalinfo --version

pipenv 
https://pythonguidecn.readthedocs.io/zh/latest/dev/virtualenvs.html
pip install --user pipenv
sudo -H pip install -U pipenv

virtualenv
virtualenv --version
pip install virtualenv

# 命令

gdalwarp -t_srs EPSG:3857 -dstnodata None -co TILED=YES -co COMPRESS=DEFLATE -co BIGTIFF=IF_NEEDED 2009_ProjectRaster2_3857.tif 2009_ProjectRaster2_3857_nodata_tif.tif
rio rgbify -b -10000 -i 0.1 2009_ProjectRaster2_3857_nodata.tif 2009_ProjectRaster2_3857_nodata_rgb.tif
gdal2tiles.py --zoom=5-15 2009_ProjectRaster2_3857_nodata_rgb.tif ./tiles
gdal2tiles.py --xyz --tilesize=512 --zoom=5-15 2009_ProjectRaster2_3857_nodata_rgb.tif ./tiles

### Demo 功能
模型分层
每一层颜色纹理展示
可以查询

开关分开显示不同层

两端 做一些淤泥、冲击区域，区别的地方
做预警 比如用红色显示

划线 拉断面（可以先用假的）