---
name: laurens-poster
title: Relativistic Excited State Coupled-Cluster
author: "Lauren Koulias"
mentor-names: "Jonathan Moussa, Daniel Smith"
full-author-list:
    - name: "Lauren N. Koulias"
      affiliation: 1
    - name: "Lixin Lu"
      affiliation: 1
    - name: "Brandon Cooper"
      affiliation: 2
    - name: "David Williams Young"
      affiliation: 3
    - name: "Tianyuan Zhang"
      affiliation: 1
    - name: "Eugene DePrince"
      affiliation: 2
    - name: "Xiaosong Li"
      affiliation: 1
affiliations:
    - name: "Department of Chemistry, Univeristy of Washington"
      address: "Seattle, Wa"
      index: 1
    - name: "Department of Chemistry, Florida State University"
      index: 2
      address: "Tallahassee, FL"
    - name: "Computational Research Division, Lawrence Berkeley National Laboratory"
      index: 3
      address: "Berkeley, CA"
toc: true
toc_sticky: true
toc_label: "Poster Contents"
layout: poster
---

## Introduction

The goal of this project is to implement and improve the preformance of excited state coupled cluster singles and doubles (CCSD) calculations in the ChronusQuantum software package (insert hyperlink/ref 1), which can be used to generate absorption spectra in both the UV/Vis and X-ray range. This is acheived through two separate methods: 

1) Equation of Motion CCSD (EOM-CCSD) (insert ref 2, 3), wherein a nonhermitian eigenvalue problem is solved to obtain excitation energies and their oscillator strengths 

2) Time-Dependent EOM-CCSD (TD-EOM-CCSD) (insert ref 4, 5) wherein the dipole autocorrelation function is propagated forward in time, resulting in a time-domain spectrum which is then Fourier transformed into the frequency-domain in order to generate an absorption spectrum

These Coupled-Cluster calculations can include both scalar relativistic effects and spin-orbit coupling variationally by using the exact 2-component (X2C) (insert ref 6) wavefunction as our reference wavefunction for the coupled-cluster calculation. The inclusion of such relativistic effects is important when looking for fine structure in absorption spectra such as zero-field splitting and the splitting in the X-ray L- and M-edges.

## Theory
The ground state CC wavefunction (insert ref 7) is comprised of an exponential operator acting on a reference wavefunction, $$ \vert\Phi_0\rangle$$:

 $$ \vert\Psi_{CC}\rangle =  e^{\hat{T}}\vert\Phi_0\rangle$$ 

 where $$\vert\Phi_0\rangle$$ can either be the X2C ground state wavefunction or the generalized Hartree-Fock ground state wavefunction and the cluster operator, $$\hat{T}$$, at the singles and doubles level is:

 $$ \hat{T} = \hat{T}_1 + \hat{T}_1 = \sum_{ia} t_i^a \hat{a}_a^\dagger \hat{a}_i +\frac{1}{4} \sum_{ijab} t_{ij}^{ab} \hat{a}_a^\dagger \hat{a}_b^\dagger \hat{a}_j \hat{a}_i $$

 where solving for the $$t$$-amplitudes, $$t_i^a$$ and $$t_{ij}^{ab}$$, will allow the CC ground state energy to be obtained via:

 $$E_{CC} = \langle\Phi_0\vert\hat{H}e^{\hat{T}}\vert\Phi_0\rangle$$

### Equation of Motion

The excited state wavefunctions can be determined as eigenfunctions of the shifted similarity-transformed Hamiltonian (insert ref 2,3):

$$ \tilde{H} = \bar{H}-E_{CC} $$

Where the eigenproblem that we set out to solve is:

$$ \tilde{H}\hat{R}_P\vert\Psi_{CC}\rangle = \omega_P\hat{R}_P\vert\Psi_{CC}\rangle $$

and

$$ \langle\Psi_{CC}\vert\hat{L}_P\tilde{H} = \langle\Psi_{CC}\vert\hat{L}_P\omega_P $$

