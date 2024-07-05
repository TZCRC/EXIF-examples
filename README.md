# EXIF-examples

A variety of image files with embedded EXIF metadata. Each folder is titled with the camera model.


## Working with metadata

[ExifTool](https://exiftool.org) is terrific for command-line extraction of data, manipulation / geotagging, and renaming of files.

To produce the exifdata csv file I used:

```
exiftool -n -common -csv -r . > exifdata.csv
```

### Copy from an SD card, rename and georeference in one step

Copy from an SD card (Nikon folder example) to another, renaming by datetime and geotagging from GPX. This takes no longer than copying the files from the SD card in the first place - and eliminates the long copy time when geotagging later (which by necessity rewrites the entire file).

```
exiftool -r /Volumes/NIKON\ D5600/DCIM/ \ # Source directory
  -d %Y%m%d%H%M%S%%-c.%%le \ # Read capture datetime and produce YYYYMMDDHHMMSS format
  '-filename<PREFIX_${DateTimeOriginal}' \ # Rename with a prefix (camera / aircraft?) + date
  -geotag GPXFILE.gpx # the source GPX file
```
