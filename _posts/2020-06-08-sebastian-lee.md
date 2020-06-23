---
name: sample-poster
title: Establishing a general framework to represent molecular wavefunctions and provide simple interoperability
author: "Sebastian Lee"
mentor-names: "Taylor Barnes"
full-author-list:
    - name: "Sebastian J. R. Lee"
      affiliation: 1
    - name: "Thomas F. Miller III"
      affiliation: 1
affiliations:
    - name: "Department of Chemistry and Chemical Engineering, California Institute of Technology"
      address: "Pasadena, CA"
      index: 1
toc: true
toc_sticky: true
toc_label: "Poster Contents"
layout: poster
---

## Background and Motivation
- The barrier to entry for preparing a new tool for use by the broader CMS community can be prohibitively high

- Typically developers choose to restrict the implementation of their new tool into an established software package or construct an entirely new package from scratch 

- In recent years, there has been a trend of developing open-source standalone libraries or packages that serve a specific focus 
    - e.g. Libxc$$^XX$$, GeomeTRIC$$^XX$$, and projects at MolSSI

- In particular MolSSI has embraced the goal of connecting the CMS community through projects like the QCArchive$$^XX$$, the MolSSI driver interface$$^XX$$ (MDI), and the revamped basis set exchange$$^XX$$. 

- **Goal:** Create a general wavefunction representation of a molecule to provide the CMS community a simple way to pass information between different software packages to combine available methodologies and facilitate analysis

- Show Figure from proposal as an example workflow. Emphasize QCProgram to QCArchive to (Visualization, Machine-learning, post-HF calculations).

![NSF Logo]({{ site.url }}{{ site.baseurl }}/assets/images/sample-poster/nsf.png)  
***Figure 1**: The logo of the National Science Foundation.*

## Representing a Molecular Wavefunctions
- Ties into QCSchema and QCElemental.
- Show QCSchema and QCElemental code

- Needs a basis set definition

### Basis Set Definition
- Ties in nicely with previous work of MolSSI on the Basis Set Exchange

## Integration into QCEngine
- Gather wavefunction information from quantum chemistry software packages

- For example the Entos Program Harness retrieves properties for both restricted and unrestricted wavefunctions
```python
entos_wavefunction_map = {
       "restricted": {
           "orbitals": "scf_orbitals_a",
           "density": "scf_density_a",
           "fock": "scf_fock_a",
           "eigenvalues": "scf_eigenvalues_a",
           "occupations": "scf_occupations_a",
       },
       "unrestricted": {
           "orbitals_alpha": "scf_orbitals_a",
           "orbitals_beta": "scf_orbitals_b",
           "density_alpha": "scf_density_a",
           "density_beta": "scf_density_b",
           "fock_alpha": "scf_fock_a",
           "fock_beta": "scf_fock_b",
           "eigenvalues_alpha": "scf_eigenvalues_a",
           "eigenvalues_beta": "scf_eigenvalues_b",
           "occupations_alpha": "scf_occupations_a",
           "occupations_beta": "scf_occupations_b",
       },
     }
```

## Enabling Interoperability

- Visualization

- Machine-learning

- Easily pass quantum chemistry calculations between codes
    - post-HF calculations


## References
1. S. Lehtola, C. Steigemann, M. J. Oliveira, and M. A. Marques, SoftwareX 7, 1 (2018).
2. L.-P. Wang and C. Song, The Journal of Chemical Physics 144, 214108 (2016).
3. D. G. Smith, L. Naden, D. Altarawy, and L. Burns, QCArchive, https://qcarchive.molssi.org/, 2019.
4. T. A. Barnes, MolSSI Driver Interface, https://github.com/MolSSI/MDI Library, 2019. (MDI)
5. B. P. Pritchard, D. Altarawy, and T. L. Windus, A new basis set exchange: An open, up-to-date resource for the molecular sciences community, Manuscript in Preparation. (BSE)
6. D. G. Smith, L. Naden, D. Altarawy, and L. Burns, QCSchema, https://github.com/MolSSI/QCSchema, 2019. (QCSchema)
7. F. Manby, T. F. Miller III et al., ChemRxiv , DOI: 10.26434/chemrxiv.7762646.v2 (2019), Preprint. (Entos)
8. R. M. Parrish et al., Journal of Chemical Theory and Computation 13, 3185 (2017)
9. H.-J. Werner et al., Molpro, version 2018.1, a package of ab initio programs, 2018, see http://www.molpro.net.

### Acknowledgements

"Sebastian Lee was supported by a fellowship from The Molecular Sciences Software Institute under NSF grant OAC-1547580"
