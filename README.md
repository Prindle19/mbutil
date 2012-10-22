# MBUtil

MBUtil is a utility for importing and exporting the [MBTiles](http://mbtiles.org/) format,
typically created with [MapBox](http://mapbox.com/) [TileMill](http://mapbox.com/tilemill/).

Before exporting tiles to disk, see if there's a [MapBox Hosting plan](http://mapbox.com/plans/)
or an open source [MBTiles server implementation](https://github.com/mapbox/mbtiles-spec/wiki/Implementations)
that works for you - tiles on disk are notoriously difficult to manage.

The new Google Maps Engine Options should make it easy to manage tiles on Google Maps Engine, and this utility will generate a .ebm file automatically which will create all the assets and mosaics you need automatically, including the spatial extents and projection information in a spatial metadata file for each tile.

## Installation

Git checkout (requires git)

    git clone git://github.com/Prindle19/mbutil.git
    cd mbutil
    ./mb-util -h

    # then to install the mb-util command globally:
    sudo python setup.py install
    # then you can run:
    mb-util

Python installation (requires easy_install)

    easy_install mbutil
    mb-util -h

## Usage

Export an `mbtiles` file to files on the filesystem:

    mb-util World_Light.mbtiles adirectory

Export an `mbtiles` file to files on the filesystem, and generate a Google Maps Engine .ebm file and spatial sidecar files for use on Google Maps Engine:

    mb-util --scheme=tms --gme=true --acquisitionDate=2012:10:22 --attribution=OSM --tags="osm, tilemill, osm bright" /gevol/mbtilesexport/OSMBright_Level9.mbtiles /gevol/mbtilesexport


Import a directory into a `mbtiles` file

    mb-util directory World_Light.mbtiles

## Requirements

* Python `>= 2.6`

## Metadata

MBUtil imports and exports metadata as JSON, in the root of the tile directory, as a file named `metadata.json`.

```javascript
{
    "name": "World Light",
    "description": "A Test Metadata",
    "version": "3"
}
```

## Testing

This project uses [nosetests](http://readthedocs.org/docs/nose/en/latest/) for testing. Install nosetests
and run

    nosetests

## See Also

* [node-mbtiles provides mbpipe](https://github.com/mapbox/node-mbtiles/wiki/Post-processing-MBTiles-with-MBPipe), a useful utility.

## License

BSD - see LICENSE.md

## Orriginal Authors

- Tom MacWright (tmcw)
- Dane Springmeyer (springmeyer)
- Mathieu Leplatre (leplatrem)

## GME Components Added By

- Sean Wohltman (Prindle19)
