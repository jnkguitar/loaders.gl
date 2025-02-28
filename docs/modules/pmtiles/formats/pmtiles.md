# PMTiles 

- *[`@loaders.gl/pmtiles`](/docs/modules/pmtiles)*
- *[PMTiles specification](https://github.com/protomaps/PMTiles)*

PMTiles is a general format for storing tiled data addressed by Z/X/Y coordinates in a single (big) archive file. PMTiles is optimized for the cloud and can be hosted on commodity storage platforms like S3, enabling low-cost, zero-maintenance map applications, without requiring a server in the middle. PMTiles is structured to minimize overhead requests. The current V3 version of the format includes directories and tile data.

PMTiles is commonly used for visualization (e.g. for cartographic basemap vector tiles), and then often contains vector data, where each tile data contained within the archive is encoded as a Mapbox Vector Tile (MVT), however it can also be used to store image tiles (in PNG and JPEG format) containing e.g. raster data or terrain mesh data.

A PMTiles archive replaces a big directory tree of thousands of individual tile files, allowing an entire tileset to be manipulated (uploaded, downloaded, served, analyzed) as a single file.

In addition, there is a range of utilities and libraries for working with PMTiles, such Python packages for reading and writing, and support for various programming languages and tools as well as a number of viewers. And tiling tools such as [tippecanoe](https://github.com/felt/tippecanoe) can now output directly to PMTiles.

## Tile types

PMTiles is a container format and can in principle contain any type of quadtree-organized tiles. A number of vector and image tile types are predefined.

| Type   | MIME type                              | pmtiles | Description                                         |
| ------ | -------------------------------------- | ------- | --------------------------------------------------- |
| `MVT`  | `'application/vnd.mapbox-vector-tile'` | `1`     | [Mapbox Vector Tile](/docs/modules/mvt/formats/mvt) |
| `PNG`  | `'image/png'`                          | `2`     |                                                     |
| `JPEG` | `'image/jpeg'`                         | `3`     |                                                     |
| `WEBP` | `'image/webp'`                         | `4`     |                                                     |
| `AVIF` | `'image/avif'`                         | `5`     |                                                     |
| ...    | `'application/octet-stream'`           | ...     | Can be used for custom tile types                   |


## Metadata

The pmtiles header has a metadata field that can store arbitrary JSON metadata about the tileset. This means that for MVT pmtiles, [TileJSON](/docs/modules/mvt/formats/tilejson) is typically available in the PMTiles header.

