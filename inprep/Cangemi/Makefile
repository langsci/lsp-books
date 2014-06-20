# specify your main target here:
all: cangemi.pdf

# specify teh main file and all the files that you are including
SOURCE=cangemi.bib	cangemi.tex	chapter1.tex	chapter2.tex	chapter3.tex	chapter4.tex	chapter5.tex	chapter6.tex LSP/langsci.cls 



%.pdf: %.tex $(SOURCE)
	xelatex -no-pdf $* |grep -v math
	bibtex -min-crossrefs=200 $*
	xelatex -no-pdf $* |grep -v math
	bibtex -min-crossrefs=200 $*
	xelatex $* -no-pdf |egrep -v 'math|PDFDocEncod' |egrep 'Warning|label|aux'
	correct-toappear
	correct-index
	makeindex -o $*.ind $*.idx
	makeindex -o $*.lnd $*.ldx
	makeindex -o $*.wnd $*.wdx
	LSP/bin/reverse-index <$*.wdx >$*.rdx
	makeindex -o $*.rnd $*.rdx
	\rm $*.adx
	authorindex -i -p $*.aux > $*.adx
	sed -e 's/}{/|hyperpage}{/g' $*.adx > $*.adx.hyp
	makeindex -o $*.and $*.adx.hyp
	xelatex $* | egrep -v 'math|PDFDocEncod' |egrep 'Warning|label|aux'


# http://stackoverflow.com/questions/10934456/imagemagick-pdf-to-jpgs-sometimes-results-in-black-background
cover: cangemi.pdf
	convert $*.pdf\[0\] -resize 486x -background white -alpha remove -bordercolor black -border 2  cover.png

# convert $*.pdf\[0\] -resize 486x -background white -alpha remove -bordercolor black -border 2  cover.png

# 204x303 with a 2x2 margin it has to be 200x299
#convert tmp.pdf\[0\] -resize x299 -background white -alpha remove -bordercolor black -border 2  -quality 100 cover.png


# does not seem to have any effect:
# http://www.imagemagick.org/script/command-line-options.php#quality


public: lsp-guidelines.pdf
	scp -p lsp-guidelines.pdf www-adm@home.hpsg.fu-berlin.de:/home/www-adm/doc-langsci/omp/Meta/


commit:


o-public: /Users/stefan/public_html/Pub/lsp-guidelines.pdf /Users/stefan/public_html/Pub/lsp-guidelines.2.pdf commit
	scp -p /Users/stefan/public_html/Pub/lsp-guidelines.pdf /Users/stefan/public_html/Pub/lsp-guidelines.2.pdf home.hpsg.fu-berlin.de:public_html/Pub/


clean:
	rm -f *.bak *~ *.log *.blg *.bbl *.aux *.toc *.cut *.out *.tmp *.tpm *.adx *.adx.hyp *.idx *.ilg *.ind \
	*.and *.glg *.glo *.gls *.wdx *.wnd *.wrd *.wdv *.ldx *.lnd *.rdx *.rnd *.xdv 

realclean: clean
	rm -f *.dvi *.ps *.pdf



