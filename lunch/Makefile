# Makefile for lunch.pdf

SOURCES         = lunch1.svg lunch2.svg prices.json
TARGET          = lunch.pdf
DPI             = 300

.PHONY: all lunch clean cleaner

all: lunch

lunch: lunch.pdf

#@cmd="convert"; for inp in $(filter %.svg,$^); do cmd+=" -density $(DPI) -quality $(QUALITY) -page $(OUT_WIDTH_IN)x$(OUT_HEIGHT_IN) $$inp"; done; cmd+=" $@"; echo $$cmd; $$cmd
#@cmd="inkscape --export-filename=$@ --export-dpi=$(DPI) $(filter %.svg,$^)"; echo $$cmd; $$cmd
#@cmd="gs -dBATCH -dNOPAUSE -q -r$(DPI) -g$(OUT_WIDTH)x$(OUT_HEIGHT) -sDEVICE=pdfwrite -sOutputFile=$@ $@-tmp.pdf"; echo $$cmd; $$cmd
%.pdf: %.svg prices.json
	@cmd="rsvg-convert --dpi-x $(DPI) --dpi-y $(DPI) -f pdf -o $@ $(filter %.svg,$^)"; echo $$cmd; $$cmd
	@mv $@ $@-tmp.pdf
	@cmd="gs -dBATCH -dNOPAUSE -q -sDEVICE=pdfwrite -sOutputFile=$@ $@-tmp.pdf"; echo $$cmd; $$cmd
	@rm $@-tmp.pdf

lunch.pdf: lunch1.pdf lunch2.pdf
	@cmd="gs -dBATCH -dNOPAUSE -sDEVICE=pdfwrite -sOutputFile=$@ $^"; echo $$cmd; $$cmd

clean:
	@echo rm lunch1.pdf && [ -f lunch1.pdf ] && rm lunch1.pdf || true
	@echo rm lunch2.pdf && [ -f lunch2.pdf ] && rm lunch2.pdf || true

cleaner: clean
	@echo rm lunch.pdf && [ -f lunch.pdf ] && rm lunch.pdf || true
