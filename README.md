# test-r-template

## background

this repo is a minimal test case for the issue [here](https://github.com/rstudio/rticles/issues/273).

## test

### successful case with modified template

`template.tex` is a modified version of `template_orig.tex`, in which line 84–86 are activated.

Please test the `pandoc`-based generation using the following (tested on macOS 10.15.6 with pandoc 2.9.1.1):
```
pandoc -f markdown+tex_math_single_backslash -o Manuscript.pdf --pdf-engine=pdflatex --template=template.tex --filter=pandoc-crossref test.md
```
### erroneous case with original template

`template_orig.tex` is the original template file, with which the following command would produce an error (down below):
```
pandoc -f markdown+tex_math_single_backslash -o Manuscript.pdf --pdf-engine=pdflatex --template=template_orig.tex --filter=pandoc-crossref test.md
```

error:
```
Error producing PDF.
! You can't use `\spacefactor' in vertical mode.
\@->\spacefactor
                 \@m {}
l.77 \@

```