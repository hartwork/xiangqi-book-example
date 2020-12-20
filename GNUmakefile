# Copyright (C) 2020 Sebastian Pipping <sebastian@pipping.org>
# Licensed under Creative Commons Attribution 4.0 International (CC BY 4.0)

SETUP_WXF_FILES = $(wildcard setups/*.wxf)
SETUP_SVG_FILES = $(patsubst %.wxf,%.svg,$(SETUP_WXF_FILES))
SETUP_PDF_FILES = $(patsubst %.svg,%.pdf,$(SETUP_SVG_FILES))


.PHONY: all
all: book.pdf

.PHONY: clean
clean:
	$(RM) book.pdf $(SETUP_SVG_FILES) $(SETUP_PDF_FILES)
	$(RM) -R tmp/ venv/

tmp:
	mkdir $@
	
venv:
	python3 -m venv venv

venv/bin/xiangqi-setup: | venv
	venv/bin/pip install 'xiangqi-setup<2.0.0'

setups/%.pdf: setups/%.svg
	inkscape --export-filename=$@ $^

setups/%.svg: setups/%.wxf GNUmakefile | venv/bin/xiangqi-setup
	# IMPORTANT: Before changing themes
	#            please check if the theme's license fits your intended use!
	venv/bin/xiangqi-setup --board clean_alpha --pieces retro_simple $< $@

book.pdf: book.tex $(SETUP_PDF_FILES) | tmp
	pdflatex -output-directory tmp $< && ln -f tmp/$@ $@
