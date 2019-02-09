## codebar assets

For reference on how to use any of our assets please visit [manual.codebar.io/brandbook](http://manual.codebar.io/brandbook.html)

If you have any questions about the fair usage of these assets please email hello@codebar.io.

### Re-creating the logos

If you changed a logo or added another one in SVG format, you can automatically create rasterized versions using the [Makefile](logo/Makefile).

To create the images, make, imagemagick and inkscape need to be installed. On Mac, make should come with [XCode](https://developer.apple.com/xcode/), imagemagick can be installed using brew (`brew install imagemagick`) and inkscape is available as a package from https://inkscape.org/

On Linux, all three applications should be available in your package-manager, where `make` comes with `build-essentials` on Ubuntu & `base-devel` on Arch

If all these applications are installed, running

```
make all
```

in `logo/` should recreate rasterized versions for all SVGs that have changed. If you added a new logo, a new PHONY recipe needs to be created like for [`codebar-logo`](logo/Makefile#L30-L31) and that recipe needs to be added to the [`all` recipe](logo/Makefile#L24).


##### All content in this repo is Copyright © 2019 codebar Ltd, 10791813. All rights reserved.
