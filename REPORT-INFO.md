# Project Report Guidelines

Your report should include the following sections (you can modify the titles as appropriate):

0. Title, your name & affiliation

1. Introduction and Motivation: introduce the need for your software package; what problem is it trying to solve? This should be relate to your research.

2. Methodology: governing equations, description of the physical problem, etc. This should not include the software details, as those go in the next section.

3. Implementation: description of the software design, layout, functionality. What modules and classes comprise your software? How does someone run it, and how do they interact with it? (e.g., command-line arguments, input file, GUI). What packages does your software depend on? 

4. Results: show sample results based on the functionality of your code. Keep in mind some of the plotting practices we talked about.

5. Conclusions and future work: summarize the report, describe the overall functionality of your software. How can this software evolve, what else would you want to add to it moving forward? (Or what would you want others to add to it?) How do you see this being used?

There is no length requirement, but generally 5–15 pages would be appropriate for this amount of content. (Longer is not necessarily better.) 

**Make sure you cite your software** as we talked about in class---use Zenodo to archive the final version of your software and then use the resulting DOI to cite. You can format the reference like this (replace elements with the specifics of your software: 

> {Your name}. (2019) {Your software} v{version number} [software]. Zenodo. https://doi.org/xxxx/xxxxx

or using BibTeX:
```TeX
@misc{yoursoftware,
    author = {First Middle Last},
    year = 2019,
    title = {software v0.1.0},
    doi = {10.5281/zenodo.xxxx},
    url = {https://github.com/...},
}
```

Please submit the report as a PDF.
I recommend using LaTeX and formatting this like a typical journal article submission (e.g., using the Elsevier article class), but you can use what you prefer. The idea behind this report is that it could serve as the seed for a later software paper about your package.

Your report grade will be based on how you meet the above content items, as well as readability of both your writing and any figures.
