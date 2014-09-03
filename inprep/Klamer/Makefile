# specify your main target here:
all: collection.pdf

# specify the main file and all the files that you are including
SOURCE= collection.tex 
	 
%.pdf: %.tex $(SOURCE)
	xelatex -no-pdf collection 	 
	for i in {1..11}; do  echo ======$i;  bibtex -min-crossrefs=200 collection$i-blx; done
	xelatex  -no-pdf collection
	makeindex -o collection.ind collection.idx
	makeindex -o collection.lnd collection.ldx
#	makeindex -o collection.wnd collection.wdx
#	LSP/bin/reverse-index <collection.wdx >collection.rdx
#	makeindex -o collection.rnd collection.rdx 
# 	authorindex -i -p collection.aux > collection.bib.adx
	sed 's/|hyperpage//' collection.adx > collection.txt.adx 
	cat collection.bib.adx collection.txt.adx > collection.combined.adx
	sed -e 's/}{/|hyperpage}{/g' collection.adx > collection.adx.hyp
	makeindex -o collection.and collection.combined.adx
	xelatex -no-pdf collection 
	xelatex collection 


cover: collection.pdf
	convert collection.pdf\[0\] -resize 486x -background white -alpha remove -bordercolor black -border 2  cover.png

clean:
	rm -f *.bak *~ *.log *.blg *.aux *.toc *.cut *.out *.tmp *.tpm *.adx *.adx.hyp *.idx *.ilg \
	*.and *.glg *.glo *.gls *.wdx *.wnd *.wrd *.wdv *.ldx *.lnd *.rdx *.rnd *.xdv 

realclean: clean
	rm -f *.dvi *.ps *.pdf *.bbl
