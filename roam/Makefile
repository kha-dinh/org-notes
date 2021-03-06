# Latex Makefile using latexmk
# Modified by Dogukan Cagatay <dcagatay@gmail.com>
# Originally from : http://tex.stackexchange.com/a/40759
#
# Change only the variable below to the name of the main tex file.
PROJNAME=$(shell basename $(CURDIR))


# You want latexmk to *always* run, because make does not have all the info.
# Also, include non-file targets in .PHONY so they are run regardless of any
# file of the given name existing.
.PHONY: $(PROJNAME).pdf all clean

# The first rule in a Makefile is the one executed by default ("make"). It
# should always be the "all" rule, so that "make" and "make all" are identical.
all: $(PROJNAME).pdf

# CUSTOM BUILD RULES

# In case you didn't know, '$@' is a variable holding the name of the target,
# and '$<' is a variable holding the (first) dependency of a rule.
# "raw2tex" and "dat2tex" are just placeholders for whatever custom steps
# you might have.

%.tex: %.raw
	./raw2tex $< > $@

%.tex: %.dat
	./dat2tex $< > $@

# MAIN LATEXMK RULE

# -pdf tells latexmk to generate PDF directly (instead of DVI).
# -pdflatex="" tells latexmk to call a specific backend with specific options.
# -use-make tells latexmk to call make for generating missing files.

# -interactive=nonstopmode keeps the pdflatex backend from stopping at a
# missing file reference and interactively asking you for an alternative.


PDFLATEX_OPT=-synctex=1 -interaction=nonstopmode -file-line-error

# $(PROJNAME).pdf: main.tex
# 	latexmk  --jobname=$(PROJNAME) -pdf \
# 	-pdflatex=$(PDFLATEX_OPT) -use-make $<


$(PROJNAME).pdf: main.tex
	latexmk  -f -pdf \
	-xelatex $(PDFLATEX_OPT) -use-make $<

cleanall:
	rm -rf *.aux *.bbl *.blg *.fdb_latexmk  \
	*.fls *.log *.out *.nav *.snm *.toc *.synctex.gz *.pdf *.xdv

clean:
	rm -rf *.aux *.bbl *.blg *.fdb_latexmk  \
	*.fls *.log *.out *.nav *.snm *.toc *.synctex.gz *.pdf *.xdv

