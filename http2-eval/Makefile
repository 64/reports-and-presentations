.PHONY: all clean spell

TEXSRCS := $(shell find . -maxdepth 1 -name "*.tex")
TEXFLAGS := -shell-escape -quiet main.tex

all: $(TEXSRCS)
	@cp *.tex build/
	@cp img/* build/
	@cp references.bib build/
	@cd build && pdflatex $(TEXFLAGS)
	@cd build && biber main
	@cd build && pdflatex $(TEXFLAGS)
	@cd build && pdflatex $(TEXFLAGS)

clean:
	rm -rf build/*

spell:
	for src in $(TEXSRCS); do aspell -t -c $$src; done
