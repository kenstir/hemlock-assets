NOTICE
======
This is a private repo and no rights are granted to distribute anything.


Provenance of SVG Files
=======================
The source files under svg/ came from various places:
* fontawesome5/*.svg are from fontawesome.com version 5 where I am a Pro member.
* fontawesome6/*.svg are from fontawesome.com version 6 where I am a Pro member.
* hemlock-*.svg are edited by me.
* material-magnify.svg is from material.io (now https://pictogrammers.com/library/mdi/icon/magnify/)
* thenounproject/*.svg are from thenounproject.com where I am a NounPro member.


How to add a new icon (Android)
===============================
1. Download .svg from e.g. https://fontawesome.com/v5/icons/calendar-day?f=classic&s=light&rt=flip-horizontal
2. Open in Inkscape and resize canvas (File >> Document Properties)
   * 576 x 512px for cwmars
   * 640 x 512px for acorn (MainGridActivity)
3. Add layers
   * move path to layer "outline"
   * add cwmars color to layer "cwmars fill"
4. Import into Android Studio
   * Select hemlock-pro-assets in project view
   * File >> New >> Vector Asset
   * Change the size
     - 54 x 48dp for cwmars
     - 60 x 48dp for acorn main grid
     - 45 x 36dp for acorn main grid bottom row
   * Add "_48" or "_36" to the name
5. Fix in Android Studio
   * Replace "currentColor" with "#000000" in the .xml
   * Ctrl+A and Alt+Ctrl+L to Reformat Code
   * Remove license block


How to export icons as PNG for iOS
==================================
1. Use the Inkscape command line to export full size
   ```bash
   PATH=$PATH:/c/Program\ Files/Inkscape/bin
   for i in *.svg; do inkscape.exe --export-type="png" $i; done
   ```
2. Use the Inkscape GUI to export material-magnify.svg as 576 x 512px
   (NB: skip for acorn)
3. Use the ImageMagick command line to generate 1x, 2x, 3x versions
   ```bash
   mkdir 1x 2x 3x
   for i in *.png; do
       base=${i%.png}
       cp $i 1x/${base}-1x.png;  magick mogrify -resize  8% 1x/${base}-1x.png
       cp $i 2x/${base}-2x.png;  magick mogrify -resize 16% 2x/${base}-2x.png
       cp $i 3x/${base}-3x.png;  magick mogrify -resize 24% 3x/${base}-3x.png
   done
   ```
