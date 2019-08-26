---
layout: page
title: Research
#subtitle:
---

Jump to: <br />
<a href="#zonalflow">Zonal Flow</a> <br />
<a href="#coupling"> Multiscale Turbulence-transport Coupling </a> <br />
<a href="#neoclassical">Neoclassical Transport Theory</a>

<h2 id="zonalflow"></h2> <br />
## Zonal Flow
Zonal flow presents a fundamental challenge to understand how regular, coherent patterns can form out of turbulence.  Zonal flow forms in diverse physical systems such as planetary atmospheres of Jupiter and Saturn (as well as being related to jet streams on Earth), and in magnetized plasmas like tokamaks.  One one hand, it is a wonderful scientific problem to try to get the bottom of the physics that leads to zonal flow in these systems.  On the other hand, there is enormous practical significance, since zonal flows are thought to regulate the microturbulence causing the majority of heat loss in tokamak fusion reactors.

#### Pattern Formation
Nonlinear physics is hard.  Almost everyone has experienced the enormous difficulty posed by trying to analytically solve nonlinear equations compared with linear ones.  This difficulty is one reason why bifurcation theory and universality classes have such great significance for trying to make sense of the types of behavior that can occur.  In a [pair][ZF_pattern_formation] of [papers][ZF_generation_njp], I showed that within a certain model for the Hasegawa-Mima equation, zonal flows arise within a pattern-formation paradigm.  The model involves the quasilinear approximation, and a statistical analysis thereof, leading to the so-called CE2 equations (for cumulant expansion at 2nd order).  When mathematically analyzed from the right perspective, the bifurcation in which zonal flows form in fact turns out to be identical to the classic Rayleigh-Benard convection problem and the formation of convection cells in a layer of fluid heated between two plates.  In a multiple-scale perturbation analysis, I derived the coefficients for the real Ginzburg-Landau equation, and favorably compared these with direct numerical solution of the nonlinear equations.  This analysis has wide implications for the understanding of zonal flow, such as a conceptual framework for understanding the zonal flow length scale in terms of stability.  It further enables the use of a number of insights and techniques from the field of pattern formation to tackle further zonal flow problems.



#### Wave kinetic theory and geometrical-optics approach
<img style="padding: 0 0 10px 10px; float: right;" src="../img/ZF_theory_hierarchy.png" />
I [realized][ZF_wave_kinetic] that a widely used formalism for studying zonal flow ended up being mathematically pathological.  That formalism, a particular wave-kinetic equation (WKE) for drift-wave fluctuations combined with an evolution equation for zonal flow, had been used to give linear growth rates.  But when used directly as a nonlinear model, it generates arbitrarily small scales, a clearly unphysical behavior.  In the same article, I provided a better wave-kinetic equation, which I referred to as a new geometrical-optics (GO) approximation.  I derived the better-behaved CE2-GO model, and showed that it sits as an intermediate physics model between CE2 and the pathological WKE.  CE2-GO is theoretically appealing because the long-wavelength approximation renders the equations *local* in the phase space. (This paper has the surely rare distinction of having an affiliation of Stanford Law School.  That's another story.)

In a [follow-up work][CE2_Wigner_Moyal], Daniel Ruiz, myself, Eric Shi, and Ilya Dodin recast the physics content of CE2 into an equivalent mathematical form using the Wigner-Moyal formalism.  This was a nice piece of work because in earlier work I had mentioned that the Wigner-Moyal equation, familiar from quantum mechanics, must be equivalent, but it had never been shown explicitly.  The phase-space coordinates of the Wigner-Moyal equation can be somewhat more intuitive, and have a more natural reduction for geometrical-optics approximations.  Ilya Dodin's group at the Princeton Plasma Physics Laboratory has since continued to study zonal flow and drift waves with the Wigner-Moyal approach. (The papers from Dodin's group used the alternate name "improved wave-kinetic equation" for CE2-GO)

To test the fidelity of CE2-GO and whether it would actually be a useful model for further fundamental studies of zonal flow, I [numerically simulated][CE2GO_simulation] it and compared with direct quasilinear simulations.  While the energy partition between fluctuations and zonal flow are correctly captured in CE2-GO, the scale length of the nonlinearly saturated zonal flow is not correctly recovered by CE2-GO.  This suggests that, unfortunately, some physics and instabilities that determine the zonal flow size could not be studied in the CE2-GO framework.

#### Zonal flow and MHD, with potential applicability to the interior of gas giants
With my collaborator [Navid Constantinou](navidconstantinou.com), I explored how zonal flow behaves in a conducting fluid, as opposed to ordinary hydrodynamic fluids.  This brings in MHD physics.  Zonal flows often appear where there is rotation, and rotation and magnetization commonly appear together in astrophysical fluid dynamics, such as the sun, the interior of gas giants, and astrophysical disks.  Using a [CE2 zonostrophic instability analysis][magneticsuppression2018] framed around magneto-Rossby waves, without any assumption of scale separation between zonal flow and turbulence, we found that MHD fluctuations could suppress zonal flow.  The results agreed with a Kelvin-Orr shearing wave analysis in a certain asymptotic limit.

