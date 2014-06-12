# specify your main target here:
all: collection.pdf #clean

# specify the main file and all the files that you are including
SOURCE=collection.tex mybibliography.bib \
chapters/01intro.tex chapters/02history.tex chapters/03relatedness.tex chapters/04position.tex chapters/05kinship.tex chapters/06numerals.tex \
chapters/07elevation.tex chapters/08arithmetic.tex chapters/09plural.tex
	

%.pdf: %.tex $(SOURCE)
	xelatex $*
	bibtex $*
	bibtex collection1-blx
	bibtex collection2-blx
	bibtex collection3-blx
	bibtex collection4-blx
	bibtex collection5-blx
	bibtex collection6-blx
	bibtex collection7-blx
	bibtex collection8-blx
	bibtex collection9-blx
	xelatex $*
	xelatex $*

clean:
	rm -f *.bak *~ *.log *.blg *.bbl *.aux *.toc *.cut *.out *.tmp *.tpm *.adx *.adx.hyp *.idx *.ilg *.ind \
	*.and *.glg *.glo *.gls *.wdx *.wnd *.wrd *.wdv *.ldx *.lnd *.rdx *.rnd *.xdv 

realclean: clean
	rm -f *.dvi *.ps *.pdf



