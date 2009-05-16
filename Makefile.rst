include $(HOME)/Library/Make/rst.conf

%.html: %.rst
	$(RST2HTML) --stylesheet-path=$(HOME)/Library/Make/rst-styles/$(STYLESHEET) $< $@

%.tex: %.rst
	$(RST2LATEX) $< $@

%.dvi: %.tex
	cd `dirname $<` && $(LATEX) $< && $(LATEX) $<

%.pdf: %.dvi
	$(DVIPDFM) -o $@ $<

