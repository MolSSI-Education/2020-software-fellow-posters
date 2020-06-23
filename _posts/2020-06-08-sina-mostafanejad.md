---
name: 2020-06-08-sina-mostafanejad-poster
title: "OpenRDM: An open-source platform for reduced density matrix-based analysis and computation"
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

The development of an accurate and efficient model for the description of electron correlation
effects is an active area of research in quantum chemistry and molecular physics.
Although popular models such as Kohn-Sham density functional theory (DFT) have been 
successfully applied to a wide variety of molecular systems, they often exhibit dramatic 
failures towards strongly correlated systems with dominant multireference character. In such
cases, multiconfiguration pair-density functional theory (MC-PDFT) offers a possible remedy 
towards a robust and economic deliniation of strong and weak correlation effects. As such, the efficacy
of MC-PDFT stems from highlighting the complimentary strengths of multireference methods and DFT
to account for static and dynamical correlation effects, respectively.

## Theory

### Reduced density matrix-driven CASSCF method

### Multiconfiguration pair-density functional theory

## Software Infrastructure

![OpenRDM]({{ site.url }}{{ site.baseurl }}/assets/images/sina_mostafanejad/openrdm.png)
***Figure 1**: OpenRDM package*

## Applications

### Singlet-triplet energy gaps of graphene nanoribbons

Singlet-triplet energy gaps of larger members of oligocene series not only shed some light
on their fascinating opto-electronic properties but also reflect the key role 
electron correlation effects play in shaping their electronic structure.

Figure 2 illustrates the singlet-triplet energy gaps of oligocene ($$k$$-acene) series 
where $$k=1-12$$ is the number of fuzed benzene rings. All calculations adopt a full-valence
active space of $$\pi/\pi^*$$ orbitals comprised of $$4k+2$$ electrons in $$4k+2$$ orbitals
\[denoted as ($$4k+2$$e, $$4k+2$$o)\] and cc-pVTZ basis set. Translated PBE (tPBE) on-top
pair-density functional was used for MC-PDFT calcualtions. 

![STgaps]({{ site.url }}{{ site.baseurl }}/assets/images/sina_mostafanejad/st-gaps.png)
***Figure 2**: Singlet-triplet energy gaps of oligocene molecues*

The v2RDM-CASSCF results in Fig. 2 display reasonable agreement with those of experiment
for smaller members of oligocene series. However, a proper description of correlation effects,
in particular, for larger polyacenes requires simultaneous account of static and dynamical
electron correlation. Adopting tPBE density functional captures dynamical correlation effects
which closes the gaps as the number of benzene rings increase. The singlet-triplet
energy gap value of 4.87 $$kcal\ mol^{-1}$$, predicted by tPBE functional for infinitely large
oligocenes, is in good agreement with the literature value of 5.06 $$kcal\ mol^{-1}$$ from
Ref. XXXX.

### Reaction energies

The O3ADD6 benchmark set is comprised of the energies of stationary point species with
strong electron correlation associated with 1,3-dipolar cycloadditions of ozone to ethylene
and acetylene relative to the energies of isolated reactants (Fig. 3).

![Reaction]({{ site.url }}{{ site.baseurl }}/assets/images/sina_mostafanejad/o3add6.png)
***Figure 3**: 1,3-dipolar cycloaddition reaction of ozone to olefins*

Here, we applied the hybrid MC-PDFT ($$\lambda$$-MC-PDFT) to compute the relative energies of
stationary points and reactants in the O3ADD6 benchmark set and presented the results in Table 1.
For the sake of comparison, we have also added the energies calculated by the MC1H method of
Ref. XXXX as well as the best estimate values of Ref. YYYY.


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

### Dissociation of di- and polyatomic molecules

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
1. 
2. 

## Acknowledgements

Mohammad Mostafanejad was supported by a fellowship from The Molecular Sciences Software Institute under NSF grant OAC-1547580.
