---
name: freud-2020
title: "freud: subtitle"
author: "Bradley Dice"
mentor-names: "Doaa Altarawy"
full-author-list:
    - name: "Bradley D. Dice"
      affiliation: 1
    - name: "Second Author"
      affiliation: 2
    - name: "Third Author"
      affiliation: 2
affiliations:
    - name: "The Molecular Sciences Software Institute"
      address: "Blacksburg, VA"
      index: 1
    - name: "Department of Chemistry, Virginia Tech University"
      index: 2
      address: "Blacksburg, VA"
toc: true
toc_sticky: true
toc_label: "Poster Contents"
layout: poster
---

<div>
  <a href="https://freud.readthedocs.io/en/stable/reference/citing.html"><img style="display:inline;" title="Citing freud" src="https://img.shields.io/badge/cite-freud-informational.svg" /></a>
  <a href="https://pypi.org/project/freud-analysis/"><img style="display:inline;" title="PyPI" src="https://img.shields.io/pypi/v/freud-analysis.svg" /></a>
  <a href="https://anaconda.org/conda-forge/freud"><img style="display:inline;" title="conda-forge" src="https://img.shields.io/conda/vn/conda-forge/freud.svg" /></a>
  <a href="https://freud.readthedocs.io/en/latest/?badge=latest"><img style="display:inline;" title="ReadTheDocs" src="https://readthedocs.org/projects/freud/badge/?version=latest" /></a>
  <a href="https://mybinder.org/v2/gh/glotzerlab/freud-examples/master?filepath=index.ipynb"><img style="display:inline;" title="Binder" src="https://mybinder.org/badge_logo.svg" /></a>
  <a href="https://codecov.io/gh/glotzerlab/freud"><img style="display:inline;" title="Codecov" src="https://codecov.io/gh/glotzerlab/freud/branch/master/graph/badge.svg" /></a>
  <a href="https://github.com/glotzerlab/freud"><img style="display:inline;" title="GitHub-Stars" src="https://img.shields.io/github/stars/glotzerlab/freud.svg?style=social" /></a>
</div>


# Overview

The **freud** Python library provides a simple, flexible, powerful set of tools for analyzing trajectories obtained from molecular dynamics or Monte Carlo simulations.
High performance, parallelized C++ is used to compute standard tools such as radial distribution functions, correlation functions, order parameters, and clusters, as well as original analysis methods including potentials of mean force and torque (PMFTs) and local environment matching.
The **freud** library supports [many input formats](https://freud.readthedocs.io/en/stable/topics/datainputs.html) and outputs [NumPy arrays](https://numpy.org/), enabling integration with the scientific Python ecosystem for many typical materials science workflows.

# Resources

- [Reference Documentation](https://freud.readthedocs.io/): Examples, tutorials, topic guides, and package Python APIs.
- [Installation Guide](https://freud.readthedocs.io/en/stable/gettingstarted/installation.html): Instructions for installing and compiling **freud**.
- [freud-users Google Group](https://groups.google.com/d/forum/freud-users): Ask questions to the **freud** user community.
- [GitHub repository](https://github.com/glotzerlab/freud): Download the **freud** source code.
- [Issue tracker](https://github.com/glotzerlab/freud/issues): Report issues or request features.

# Finding Particle Neighbors

# Standard Analysis Techniques

# Specialized Methods

# References
1. V. Ramasubramani, B. D. Dice, E. S. Harper, M. P. Spellings, J. A. Anderson, and S. C. Glotzer. freud: A Software Suite for High Throughput Analysis of Particle Simulation Data. Computer Physics Communications Volume 254, September 2020, 107275. [https://doi.org/10.1016/j.cpc.2020.107275](https://doi.org/10.1016/j.cpc.2020.107275).
2. B. Dice, V. Ramasubramani, E. S. Harper, M. P. Spellings, J. A. Anderson, and S. C. Glotzer. Analyzing Particle Systems for Machine Learning and Data Visualization with freud. Proceedings of the 18th Python in Science Conf. (SciPy 2019), SciPy, 27-33. [https://doi.org/10.25080/Majora-7ddc1dd1-004](https://doi.org/10.25080/Majora-7ddc1dd1-004).

# Acknowledgements

Bradley Dice was supported by a fellowship from The Molecular Sciences Software Institute under NSF grant OAC-1547580.
