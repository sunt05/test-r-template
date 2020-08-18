---
title: 'A Python-enhanced urban land surface model SuPy (SUEWS in Python, v2019.2): development, deployment and demonstration'

journal: "gmd"
author:
  - given_name: Ting
    surname: Sun
    orcid: 0000-0002-2486-6146
    affiliation: 1
    email: ting.sun@reading.ac.uk
    corresponding: true
  - given_name: Sue
    surname: Grimmond
    affiliation: 1
    email: c.s.grimmond@reading.ac.uk
    # corresponding: true

affiliation:
  - code: 1
    address: Department of Meteorology, University of Reading, Reading, RG6 6BB, UK
  # - code: 2
  #   address: Psychoceramics, Wesleyan University, Middletown, CT, United State


# If you have more than one corresponding author, add them manually using the following structure:
# Two authors: \correspondence{Daniel Nüst (daniel.nuest@uni-muenster.de) and Josiah Carberry (j.carberry@orcid.org)}
# Three authors or more: \correspondence{Daniel Nüst (daniel.nuest@uni-muenster.de), Josiah Carberry j.carberry@orcid.org), and Markus Konkol (m.konkol@wwu.de)}
# If the following line is uncommented, the "corresponding: true" above are ignored
# correspongdingauthors: Daniel Nüst (daniel.nuest@uni-muenster.de) and Josiah Carberry (j.carberry@orcid.org)

Date: 10 Feb 2019

abstract: |
  Accurate and agile modelling of the climate of cities is essential for urban climate services. The Surface Urban Energy and Water balance Scheme (SUEWS) is a state-of-the-art, widely used, urban land surface model (ULSM) which simulates urban-atmospheric interactions by quantifying the energy, water and mass fluxes. Using SUEWS as the computation kernel, SuPy (SUEWS in Python), stands on the Python-based data stack to streamline the pre-processing, computation and post-processing that are involved in the common modelling-centred urban climate studies. This paper documents the development of SuPy, which includes the SUEWS interface modification, F2PY (Fortran to Python) configuration and Python frontend implementation. In addition, the deployment of SuPy via PyPI (Python Package Index) is introduced along with the automated workflow for cross-platform compilation. This makes SuPy available for all mainstream operating systems (Windows, Linux, and macOS). Furthermore, three online tutorials in Jupyter notebooks are provided to users of different levels to become familiar with SuPy urban climate modelling. The SuPy package represents a significant enhancement that supports existing and new model applications, reproducibility, and enhanced functionality.


# bibliography: sample.bib
running:
  title: R Markdown Template for Copernicus
  author: Nüst et al.
competinginterests: |
  The authors declare no competing interests.
# OPTIONAL:
algorithms: true
# See https://publications.copernicus.org/for_authors/licence_and_copyright.html, normally used for transferring the copyright, if needed.
copyrightstatement: |
  The author's copyright for this publication is transferred to institution/company.
availability:
  #  use this to add a statement when having only software code available
  #  use this to add a statement when having only data sets available
  # code: |
  # data: |
  codedata: |
    use this to add a statement when having data sets and software code available
  sample: |
    use this section when having geoscientific samples available
videosupplement: |
  use this section when having video supplements available
authorcontribution: |
  Daniel wrote the package. Josiah thought about poterry. Markus filled in for a second author.
disclaimer: |
  We like Copernicus.
acknowledgements: |
  Thanks to the rticles contributors!
appendix: |
  \section{Figures and tables in appendices}
  \subsection{Option 1}
  If you sorted all figures and tables into the sections of the text, please also sort the appendix figures and appendix tables into the respective appendix sections.
  They will be correctly named automatically.
  \subsection{Option 2}
  If you put all figures after the reference list, please insert appendix tables and figures after the normal tables and figures.

  `\appendixfigures` needs to be added in front of appendix figures
  `\appendixtables` needs to be added in front of appendix tables

  Please add `\clearpage` between each table and/or figure. Further guidelines on figures and tables can be found below.
  Regarding figures and tables in appendices, the following two options are possible depending on your general handling of figures and tables in the manuscript environment:
  To rename them correctly to A1, A2, etc., please add the following commands in front of them:

output:
  custom_document:
    # for PDF output
    template: 'template.tex'
    path: Manuscript.pdf
    pandoc_args: [
      '--filter=pandoc-crossref'

      ]

export_on_save:
  pandoc: true

# listings: true

---

## test section

To address these considerations, SuPy's architecture uses Python's data processing and Fortran's computational efficiency. SuPy consist of three parts (@fig:schematic):

1)  *SUEWS*: a Fortran-coded local scale urban land surface model of moderate complexity that can simulate the urban surface energy balance in combination with the complete urban hydrological cycle, considering irrigation and runoff processes (Grimmond and Oke, 1986, Grimmond and Oke 1991, Grimmond et al. 1991, Offerle et al. 2003, Järvi et al. 2011, Jarvi et al. 2014, Ward et al. 2016).

2)  *SuPy\_driver*: calculation kernel compiled by F2PY (Fortran to Python, part of the NumPy package) (Peterson, 2009) to facilitate the transfer of SUEWS Fortran modelling ability to Python and guarantee the computational performance.

3)  *SuPy:* a Python-based frontend processor using pandas `DataFrame` and derived functionality for data analysis and simulation management.

![SuPy's three major components (left to right): a) SUEWS, a
Fortran-coded local scale urban land surface model; b) SuPy\_driver, the
calculation kernel compiled by F2PY; c) SuPy, a Python-based frontend
processor](./image1.png){#fig:schematic width=90%}
