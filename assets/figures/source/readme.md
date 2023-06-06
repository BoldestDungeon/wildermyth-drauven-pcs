== EXPORTING PHOTOSHOP LAYERS TO IMAGE FILES

The "ImageMagick" tool is a command-line tool that can be used to convert all layers in a `.psd` file to individual `.png` files.

Once installed, the command to use is:

```convert -dispose Background DrauvenMystic.psd -layers coalesce -set filename:layers %l 'export/DrauvenMystic_%[filename:layers].png'  ```

(Where you replace `DrauvenMystic.psd` with the name of the file you wish to export from and `DrauvenMystic_` with the correct prefix for the files you wish to create.)
