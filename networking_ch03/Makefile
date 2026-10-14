SHELL=/bin/bash
.PHONY: pdf clean
pdf:
	latexmk -lualatex -interaction=nonstopmode -halt-on-error -file-line-error main.tex
clean:
	latexmk -c main.tex