Where $$\vert\Psi_{CC}\rangle$$ is the ground state CC equation and $$\omega_P$$ is the excitation energy for state $$P$$. The linear excitation and de-excitation operators, $$\hat{R}_P$$ and $$\hat{L}_P$$ respecitvely, can be used to calculate the oscillator strength for each excitation.  

### Real-Time Equation of Motion

Instead of solving this eigenproblem directly, we can instead propagate the dipole autocorrelation function forward in time (insert ref 4,5). The spectral lineshape function of the dipole autocorrelation function is:

$$ I(\omega) = \sum_{\xi \in {x,y,z}} \int\limits_{-\infty}^\infty dt\,e^{-iwt} \langle M(0) \cdot M(t)\rangle $$

and more specifically, the coupled-cluster dipole moment function is defined as:

$$ I(\omega) = \sum_{\xi \in {x,y,z}} \int\limits_{-\infty}^\infty dt\,e^{-iwt} \langle\Phi_0\vert(\hat{1}+\hat{\Lambda}\bar{\mu}_\xi e^{i\tilde{H}t}\bar{\mu}_\xi\vert\Phi_0\rangle $$ 

where $$\bar{\mu}_\xi$$ is the similarity transformed dipole operator. 

This propagation forms a time domain spectrum which can then be Fourier transformed using the Pade approximation to yeild a frequency domain absorption spectrum:

(insert water time domain / freq domain spectrum diagram)


## Results

### Zero-Field Splitting in Atomic Spectra

When ℂ-GHF is used as the reference wavefunction, only one transition is seen in this energy regime, from the $$^2S$$ ground state to the $$^2P$$ excited state. However, when using the X2C reference, the inclusion of relativistic effects, particularly spin-orbit coupling, allows the $$^2P$$ states to split into $$2^P_{1/2}$$ and $$^2P_{3/2}$$ states. Additionally, the relative oscillator strength is as expected for the two- and four-fold degeneracy of the $$2^P_{1/2}$$ and $$^2P_{3/2}$$ states. It should also be noted that the excitation energies and oscillator strengths are in agreement in both the EOM-CCSD and TD-EOM formalisms.


![Figure Label]({{ site.url }}{{ site.baseurl }}/assets/images/LAUREN_KOULIAS/na_td_and_eom.png)  
***Figure 1**: The Sodium D-Line*

A preliminary benchmark for the accuracy of TD-X2C-EOM-CCSD on Zero-Field splitting in atomic spectra can be found in Ref. 5.


### L-edge X-Ray Spectra

Similarly, in the L-edge of Aluminum when the ℂ-GHF reference wavefunction is use we see transitions from the 2p to 3p orbitals. However, when we use an X2C reference, the p orbitals split into $$J=\frac{1}{2}$$ and $$J=\frac{3}{2}$$, giving rise to the $$L_{2,3}$$-edge separation that can seen in Fig. 2. Again, the good aggreement between the EOM-CCSD and TD-EOM formalisms should be noted

![Figure Label]({{ site.url }}{{ site.baseurl }}/assets/images/LAUREN_KOULIAS/al_l_edge_spec.png)  
***Figure 2**: Aluminum $$L_{2,3}$$-edge*

(add TD-X2C to figure!!)

A benchmark for the accuracy of X2C-EOM-CCSD in both the US/Vis and X-ray region will be submitted by the end of the summer (insert Ref. 6).

## Computational Analysis

### Parallelization

Figure comparing timings vs for number of cores used

### Real-Time Propagators

Figure comparing Lanczos timings vs rk4 both with and without TA

## References
1. ref 1
2. ref 2 
3. ref 3
4. ref 4
5. ref 5
6. ref 6
7. ref 7
8. ref 8

### Acknowledgements

"`Lauren Koulias` was supported by a fellowship from The Molecular Sciences Software Institute under NSF grant OAC-1547580"


