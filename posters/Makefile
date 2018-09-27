.PHONY: clean

all: coaching_101_300dpi.pdf coaching_101_300dpi.png

clean:
	rm *.png
	rm *.pdf

coaching_101_%dpi.pdf:
	inkscape \
		--without-gui \
		--export-text-to-path \
		--export-dpi=$* \
		--export-pdf=$@ \
		--export-pdf-version=1.4 \
		 coaching_101.svg

# $* is the number matched before dpi
# $@ is the target file name
coaching_101_%dpi.png:
	inkscape \
		--without-gui \
		--export-dpi=$* \
		--export-png=$@ \
		coaching_101.svg
