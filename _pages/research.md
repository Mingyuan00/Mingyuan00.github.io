---
layout: archive
title: "Research"
permalink: /research/
author_profile: true
---

I am currently working on two main research projects:

**A. Development of novel AI-based enhanced sampling methods**

Current computational hardware limits the timescale of molecular dynamics simulations of biomolecules to microseconds, while many important biomolecular processes (protein folding, ligand binding, enzyme activation, etc.) are much slower. The understanding of these so-called "rare events" is of great interest for various downstream applications, such as drug discovery or protein design. 

Without significantly sacrificing the accuracy of the simulations (e.g. through coarse-graining), enhanced sampling algorithms are able to accelerate these events by adding bias to the energy surface or selectively restarting simulations at specific system configurations. The former class of methods often requires a user-defined set of *collective variables (CV)* or *reaction coordinates (RC)* to perform efficiently. However, the definition of RC for complex biomolecular systems based on human expertise is generally unfeasible. Various CV machine learning methods have been proposed, yet almost all of them require sufficient **unbiased** sampling across the whole configuration space, leading to a "chicken-and-egg" paradox. 

On the other hand, the latter class of methods, often referred to as *adaptive sampling* methods, allow efficient prior-knowledge-free exploration by selectively seeding new rounds of simulations at system configurations more likely to trigger rare events without the need for a user-defined CV or adding bias. However, their efficiency is generally much lower in comparison to CV-based methods and much longer simulations are often required for robust statistics. Nevertheless, we discovered that they are sufficient to provide enough statistics for CV machine learning methods.

The core idea of our approach is to integrate the strength of adaptive sampling, CV machine learning and CV-based enhanced sampling methods to sample efficiently without the need for pre-defined CV. Together with several technical improvements, we implemented a fully automated pipeline (for Gromacs) for the sampling of rare events of biomolecular systems and succeeded in two model systems.

<img src="/images/Overall workflow.png" style="zoom:50%;" />

The results at the current stage have been published [here](https://pubs.acs.org/doi/abs/10.1021/acs.jctc.4c00764). Current implementations are available [here](https://github.com/Mingyuan00/Adaptive_Sampling_for_OPES).

I am still actively working on this project by further improving each part (e.g. better adaptive sampling/CV machine learning/enhanced sampling algorithms) of this automated pipeline for its general applicability in more complex biomolecular systems. 

**B. Development of novel RC learning methods**

The accurate determination of optimal RC for biomolecular systems is not only useful for performing enhanced sampling methods but also essential for subsequent mathematical modeling (e.g. Markov State Model construction) or correct biophysical interpretation. Multiple data-driven approaches have been proposed, yet we believe there is still room for improvement, in terms of both training efficiency and accuracy. Inspired by the recent theoretical development in the mathematical definition of optimal RC, known as *lumpability and decomposability*, we developed a novel RC learning algorithm known as *Flow Matching for Reaction Coordinates* (FMRC).

<img src="/images/FMRC.png" style="zoom:50%;" />

Notably, our algorithm utilizes a recently developed training objective, *flow matching*, for the training of our decoders based on *continuous normalizing flow*. Our algorithms are able to learn a more accurate system dynamics representation as a low-dimensional RC in comparison to other SOTA RC learning methods. In addition, our algorithms are easy to train with minimum hyperparameters tuning across different systems/training lag times and have significantly less training variance. 

Detailed results are currently under review and available as [preprints](https://arxiv.org/abs/2408.17139). Current implementations are available [here](https://github.com/Mingyuan00/Flow_Matching_for_RC).
