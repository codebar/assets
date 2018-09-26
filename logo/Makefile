# This Makefile creates the logo in different formats based on the svg version
#  in svg/codebar-logo.svg. A Makefile specifies how a specific file should
#  be created. If that file needs a different file to work on,  e.g. like the
#  jpg files that need the png files, Make will create the png's first using
#  the recipe specified for them.
#
# To create the images, make, imagemagick and inkscape need to be installed.
# On Mac, make should come with XCode (https://developer.apple.com/xcode/),
#  imagemagick can be installed using brew (`brew install imagemagick`)
#  and inkscape is available as a package from https://inkscape.org/
#
# On Linux, all three applications should be available in your package-manager
#  where `make` comes with `build-essentials` on Ubuntu & `base-devel` on Arch
#
# If you want to update all rasterized versions, issuing `make all` should
#  re-create all files. If Make reports `make: Nothing to be done for 'all'.`,
#  that means the source file (the svg) hasn't changed and thus Make does not
#  need to recreate the rasterized versions.
#
# If you want to force re-creation, issue `make clean`, which will delete all
#  rasterized versions and then will force `make all` to re-create them.

# Create all derived formats using the recipes below
all: eps/codebar-logo.eps png/codebar-logo.png png/codebar-logo-160x160.png png/codebar-logo-300x300.png jpg/codebar-logo.jpg jpg/codebar-logo-160x160.jpg jpg/codebar-logo-300x300.jpg

# clean is .PHONY because it doesn't create a file.
#  it will delete all derived files. Usually you won't need this.
#  (https://www.gnu.org/software/make/manual/html_node/Phony-Targets.html)
.PHONY: clean
clean:
	rm eps/codebar-logo.eps
	rm png/codebar-logo*.png
	rm jpg/codebar-logo*.jpg

# Create an EPS version of the logo
#
# A 'target' can be read as
# > In order to create eps/codebar-logo.eps
# > Issue the following command that requires svg/codebar-logo.svg to be present
eps/codebar-logo.eps: svg/codebar-logo.svg
	inkscape -z -E eps/codebar-logo.eps svg/codebar-logo.svg

# Create the logo as a PNG at different resolutions (300dpi, 160x160px, 300x300px)
png/codebar-logo.png: svg/codebar-logo.svg
	inkscape -z -e png/codebar-logo.png -d 300 svg/codebar-logo.svg

png/codebar-logo-160x160.png: svg/codebar-logo.svg
	inkscape -z -e png/codebar-logo-160x160.png -w 160 svg/codebar-logo.svg

png/codebar-logo-300x300.png: svg/codebar-logo.svg
	inkscape -z -e png/codebar-logo-300x300.png -w 300 svg/codebar-logo.svg

# '-background white -alpha remove' so that transparency is replaced with white
#  as convert would by default replace transparency (alpha) with black.
# command uses 'png/codebar-logo' as a source because convert is bad at
#  converting the source file, the svg, so we use the already rasterized png.
#
# If the corresponding png is not present, Make will issue the command above
#  to create the png file from the svg first.
jpg/codebar-logo.jpg: png/codebar-logo.png
	convert png/codebar-logo.png -background white -alpha remove jpg/codebar-logo.jpg

jpg/codebar-logo-160x160.jpg: png/codebar-logo-160x160.png
	convert png/codebar-logo-160x160.png -background white -alpha remove jpg/codebar-logo-160x160.jpg

jpg/codebar-logo-300x300.jpg: png/codebar-logo-300x300.png
	convert png/codebar-logo-300x300.png -background white -alpha remove jpg/codebar-logo-300x300.jpg
