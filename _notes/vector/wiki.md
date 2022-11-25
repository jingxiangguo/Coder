---
layout: single 
title: 'MSE'
date: 2022-11-26
permalink: /notes/Model/MSE/wiki/
author_profile: true
toc: true
---
## Wiki 
---


Introduction
Starting with version 9.6.1, OLI is introducing a third thermodynamic model in addition to the previously available Aqueous (AQ) and Mixed-Solvent Electrolyte (MSE) models. This new model, called MSE-SRK, is based on the MSE model for electrolyte systems but utilizes the Soave-Redlich-Kwong (SRK) equation of state for both the gas phase and the second liquid (or nonelectrolyte) liquid phase. The MSE-SRK model is targeted at upstream oil and gas and related chemistries and is designed to eliminate the deficiencies that hampered the use of MSE for these applications.

The purpose of this document is to answer the following questions:

Why was MSE-SRK developed?
How does it work?
What are the advantages of MSE-SRK?
What are its disadvantages?


Why was MSE-SRK developed?
Since 2000, OLI has been intensively developing the MSE thermodynamic framework. Simultaneously, the older AQ model has been maintained and upgraded on an as-needed basis. The MSE model offers major advantages over the AQ model including:

No limitations with respect to electrolyte concentration, making it possible to simulate electrolyte systems from infinite dilution to pure solute limits;
Accuracy in predicting the properties of multicomponent systems with multiple competing solid phases;
Simulating the effects of important organic components (e.g., glycol or methanol) on the behavior of electrolytes;
Reproducing the properties of systems with two ionic liquid phases;
Including the computation of solid-gas (or sublimation) equilibria in addition to vapor-liquid, solid-liquid, and liquid-liquid equilibria
Thus, the MSE model represents the state-of-the-art of electrolyte modeling. However, MSE has significant limitations for calculations that include supercritical components at elevated pressures. These limitations are:

Inability to reproduce the critical behavior of nonelectrolyte mixtures;
Spurious discontinuities in the phase behavior of systems containing supercritical components at transition points between vapor-liquid and liquid-liquid equilibria arising from the use of different formulations for the gas phase and second liquid phase
Since accurate modeling of systems containing supercritical components at elevated pressures is essential for upstream oil and gas applications, MSE has found limited use in this area. For upstream oil and gas, the AQ model has been generally preferred even though it is clearly inferior to MSE with respect to predicting the behavior of electrolytes. To remedy this situation, the MSE-SRK model has been developed. It retains the state-of-the-art treatment of electrolytes that is a key feature of MSE and, at the same time, introduces the same formulation for the gas phase and second liquid phase to eliminate the above deficiencies of MSE.



How does MSE-SRK work?
Figure 1 compares the structure of the MSE and MSE-SRK models. The key difference lies in the treatment of the second liquid phase in liquid-liquid equilibrium computations.

In both the MSE and MSE-SRK models, the electrolyte-containing (usually aqueous) liquid phase is represented in the same way, i.e., by a combination of the Helgeson-Kirkham-Flowers (HKF) equation of state for standard-state properties and the MSE activity coefficient model for solution nonideality. Accordingly, the chemical potential of a species i in a liquid phase is calculated as

μiL = μiL,0,x(T,P) + RT ln xiγiX* (T,P,x) (equation 1)

where μiL,0,x(T,P) is the standard-state chemical potential from the HKF theory [1,2], xi is the mole fraction, and γiX* (T,P,x) is the activity coefficient from the MSE theory of Wang et al. [3], which accounts for long-range electrostatic, specific ionic, and short-range intermolecular interactions.

In the case of MSE, eq. (1) is always used for the liquid, whether the system contains one or two liquid phases. This makes it possible to model systems in which both liquid phases are ionic and to predict the transitions from partially miscible to homogeneous liquid systems (i.e., the upper or lower critical solution temperature).

In the case of MSE-SRK, eq. (1) is used for only one liquid phase, i.e., the electrolyte-containing one. The other phase is assumed to be always non-ionic and is modeled using the Soave-Redlich-Kwong (SRK) equation of state [4]. The chemical potential in the non-ionic liquid phase is then calculated as


μiG = μiG,0(T) + RT Ln (P yi φi (T,P) / P0 ) (Equation 2)

where μiG,0(T) is the chemical potential of pure component i in the ideal gas state, yi yi is the mole fraction, φi (T,P) is the fugacity coefficient from the SRK EOS, P is the total pressure, and P0 = 1 atm. The same approach to the second liquid phase is used in the Aqueous (AQ) thermodynamic model (although the treatment of the ionic phase and solid phases is quite different).

For both MSE and MSE-SRK, the properties of the gas phase are obtained from the SRK equation according to eq. (2). Thus, in the case of MSE, vapor-liquid equilibria are always modeled using two separate models – one for the liquid phase and one for the gas phase. This means that MSE can never reproduce the vapor-liquid critical locus. On the other hand, MSE-SRK can easily reproduce vapor-liquid critical behavior for nonelectrolyte systems (e.g., for hydrocarbons and light inorganics). Further, this makes it easy for MSE-SRK to transition smoothly from vapor-liquid behavior to liquid-liquid behavior, which is particularly important when a system contains supercritical components (especially at high pressures).


It is noteworthy that the different treatment of the second liquid phase in the two models leads to a key difference in the representation of critical behavior. MSE can reproduce liquid-liquid, but not vapor-liquid critical end points. For MSE-SRK, the reverse is true, i.e., it can reproduce vapor-liquid, but not liquid-liquid critical behavior.

The properties of solid phases are the same in MSE and MSE-SRK. Thus, when a system contains only a single electrolyte liquid phase and any number of solid phases, MSE and MSE-SRK are equivalent. The transport properties and surface tension are also calculated in the same way in both models (cf. the “Other Properties” columns Fig. 1). The only property that is not available in MSE-SRK is interfacial tension because this property requires a single model for both liquid phases [5].

The difference in the treatment of systems that may form two liquid phases has profound consequences for mixtures containing organics and light inorganic components such as CO2 and H2S. In the rest of this document, we examine these consequences in detail.


