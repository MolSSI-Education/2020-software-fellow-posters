---
name: sample-poster
title: Simple interoperability via a general representation of molecular wavefunctions
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

- The barrier to entry for preparing a new tool for use by the broader computational molecular science (CMS) community can be prohibitively high.
Typically developers choose to restrict the implementation of their new tool into an established software package or construct an entirely new package from scratch.

- Recently, there has been a trend of developing open-source standalone libraries or packages that serve a specific focus
    - e.g. Libxc$$^1$$, GeomeTRIC$$^2$$, and projects at MolSSI

- MolSSI has embraced the goal of connecting the CMS community through projects like the QCArchive$$^3$$, the MolSSI driver interface$$^4$$, and the revamped basis set exchange$$^5$$.

- **Goal:** Therefore, in collaboration with MolSSI, we propose to create a general wavefunction representation of a molecule to provide the CMS community a simple way to pass information between different software packages to combine available methodologies and facilitate analysis

## Enabling Interoperability

- This new framework allows simple access to wavefunction properties that can used in more workflows such as
    - Post processing in other quantum chemistry programs (e.g. correlated calculations)
    - Integration into the MolSSI Driver Interface
    - Orbital and density visualization

![Figure]({{ site.url }}{{ site.baseurl }}/assets/images/sebastian_lee/Figure_V8.png)
**Figure 1**: A schematic representation of the types of workflow enabled by the wavefunction representation framework

## Representing Molecular Wavefunctions
- This new framework has been implented within QCArchive$$^3$$
- QCArchive provides an open-sourced, community-wide quantum chemistry platform to facilitate computational chemistry research by enabling tasks such as force field construction, physical property prediction, and new methodology assessment 
- QCArchive is modularized into a set of smaller projects (QCSchema, QCElemental, QCEngine, QCFractal) that work in concert to achieve complex computational work flows
### QCSchema Integration
- QCSchema provides a standardized JSON format for storing quantum chemical information
- We have expanded the MolSSI QCSchema to include wavefunction quantities
- For example, here are some of the self-consistent field (SCF) quantities that have been added to QCSchema

```python
# Orbitals
scf_wavefunction["scf_orbitals_a"] = {
  "type": "array",
  "description": "SCF alpha-spin orbitals in the AO basis.",
  "items": {"type": "number"},
  "shape": {"nao", "nmo"}
}

# Density
scf_wavefunction["scf_density_a"] = {
  "type": "array",
  "description": "SCF alpha-spin density in the AO basis.",
  "items": {"type": "number"},
  "shape": {"nao", "nao"}
}

# Fock matrix
scf_wavefunction["scf_fock_a"] = {
  "type": "array",
  "description": "SCF alpha-spin Fock matrix in the AO basis.",
  "items": {"type": "number"},
  "shape": {"nao", "nao"}
}
```

### QCElemental Integration
- Next we have added the wavefunction quantities to QCElemental$$^7$$ so they are available to QCEngine and QCFractal (representative code snippet shown below)

```python
class WavefunctionProperties(ProtoModel):

  # The full basis set description
  basis: BasisSet = Field(..., description=str(BasisSet.__doc__))

  # SCF Results
  scf_orbitals_a = Field(None, description="SCF alpha-spin orbitals.")
  scf_orbitals_b = Field(None, description="SCF beta-spin orbitals.")
  scf_density_a = Field(None, description="SCF alpha-spin density matrix.")
  scf_density_b = Field(None, description="SCF beta-spin density matrix.")
  scf_fock_a = Field(None, description="SCF alpha-spin Fock matrix.")
  scf_fock_b = Field(None, description="SCF beta-spin Fock matrix.")
  scf_eigenvalues_a = Field(None, description="SCF alpha-spin eigenvalues.")
  scf_eigenvalues_b = Field(None, description="SCF beta-spin eigenvalues.")
  scf_occupations_a = Field(None, description="SCF alpha-spin occupations.")
  scf_occupations_b = Field(None, description="SCF beta-spin occupations.")
```

- A major complication of storing and exporting wavefunction quantities is fully specifying the basis set used to construct these objects
- This complication was overcome by utilizing the previous work of MolSSI on the Basis Set Exchange$$^5$$, which provided a natural way to integrate a basis set definition in QCElemental

## Gathering Wavefunction Information

- Next QCEngine$$^8$$ is used to gather wavefunction information from quantum chemistry software packages
- For example the Entos QCore Program Harness retrieves properties for both restricted and unrestricted wavefunctions (example code snippet)
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

- Both Psi4$$^9$$ and Entos QCore$$^{10}$$ have wavefunction support with more programs planned for the future

## Conclusion
- The outcome of this project will provide a powerful tool for new and existing members of the CMS community
- For example: 
    - This wavefunction data framework contains the necessary information (i.e. MO coefficients and the one-electron density) to plot isosurfaces of these properties, which is an essential tool for gaining a qualitative perspective of a chemical system
    - Integration of this framework into QCEngine allows for the combination of methodologies available in different quantum chemistry programs. For example, a mean-field calculation could be run in Entos QCore and then a package with strong wavefunction support (e.g. Psi4) could perform a correlated calculation using the mean-field reference


## References
1. S. Lehtola, C. Steigemann, M. J. Oliveira, and M. A. Marques, SoftwareX 7, 1 (2018).
2. L.-P. Wang and C. Song, The Journal of Chemical Physics 144, 214108 (2016).
3. D. G. Smith, L. Naden, D. Altarawy, and L. Burns, QCArchive, https://qcarchive.molssi.org/, 2019.
4. T. A. Barnes, MolSSI Driver Interface, https://github.com/MolSSI/MDI Library, 2019.
5. B. P. Pritchard, D. Altarawy, and T. L. Windus, A new basis set exchange: An open, up-to-date resource for the molecular sciences community, Manuscript in Preparation.
6. D. G. Smith, L. Naden, D. Altarawy, and L. Burns, QCSchema, https://github.com/MolSSI/QCSchema, 2019. (QCSchema)
7. D. G. Smith, L. Naden, D. Altarawy, and L. Burns, QCSchema, https://github.com/MolSSI/QCSchema, 2019. (QCElemental)
8. D. G. Smith, L. Naden, D. Altarawy, and L. Burns, QCSchema, https://github.com/MolSSI/QCSchema, 2019. (QCEngine)
9. R. M. Parrish et al., Journal of Chemical Theory and Computation 13, 3185 (2017)
10. F. Manby, T. F. Miller III et al., ChemRxiv , DOI: 10.26434/chemrxiv.7762646.v2 (2019), Preprint.

### Acknowledgements

"Sebastian Lee was supported by a fellowship from The Molecular Sciences Software Institute under NSF grant OAC-1547580"
