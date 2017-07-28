.PHONY: build softclean clean forwardsearch

SRCDIR = src
BLDDIR = bld
AUXDIR = tmp
SVGDIR = svg-inkscape

SCRFILE = paper.tex
DEPS = $(wildcard $(SRCDIR)/*.tex $(SRCDIR)/*.bib)
TARGET = $(BLDDIR)/$(subst .tex,.pdf,$(SCRFILE))

build: $(TARGET)

$(TARGET): $(DEPS)

$(BLDDIR)/%.pdf: $(SRCDIR)/%.tex
	mkdir -p $(BLDDIR)
	mkdir -p $(AUXDIR)
	latexmk -output-directory=$(BLDDIR) -aux-directory=$(AUXDIR) -pdf -synctex=1 -shell-escape -halt-on-error $<

# cygstart sumatrapdf.exe -reuse-instance $(BLDDIR)/$(subst .tex,.pdf,$(SCRFILE))

forwardsearch:
	cygstart sumatrapdf -reuse-instance $(BLDDIR)/$(subst .tex,.pdf,$(SCRFILE)) -forward-search $(LNFILE) $(LN)

clean: softclean
	-rm -rf $(AUXDIR)
	-rm -rf $(SVGDIR)

softclean:
	-rm -rf $(BLDDIR)