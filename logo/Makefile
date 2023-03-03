# This Makefile creates the logo in different formats based on the svg version
#  in svg/codebar-logo.svg. A Makefile specifies how a specific file should
#  be created. 
#
# To create the images, make and inkscape need to be installed.
# On Mac, make should come with XCode (https://developer.apple.com/xcode/),
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
all: codebar-logo codebar-logo-banner

## the next tasks are marked as .PHONY because they don't create a specific file
##  (https://www.gnu.org/software/make/manual/html_node/Phony-Targets.html)

# This recipe will create all derived formats for codebar-logo
.PHONY: codebar-logo
codebar-logo: eps/codebar-logo.eps png/codebar-logo-72dpi.png png/codebar-logo-300dpi.png 

# This recipe will create all derived formats for codebar-logo-banner
.PHONY: codebar-logo-banner
codebar-logo-banner: eps/codebar-logo-banner.eps png/codebar-logo-banner-72dpi.png png/codebar-logo-banner-300dpi.png 

#  clean will delete all derived files. Usually you won't need this.
.PHONY: clean
clean:
	rm eps/*.eps
	rm png/*.png

# Create an EPS format in eps/ of a file that exists in svg/
#  If you invoke `make eps/codebar-logo.eps` Make will look for
#  a file called svg/codebar-logo.svg (or another recipe that creates said file)
#  it will then substitute $@ with the target filename (eps/codebar-logo.eps)
#  and $< with the source filename (svg/codebar-logo.svg).
#
#  This recipe thus reads as: In order to create a file matching eps/%.eps,
#  I need a corresponding file in svg/ to exist and will call this command to
#  create the eps file.
eps/%.eps: svg/%.svg
	inkscape -z -E $@ $<

# Creates a 300dpi rasterized version of an svg in png format
png/%-300dpi.png: svg/%.svg
	inkscape -z -e $@ -d 300 $<

png/%-72dpi.png: svg/%.svg
	inkscape -z -e $@ -d 72 $<

