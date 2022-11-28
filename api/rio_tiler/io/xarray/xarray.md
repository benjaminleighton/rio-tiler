# Module rio_tiler.io.xarray

rio_tiler.io.xarray: Xarray Reader.

None

## Variables

```python3
WGS84_CRS
```

```python3
rioxarray
```

```python3
xarray
```

## Classes

### XarrayReader

```python3
class XarrayReader(
    input: 'xarray.DataArray',
    tms: 'TileMatrixSet' = <TileMatrixSet title='Google Maps Compatible for the World' identifier='WebMercatorQuad'>,
    geographic_crs: 'CRS' = CRS.from_epsg(4326)
)
```

#### Attributes

| Name | Type | Description | Default |
|---|---|---|---|
| dataset | xarray.DataArray | Xarray DataArray dataset. | None |
| tms | morecantile.TileMatrixSet | TileMatrixSet grid definition. Defaults to `WebMercatorQuad`. | `WebMercatorQuad` |
| geographic_crs | rasterio.crs.CRS | CRS to use as geographic coordinate system. Defaults to WGS84. | WGS84 |

#### Ancestors (in MRO)

* rio_tiler.io.base.BaseReader
* rio_tiler.io.base.SpatialMixin

#### Instance variables

```python3
geographic_bounds
```

Return dataset bounds in geographic_crs.

```python3
maxzoom
```

Return dataset maxzoom.

```python3
minzoom
```

Return dataset minzoom.

#### Methods

    
#### feature

```python3
def feature(
    self,
    shape: 'Dict',
    dst_crs: 'Optional[CRS]' = None,
    shape_crs: 'CRS' = CRS.from_epsg(4326),
    resampling_method: 'Resampling' = 'nearest'
) -> 'ImageData'
```

    
Read part of a dataset defined by a geojson feature.

**Parameters:**

| Name | Type | Description | Default |
|---|---|---|---|
| shape | dict | Valid GeoJSON feature. | None |
| dst_crs | rasterio.crs.CRS | Overwrite target coordinate reference system. | None |
| shape_crs | rasterio.crs.CRS | Input geojson coordinate reference system. Defaults to `epsg:4326`. | `epsg:4326` |

**Returns:**

| Type | Description |
|---|---|
| rio_tiler.models.ImageData | ImageData instance with data, mask and input spatial info. |

    
#### get_maxzoom

```python3
def get_maxzoom(
    self
) -> 'int'
```

    
Define dataset maximum zoom level.

    
#### get_minzoom

```python3
def get_minzoom(
    self
) -> 'int'
```

    
Define dataset minimum zoom level.

    
#### info

```python3
def info(
    self
) -> 'Info'
```

    
Return xarray.DataArray info.

    
#### part

```python3
def part(
    self,
    bbox: 'BBox',
    dst_crs: 'Optional[CRS]' = None,
    bounds_crs: 'CRS' = CRS.from_epsg(4326),
    resampling_method: 'Resampling' = 'nearest'
) -> 'ImageData'
```

    
Read part of a dataset.

**Parameters:**

| Name | Type | Description | Default |
|---|---|---|---|
| bbox | tuple | Output bounds (left, bottom, right, top) in target crs ("dst_crs"). | None |
| dst_crs | rasterio.crs.CRS | Overwrite target coordinate reference system. | None |
| bounds_crs | rasterio.crs.CRS | Bounds Coordinate Reference System. Defaults to `epsg:4326`. | `epsg:4326` |
| resampling_method | rasterio.enums.Resampling | Rasterio's resampling algorithm. Defaults to `nearest`. | `nearest` |

**Returns:**

| Type | Description |
|---|---|
| rio_tiler.models.ImageData | ImageData instance with data, mask and input spatial info. |

    
#### point

```python3
def point(
    self,
    lon: 'float',
    lat: 'float',
    coord_crs: 'CRS' = CRS.from_epsg(4326)
) -> 'PointData'
```

    
Read a pixel value from a dataset.

**Parameters:**

| Name | Type | Description | Default |
|---|---|---|---|
| lon | float | Longitude. | None |
| lat | float | Latitude. | None |
| coord_crs | rasterio.crs.CRS | Coordinate Reference System of the input coords. Defaults to `epsg:4326`. | `epsg:4326` |

**Returns:**

| Type | Description |
|---|---|
| None | PointData |

    
#### preview

```python3
def preview(
    self,
    max_size: 'int' = 1024,
    height: 'Optional[int]' = None,
    width: 'Optional[int]' = None
) -> 'ImageData'
```

    
Return a preview of a dataset.

**Parameters:**

| Name | Type | Description | Default |
|---|---|---|---|
| max_size | int | Limit the size of the longest dimension of the dataset read, respecting bounds X/Y aspect ratio. Defaults to 1024. | 1024 |
| height | int | Output height of the array. | None |
| width | int | Output width of the array. | None |

**Returns:**

| Type | Description |
|---|---|
| rio_tiler.models.ImageData | ImageData instance with data, mask and input spatial info. |

    
#### statistics

```python3
def statistics(
    self,
    categorical: 'bool' = False,
    categories: 'Optional[List[float]]' = None,
    percentiles: 'List[int]' = [2, 98],
    hist_options: 'Optional[Dict]' = None,
    max_size: 'int' = 1024,
    **kwargs: 'Any'
) -> 'Dict[str, BandStatistics]'
```

    
Return bands statistics from a dataset.

    
#### tile

```python3
def tile(
    self,
    tile_x: 'int',
    tile_y: 'int',
    tile_z: 'int',
    tilesize: 'int' = 256,
    resampling_method: 'Resampling' = 'nearest'
) -> 'ImageData'
```

    
Read a Web Map tile from a dataset.

**Parameters:**

| Name | Type | Description | Default |
|---|---|---|---|
| tile_x | int | Tile's horizontal index. | None |
| tile_y | int | Tile's vertical index. | None |
| tile_z | int | Tile's zoom level index. | None |
| tilesize | int | Output image size. Defaults to `256`. | `256` |
| resampling_method | rasterio.enums.Resampling | Rasterio's resampling algorithm. Defaults to `nearest`. | `nearest` |

**Returns:**

| Type | Description |
|---|---|
| rio_tiler.models.ImageData | ImageData instance with data, mask and tile spatial info. |

    
#### tile_exists

```python3
def tile_exists(
    self,
    tile_x: int,
    tile_y: int,
    tile_z: int
) -> bool
```

    
Check if a tile intersects the dataset bounds.

**Parameters:**

| Name | Type | Description | Default |
|---|---|---|---|
| tile_x | int | Tile's horizontal index. | None |
| tile_y | int | Tile's vertical index. | None |
| tile_z | int | Tile's zoom level index. | None |

**Returns:**

| Type | Description |
|---|---|
| bool | True if the tile intersects the dataset bounds. |