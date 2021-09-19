---
layout: page
title: 
---
The goal of this site is to function as an [Index](https://clearerthinkingpodcast.com/?ep=039) of [Evergreen Notes](https://notes.andymatuschak.org/Evergreen_notes) that are frequently updated.

### Projects
I am working in the space of powder-bed based [additive manufacturing](https://en.wikipedia.org/wiki/3D_printing) with a focus on electron beam based additive manufacturing. The goal is to establish a [framework](https://theexitstrategy.github.io/framework) for the fabrication of complex geometries with desired properties. Each of the arising problems within this space needs the appropriate tools for it to be solved.

For this purpose a variation of tools have been developed from scan path generation from complex CAD models to various thermal models that are capable to represent the spatio-temporal temperature evolution during the process.

-	[Prometheus](https://theexitstrategy.github.io/prometheus): Implementation of complex scanning strategies for complex CAD models based on thermal modeling
-	[Semi-Analytical Heat Source](https://theexitstrategy.github.io/semi-analytical): Implementation of a semi-analytical solution for the transient thermal history of a gaussian beam for arbitrary beam paths.
-   [Finite Difference Heat Model](https://theexitstrategy.github.io/fd-gpu): Implementation of a finite difference solver for the heat equation with thermal input on GPU.

### Further Ideas

-	[Thermal stress](https://sci-hub.st/https://doi.org/10.4028/www.scientific.net/MSF.762.224) from computed temperature fields in complex geometries.
-	[Overhang Areas](https://theexitstrategy.github.io/overhang) and their influence on the emerging meltpool geometry. The goal is to find an effective thermal diffusivity for melting diretly into the power and subsequent layers to compute optimal processing parameters.
- Adaption of the semi-analytical heat conduction model for different power density distributions ([Top-Hat](https://www.edmundoptics.eu/contentassets/a22cc770fce541438bb18385a20ebb07/why-use-a-flat-top-laser-beam-fig-1.png)) to achieve the same calculation speed for other important processes. This process should be able to be adapted similar to the calculation of a pseudo-gaussian distribution from [segmental ring heat sources](https://link.springer.com/content/pdf/10.1007/s11663-000-0022-2.pdf). Except in this case the power distribution has to be integrated over the top hat profile instead.
- Including the effect of preheating, especially for more geometries in the build chamber, on the melt pool formation. Add additional heating steps to reach a constant temperature prior for each geometry in the build.
- Spot Melting as alternative melting strategy to reach geometry independent properties and also extend the space of possible reachable microstructures. The goal of the spot melt strategy should be the independence of each single spot from all other spots to reach high solidification velocities and keeping a constant melt pool geometry of each spot. First calculations show that the cooling rates are at least one order of magnitude higher compared to the line strategy. Even higher if compared with persistent meltpool which have a generally lower cooling rate.
- Implementation of a guidance system for waiting time segements into the startup square for better accuracy.
- Differential Physics

## Link List:
1.	[Principles of Effective Research](https://michaelnielsen.org/blog/principles-of-effective-research/)
2.	[Mimetic theory](https://en.wikipedia.org/wiki/Mimetic_theory)
3.	[On Caffine use](https://www.youtube.com/watch?v=mAPG18zNtXk&list=LL&index=1&t=601s)
4.  [Learning Dynamical Systems with Autoencoder Neural Networks](https://www.youtube.com/watch?v=KmQkDgu-Qp0) Could be interesting to find a linear representation of processing parameters to meltpooldepth and shape?
	1. [Deep learning for universal linear embeddings of nonlinear dynamics](https://www.nature.com/articles/s41467-018-07210-0.pdf) 
5. [How to Remember What You Read](https://fs.blog/2021/08/remember-books/)