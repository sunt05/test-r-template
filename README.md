# test-r-template

Please test the `pandoc`-based generation using the following (tested on macOS 10.15.6 with pandoc 2.9.1.1):
```
pandoc -f markdown+tex_math_single_backslash -o Manuscript.pdf --pdf-engine=pdflatex --template=template.tex --filter=pandoc-crossref test.md
```
