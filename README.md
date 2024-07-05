# EXIF-examples

A variety of image files with embedded EXIF metadata. Each folder is titled with the camera model.

ExifTool is terrific for command-line extraction of data, manipulation / geotagging, and renaming of files.

To produce the exifdata csv file I used:

```
exiftool -n -common -csv -r . > exifdata.csv
```
