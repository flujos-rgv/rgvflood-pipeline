# Vector Tile Parser

## Prerequisites

You need to make sure that you have [`gdal`](https://formulae.brew.sh/formula/gdal), `ogr2ogr`, and [`tippecanoe`](https://formulae.brew.sh/formula/tippecanoe) installed. You can install these using homebrew.

```
brew install gdal
brew install tippecanoe
```

Since `ogr2ogr` is part of `gdal`, you don't need to install that separately. Note that you do **NOT** need to run npm install, since there are no npm dependencies used in this pipeline.

Once you have these, you can run the script with `bash prepareTiles [EVENT-ID] flood`. Read the next section first to make sure that your data is in the right format.

## Structure

In order for the script to run successfully, you have to make sure that the planetscope and sentinel files are in the right place.

```
prepareTiles
input
  event-2
    planetscope
      sample_planetscope.tif
    sentinel
      sample_sentinel.tif
```

Once you run the `prepareTiles` script, you will have a `tiles` folder with the tiles for each event.

```
prepareTiles
input
tiles
  event-2
    flood
      0
      1
      2
      3
      ...
```

You can either drop individual events from the tiles folder directly into `/public/tiles/` of the floodmaps app, or just copy the entire `tiles` folder into `/public` of the floodmaps app.

## Example process

Put a new event (e.g. `event-16`) into the input folder with the correct separation of sentinel and planetscope files in separate subfolders.

Run the script:

```shell
bash prepareTiles event-16 flood
```

Once the script is done, move the event created in the `tiles` folder into the floodmaps app under `/public/tiles/`.
