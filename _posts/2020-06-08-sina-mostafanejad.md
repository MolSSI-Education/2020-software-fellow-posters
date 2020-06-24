---
name: 2020-06-08-sina-mostafanejad-poster
title: "Reduced Density Matrix-Based Models for Strongly Correlated Electrons"
author: "Sina Mostafanejad"
mentor-names: "Matthew Welborn, Samuel Ellis"
full-author-list:
    - name: "Mohammad Mostafanejad"
      affiliation: 1
affiliations:
    - name: "Department of Chemistry and Biochemistry, Florida State University"
      address: "Tallahassee, FL 32306-4390, USA"
      index: 1
toc: true
toc_sticky: true
toc_label: "Poster Contents"
layout: poster
---

## Introduction

The development of accurate and efficient models for the description of electron correlation
effects is an active area of research in quantum chemistry and molecular physics.
Although popular models such as Kohn-Sham density functional theory (DFT)
[\[1, ](https://doi.org/10.1103/PhysRev.140.A1133)[2\]](https://doi.org/10.1103/PhysRev.136.B864)
have been successfully applied to a wide variety of molecular systems, they often exhibit 
dramatic failures towards strongly correlated systems with dominant multireference character.
In such cases, multiconfiguration pair-density functional theory (MC-PDFT)
[\[3\]](https://doi.org/10.1021/acs.accounts.6b00471) offers a possible remedy towards
a robust and economic deliniation of strong within multireference methods and weak correlation
effects within DFT. 

Since almost all methods built upon the merger of multireference approaches and DFT
(MR+DFT), suffer from double counting of electron correlation, symmetry dilemma, 
and computational cost barrier of multireference methods, this poster intends to
show how reduced density matrix (RDM)-driven MC-PDFT can simultaneously address all 
of these issues.

## Theory {#Theory}

Throughout this section, we adopt the conventional notation employed within
multireference methods for labeling molecular orbitals $$\lbrace \psi\rbrace$$:
the indices $$i$$, $$j$$, $$k$$, and $$l$$ represent inactive orbitals;
$$t$$, $$u$$, $$v$$, and $$w$$ indicate active orbitals; $$a$$, $$b$$, $$c$$,
and $$d$$ denote external orbitals; and $$p$$, $$q$$, $$r$$, and $$s$$ represent
general orbitals.

### Reduced density matrix-driven CASSCF method

The complete active-space self-consistent field (CASSCF) electronic energy can 
be expressed in terms of the active-space 1- and 2-electron 
RDMs [\[4\]](https://doi.org/10.1021/acs.jctc.6b00190)

$$ 
E_{\text{CASSCF}} = (h^t_u + 2\nu^{ti}_{ui} - \nu^{tu}_{ii}) {}^1D^t_u + \frac{1}{2} \nu^{tv}_{uw} {}^2D^{tv}_{uw} \tag{1}\label{EQ:ECASSCF}
$$

defined as

$$
{}^1D^p_q = {}^1D^{p_\sigma}_{q_\sigma} = \left< \Psi \left\vert \hat{a}^\dagger_{p_\sigma} \hat{a}_{q_\sigma} \right\vert \Psi \right> \tag{2}\label{EQ:1RDM}
$$

and 

$$
{}^2D^{pq}_{rs} = {}^2D^{p_\sigma q_\tau}_{r_\sigma s_\tau} = \left< \Psi \left\vert \hat{a}^\dagger_{p_\sigma} \hat{a}^\dagger_{q_\tau} \hat{a}_{s_\tau} \hat{a}_{r_\sigma} \right\vert \Psi \right> 
\tag{3}\label{EQ:2RDM}
$$

respectively. Here, summation over repeated labels is implied. In Eq. \eqref{EQ:ECASSCF},
$$ h^p_q = \left< \psi_p \vert \hat{h} \vert \psi_q \right> $$ represents the sum of the
electron kinetic energy and electron-nucleus potential energy integrals, and 
$$\nu^{pq}_{rs} = \left< \psi_p \psi_q \vert \psi_r \psi_s \right>$$ is an element of 
the electron repulsion integral (ERI) tensor.

The core idea of variational 2-electron reduced density matrix-driven (v2RDM)-CASSCF 
is that the spin blocks of the active-space RDMs can be determined directly by
minimizing the energy with respect to variations in their elements and orbital parameters.
Since all RDMs should be $$N$$-representable, the minimization procedure becomes a 
large-scale semidefinite program with polynomial scaling, the details of which can be
found in Ref. [4](https://doi.org/10.1021/acs.jctc.6b00190).

### Multiconfiguration pair-density functional theory

The MC-PDFT energy expression can be written as

$$
\begin{align}
E_{\text{MC-PDFT}}  &= 2h^i_i + h^t_u {}^1D^t_u + E_\text{H}  \nonumber    \\\
                    &+ E_\text{xc} \left[ \rho,\Pi, \vert \nabla\rho \vert, \vert \nabla\Pi \vert \right] \tag{4}\label{EQ:EMCPDFT}
\end{align}
$$

Here, the two-electron terms from Eq. \eqref{EQ:ECASSCF} (and the two-electron contributions
to the core energy) has been replaced by classical Hartree term,

$$ 
E_\text{H} = 2 \nu^{ij}_{ij} + 2\nu^{ti}_{ui} {}^1D^t_u + \frac{1}{2} \nu^{tv}_{uw} {}^1D^{t}_{u} {}^1D^{v}_{w} \tag{5}\label{EQ:EHARTREE} ,
$$

and the remaining exchange and correlation effects are folded into a functional of the on-top
pair density (OTPD). As such, MC-PDFT addresses the double counting of the Coulomb correlation
in MR+DFT framework. At the same time, symmetry dilemma has also been resolved via chaning variables
in exchange-correlation functional from spin densities to total density, $$\rho$$, and OTPD, $$\Pi$$.

## OpenRDM Software Infrastructure

The [OpenRDM](https://github.com/SinaMostafanejad/OpenRDM) package is an open-source 
software, hosting $$ab\ initio$$ models such as MC-PDFT, which are designed for 
applications in large-scale calculations involving strongly correlated systems. 
In principle, OpenRDM can interface with any program capable of providing 1- and 2-RDMs.
For example, we have interfaced OpenRDM with [Psi4](http://www.psicode.org) program package
in order to consume RDMs generated by [v2RDM-CASSCF plugin](https://github.com/edeprince3/v2rdm_casscf). 
Its interface with CASSCF and DMRG modules in [PySCF](http://www.pyscf.org) program package
is under development.

![OpenRDM]({{ site.url }}{{ site.baseurl }}/assets/images/sina_mostafanejad/openrdm.png)
***Figure 1**: OpenRDM package*

OpenRDM's source code resides in a version controlled Github public repository.
The code quality and security is continuously monitored via [CodeFactor](https://www.codefactor.io)
and [LGTM](https://lgtm.com) services. Code development environment, continuous integration 
and delivery pipelines are also managed through [Travis CI](https://travis-ci.com) service.
It also performs automatic runs on testing routines through [CMake](https://cmake.org) build system
generator which handles fined-tuned relations among libraries and executables in our software.
Documentation is generated by [Doxygen](https://www.doxygen.nl/index.html) and automatically 
deployed to the main branch via Travis CI.

## Applications

In this section, we provide numerical evidence for the efficacy of our models
in describing the electronic structure of strongly correlated systems. In particular,
we apply (hybrid) MC-PDFT to compute singlet-triplet energy gaps of oligocene molecuels,
reaction energy barriers of 1,3-dipolar cycloaddition of ozone to olefins, dissociation 
potential energy curve (PEC) of $$N_2$$ molecule and distribution of effectively unpaired
electrons for narow zig-zag graphene nanoribbons.

### Singlet-triplet energy gaps of graphene nanoribbons

Singlet-triplet energy gaps of larger members of oligocene series not only shed some light
on their fascinating opto-electronic properties but also reflect the key role 
electron correlation effects play in shaping their electronic structure.

Figure 2 illustrates the singlet-triplet energy gaps of oligocene ($$k$$-acene) series 
where $$k$$ is the number of fuzed benzene rings. All calculations adopt a full-valence
active space of $$\pi/\pi^*$$ orbitals comprised of $$4k+2$$ electrons in $$4k+2$$ orbitals
\[denoted as ($$4k+2$$e, $$4k+2$$o)\] and cc-pVTZ basis set. Translated PBE (tPBE) OTPD
functional was used for MC-PDFT calcualtions. 

![STgaps]({{ site.url }}{{ site.baseurl }}/assets/images/sina_mostafanejad/st-gaps.png)
***Figure 2**: Singlet-triplet energy gaps of oligocene molecues*

The v2RDM-CASSCF results in Fig. 2 display reasonable agreement with those of experiment
for smaller members of oligocene series. However, a proper description of correlation effects,
in particular, for larger polyacenes requires simultaneous account of static and dynamical
electron correlation. Adopting tPBE density functional captures dynamical correlation effects
which closes the gaps as the number of benzene rings increase. The singlet-triplet
energy gap value of 4.87 $$kcal\ mol^{-1}$$, predicted by tPBE functional for infinitely large
oligocenes, is in good agreement with the literature value of 5.06 $$kcal\ mol^{-1}$$ from
Ref. [5](https://doi.org/10.1039/C5CP00214A).

### Reaction energies

The O3ADD6 benchmark set is comprised of the energies of stationary point species with
strong electron correlation associated with 1,3-dipolar cycloadditions of ozone to ethylene
and acetylene relative to the energies of isolated reactants (Fig. 3).

![Reaction]({{ site.url }}{{ site.baseurl }}/assets/images/sina_mostafanejad/o3add6.png)
***Figure 3**: 1,3-dipolar cycloaddition reaction of ozone to olefins*

Table 1 shows the relative energies of stationary points \[the van der Waals complex (vdW),
the transition state (TS), and the cycloadduct (cycloadd.)\] and reactants 
in the O3ADD6 benchmark set calculated using hybrid MC-PDFT ($$\lambda$$-MC-PDFT)
within aug-cc-pVTZ basis set. The active spaces of (2e,2o) and (4e,4o) were used for 
isolated reactants and stationary point molecules, respectively. Table 1 also includes 
the energies computed by the MC1H method of Ref. XXXX as well as the best estimate values 
of Ref. YYYY.

***Table 1**: Calculated relative energies ($$kcal\ mol^{-1}$$) of stationary points
and isolated reactants comprising O3ADD6 dataset*

|:                        |:                  :|: $$O_3 + C_2H_2 \rightarrow $$         :|||:  $$O_3 + C_2H_4 \rightarrow $$ :|||:       :| 
|:  ^^ Method            :| ^^ $$\lambda^a$$  |    vdW |    TS |    cycloadd.           |  vdW  |  TS  |  cycloadd.           | ^^ MAE    |
|-------------------------|-------------------|--------|-------|------------------------|-------|------|----------------------|-----------|
| $$\lambda$$-tPBE        |   0.20            | -0.40  | 7.69  | -68.00                 | -1.86 | 4.87 | -57.57               | 1.29      |
|-------------------------|-------------------|--------|-------|------------------------|-------|------|----------------------|-----------|
| MC1H-PBE $$^b$$         |   0.25            | -1.08  | 3.66  | -70.97                 | -1.25 | 0.13 | -61.26               | 3.35      |
|-------------------------|-------------------|--------|-------|------------------------|-------|------|----------------------|-----------|
| Reference values $$^c$$ |   ---------       | -1.90  | 7.74  | -63.80                 | -1.94 | 3.37 | -57.15               | --------- |
|=========================|===================|========|=======|========================|=======|======|======================|===========|
| $$^a$$ The optimal mixing parameter.$$\~$$ $$^b$$ From Ref. .$$\~$$  $$^c$$ Best estimates from Ref. . ||||||||

According to Table 1, the mean absolute error (MAE) in the energies obtained via tPBE functional
is 1.29 $$kcal\ mol^{-1}$$ which is close to chemical accuracy and smaller than that calculated 
by MC1H-PBE method, 3.35 $$kcal\ mol^{-1}$$.

### Molecular dissociation

The triple-bond dissociation of $$N_2$$ molecule provides another example
where accurate consideration of static and dynamical correlation effects becomes imperative.

Figure 4 depicts the dissociation potential energy curve of $$N_2$$ molecule
computed with v2RDM-driven CASSCF and MC-PDFT methods within cc-pVTZ basis. We compare 
our results with those of CASPT2/cc-pVTZ level of theory. As Fig. 4 demonstrates, the overall
shape of the CASPT2 PEC is reasonably reproduced by both v2RDM-CASSCF and tPBE methods.
However, as tPBE PEC reveals, only with simultaneous inclusion of both static and dynamical
correlation effects via MC-PDFT, an accurate description of electronic structure is achieved.

![N2pec]({{ site.url }}{{ site.baseurl }}/assets/images/sina_mostafanejad/n2-pec.png)
***Figure 4**: Dissociation potential energy curve of $$N_2$$ molecule*

Since almost all approximate density functionals suffer from delocalization error (DE),
it is possible to improve their performance by counter-balancing DE via replacing
a fraction $$\lambda \in (0,1)$$ of local exchange with its comlementary non-local part 
calculated from a multiconfiguration reference density. The resulting hybrid variant of
MC-PDFT method is called $$\lambda$$-MC-PDFT.

Figure 5 shows the non-parallelity errors (NPEs) of the PECs calculated with various denisty functionals
relative to that of CASPT2. The NPE is defined as the difference in the maximum and the minimum 
deviations between the $$\lambda$$-MC-PDFT and CASPT2 PECs from an $$N-N$$ distance of 0.7
<i><b><span>&#8491;</span></b></i> to an $$N-N$$ distance of 5.0 <i><b><span>&#8491;</span></b></i>.
The two- (and three-) particle constraints PQG(+ T2) are enforced on reference RDMs.

![N2polar]({{ site.url }}{{ site.baseurl }}/assets/images/sina_mostafanejad/n2-polar.png)
***Figure 5**: MC-PDFT and $$\lambda$$-MC-PDFT non-parallelity errors 
($$kcal\ mol^{-1}$$) associated with the dissociation of $$N_2$$ molecule*

All NPE curves presented in Fig. 5 exhibit their minimal value between $$\lambda$$ = 0.70 and 0.90.
Figure 5 also reveals that inclusion of nonlocal hybrid exchange effects indeed mitigates some DE
so that the error associated with approximate $$N$$-representability of reference RDMs becomes dicernible.
In addition, NPEs can significantly vary over various choices of functionals; however, accounting for
nonlocal exchange effects can serve as an efficient equalizer.

### Effectively unpaired electrons

Effectively unpaired electrons (EUEs) offer a qualitative/quantitative tool for the analysis of 
RDMs. We adopted EUEs to investigate the di- and polyradical character of the singlet ground state
of narrow zig-zag graphene nanoribbons.

![Nanoribbons]({{ site.url }}{{ site.baseurl }}/assets/images/sina_mostafanejad/nanoribbons.png)
***Figure 6**: Spatial distribution of effectively unpaired electrons on graphene nanoribbons*

The spatial distribution of EUEs for 6-acene, 3,6-circumacene and 3,6-periacene molecules, 
demonstrated in Fig. 6, suggests that most EUEs accumulate on the zig-zag edges and towards 
the horizontal symmetry axis that halves of graphene nanoribbons.

***Table 2**: Calculated number of effectively unpaired electrons for 6-acene, 3,6-circumacene
and 3,6-periacene molecules*

|     Molecule      |: Total EUEs    :|:  EUEs on edges   :|
|:------------------|:---------------:|:------------------:|
| 6-acene           |      2.47       |      1.24          |
| 3,6-circumacene   |      4.41       |      1.17          |
| 3,6-periacene     |      4.93       |      1.45          |

According to Table 2, the total number of EUEs in 3,6-periacene (4.93) is larger than those
of 3,6-circumacene (4.41) and 6-acene (2.47), respectively. Nonetheless, the buildup of
unpaired electrons localized on the edges shows a different trend. Again, 3,6-periacene
shows the largest number of EUEs (1.45) on the zig-zag edges. However, the number of EUEs
on the edge of 3,6-circumacene (1.17) is in fact less than that of 6-acene (1.24) which is
somewhat surprising. Therefore, connecting open-shell character, stability and chemical
reactivity in graphene nanoribbons based on the total number of EUEs should also be accompanied
by their spatial distribution.

## Conclusions

## References

1. [P. Hohenberg and W. Kohn, <i>Phys. Rev.</i>, <b>136</b>, B864 (1964)](https://doi.org/10.1103/PhysRev.136.B864)
2. [W. Kohn and L. J. Sham, <i>Phys. Rev.</i>, <b>140</b>, A1133 (1965)](https://doi.org/10.1103/PhysRev.140.A1133)
3. [L. Gagliardi, D. G. Truhlar, G. Li Manni, R. K. Carlson, C. E. Hoyer, and J. L. Bao, <i>J. Chem. Theor. Comput.</i>, <b>50</b>, 66 (2017)](https://doi.org/10.1021/acs.accounts.6b00471)
4. [J. Fosso-Tande, T. Nguyen, G. Gidofalvi, and A. E. DePrince, III, <i>J. Chem. Theor. Comput.</i>, <b>12</b>, 2260 (2017)](https://doi.org/10.1021/acs.jctc.6b00190)
5. [C. U. Ibeji and D. Ghosh, <i>Phys. Chem. Chem. Phys.</i>, <b>17</b>, 9849 (2015)](https://doi.org/10.1039/C5CP00214A)

## Acknowledgements

Mohammad Mostafanejad was supported by a fellowship from The Molecular Sciences Software Institute under NSF grant OAC-1547580.