We then found a more intuitive physical picture of how magnetic fields suppress zonal flow.  For magnetic Reynolds number Rm >> 1, the magnetic field induced by a mean flow can act as an [effective *magnetic eddy viscosity*][magneticviscosity2019] back on the mean flow.  With a simple derivation based on the ideal MHD frozen in law combined with a short decorrelation time to due turbluence, we predicted a stress-shear relation wherein the Maxwell stress is directly proportional to the flow shear.  This effect would counteract the mean flow, and suppress a zonal flow when the magnetic energy is comparable to the kinetic energy.  We confirmed this prediction in 2D resistive, incompressible MHD simulations.



#### Equivalence of the secondary instability and the zonostrophic/modulational instability
There have been various approaches to understanding the formation of zonal flow.  Two tacks have been the secondary instability (where a primary instability such as the ITG mode goes unstable) and the zonostrophic or modulational instability.  In my [dissertation][parker_phd_thesis] (Ch. 3), I showed that these are really two sides of the same coin, and that in a certain limit, they can be shown to give exactly the same dispersion relation.  The zonostrophic instability is thus a generalization of the secondary instability, where it allows a full turbulent spectrum as the background which is unstable to the formation of a coherent structure.

<h2 id="coupling"></h2> <br />
## Multiple-timescale method for turbulence-transport coupling in a tokamak
Understanding of drift-wave turbulence in tokamaks has achieved remarkable success, with first-principles theory leading to gyrokinetic simulations that can often yield turbulent heat fluxes in agreement with experimental measurements.  On the other hand, routine predictive modeling typically uses highly reduced models for turbulence, such as quasilinear transport models.  The ideal approach would exploit the vast timescale separation between turbulence (1-10 microseconds) and the energy confinement timescale (~1 second) using a multiscale approach.  With a number of collaborators, I showed potential promise for the LoDestro method.  We created a new 1D transport code Tango implementing the LoDestro method, and coupled it to the global gyrokinetic simulation code GENE.  Our early simulations (with adiabatic electrons) [showed success][turbtransport], finding a steady state balancing input heating power with turbulent heat loss.

One of the key challenges to using a turbulence simulation in the above approach is that the simulation inherently yields fluctuations in the heat flux.  There is thus a fundamentally new challenge compared to using the output of quasilinear model for a 1D transport solver, as the quasilinear models generally produce the same output for a given input.  Turbulence simulations, however, are fundamentally fluctuating (due to the turbulent physics, independent of the simulation method).  For practical usefulness, one must face up to these fluctuations and understand how much they hinder convergence to the desired solutions.  One can always simulate for a longer section of turbulence to have more averaging and decrease the variance, but the increases computational cost may be untenable.  I [investigated][turbtransport_noise] the behavior of the LoDestro method in the presence of fluctuations, and helped estimate how much averaging would be required in practice.

<h2 id="neoclassical"></h2> <br />
## Neoclassical Transport Theory
I spent a summer at MIT working on neoclassical transport theory.  One product of that was a drift-ordered, [variational computation of neoclassical transport][neoclassical_variational]] using the full Landau collision operator via a particular velocity basis expansion that worked rather well.  I also worked on how neoclassical transport coefficients are [modified in a tokamak pedestal][neoclassical_pedestal], where the radial electric field can be large enough to modify particle orbits.



[ZF_pattern_formation]: ../publications/ZF_pattern_formation.pdf
[ZF_generation_njp]: ../publications/ZF_generation_njp.pdf
[ZF_wave_kinetic]: ../publications/ZF_wave_kinetic.pdf
[CE2_Wigner_Moyal]: ../publications/CE2GO_Wigner_Moyal.pdf
[CE2GO_simulation]: ../publications/CE2GO_simulation.pdf
[magneticsuppression2018]: ../publications/magneticsuppression2018.pdf
[magneticviscosity2019]: ../publications/magneticviscosity2019.pdf
[neoclassical_pedestal]: ../publications/neoclassical_pedestal.pdf
[neoclassical_variational]: ../publications/neoclassical_variational.pdf
[turbtransport]: ../publications/turbtransport.pdf
[turbtransport_noise]: ../publications/turbtransport_noise.pdf

[magneticviscosity2019]: magneticviscosity2019.pdf
[magneticsuppression2018]: magneticsuppression2018.pdf

[arxiv:1902.01105]: https://arxiv.org/abs/1902.01105

[magneticsuppression2018-doi]: https://doi.org/10.3847/1538-4357/aace53
