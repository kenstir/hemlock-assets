Introduction
============
This is the public repo for image assets used (imported as a submodule) by the Hemlock
[Android](https://github.com/kenstir/hemlock) and
[iOS](https://github.com/kenstir/hemlock-ios) mobile apps.
Here you will find the assets themselves, and the SVG files they were created from.


How to add a new icon for Android
=================================
1. Edit the SVG in Inkscape and resize the canvas to the proper size (File >> Document Properties)
   * 640 x 512px for the Grid Main Screen
   * 576 x 512px for the List Main Screen
2. Add layers to add color as desired
   * move path to layer "outline"
   * add color to layer "fill"
3. Import into Android Studio
   * Select hemlock-assets in project view
   * File >> New >> Vector Asset
   * Change the size
     - 60 x 48dp for the Grid Main Screen
     - 45 x 36dp for the Grid Main Screen bottom row of buttons
     - 54 x 48dp for the List Main Screen
   * Add "_48" or "_36" to the name
5. Fix in Android Studio
   * Replace "currentColor" with "#000000" in the .xml
   * Ctrl+A and Alt+Ctrl+L to Reformat Code
   * Remove license block


How to export icons as PNG for iOS
==================================
1. Edit the SVG in Inkscape and resize the canvas to the proper size (File >> Document Properties)
   * 640 x 512px for the Grid Main Screen
   * 576 x 512px for the List Main Screen
2. Use the Inkscape command line to export full size PNG files
   ```bash
   PATH=$PATH:/c/Program\ Files/Inkscape/bin
   for i in *.svg; do inkscape.exe --export-type="png" $i; done
   ```
3. For List Main Screen only, use the Inkscape GUI to export material-magnify.svg as 576 x 512px
4. Use the ImageMagick command line to generate 1x, 2x, 3x versions
   ```bash
   mkdir 1x 2x 3x
   for i in *.png; do
       base=${i%.png}
       cp $i 1x/${base}-1x.png;  magick mogrify -resize  8% 1x/${base}-1x.png
       cp $i 2x/${base}-2x.png;  magick mogrify -resize 16% 2x/${base}-2x.png
       cp $i 3x/${base}-3x.png;  magick mogrify -resize 24% 3x/${base}-3x.png
   done
   ```
