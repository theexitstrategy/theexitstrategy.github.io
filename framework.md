---
layout: page
title: Notes of the Framework
---

In order to establish a framework for the fabrication of complex geometries with desired properties the current status and the underlying dynamics of the system have to be examined.

# Chapter 1: Underlying spatio-temporal dynamics
The first chapter focuses on the spatio-temporal evolution of temperature fields to build an understanding of the underlying dynamics and the relationships between processing parameters and emerging temperature fields. 

Additive Manufacturing is a sequence of welding processes, therefore it is first necessary to understand the relationships of single melt lines of the welding process.

## Single Lines
The temperature fields for single lines are calculated using the semi-analytical solution of the transient temperature field. The emerging meltpool geometry is described using the `meltpool depth` and the `meltpool length`. Different combination of `beam power P` and `beam velocity v` were used to study the parameter dependence. For each series, the total energy input at each point $[J]$ was kept constant by choosing parameters in a way that the `line energy` $\frac{P}{v}=const.$. Figure 1. shows the fraction of energy input at each position for a gaussian distribution with $\sigma = 400e-6m$. he cumulative sum accounts to 1. Therefore the total beam power in $J/s$ is deposited at each point the beam crosses. The total amount of energy can be calcualted by multiplying the time needed for the passing with the energy input per second.

---
<figure>
  <img src="https://github.com/theexitstrategy/theexitstrategy.github.io/blob/master/imgs/Gaussian_Sum.png?raw=true" alt="Overhang Areas" style="width: 100%; display: block; margin: 0 auto;">
    <figcaption><b>Figure 1.</b> (a) Cross Section of a gaussian distribution with $\sigma = 400e-6 m$ and the cumulative sum. (b) Meltpool geometries of single lines with equal energy input and increasing velocity.
  </figcaption>
</figure>
---

The underlying relationship between the energy input by the electron beam and the heat diffusion away from the beam path is visible by comparing the temperature fields of the single lines with the same energy input $E_l = const.$ but higher velocities. With higher beam velocity, the time for heat diffusion is lower when the beam reaches the end of the single line and as a result the heat is still concentrated within the meltpool and the length of the meltpool increases. The meltpool depth however does not change since the total amount of energy is still the same for each case.

---
<figure>
  <img src="https://github.com/theexitstrategy/theexitstrategy.github.io/blob/master/imgs/Single_Line_Geometry.png?raw=true" alt="Overhang Areas" style="width: 100%; display: block; margin: 0 auto;">
    <figcaption><b>Figure 2.</b> Constant Meltpooldepth of single lines with different line energies $E_l = [125,150,175,200,225] J/m$ and linear dependency of meltpool length with increasing velocity.
  </figcaption>
</figure>
---

Figure 2 shows the different meltpool depths for each respective line energy. With higher line energy, the total amount of energy deposited on the surface is higher and results in a higher meltpool depth.The elongation of the meltpool however increase linearly with the beam velocity.


## Hatching - Line Strategy
In case of a hatching process, where parallel lines with a defined line offset $l_{off}$ are molten in sucession introduce the superposition of temperature fields. In case of the first hatch line the temperature prior, the temperature below the beam, is the preheating temperature (in this case 1023K). The temperature prior of subsequent hatch lines however increases due to cumulative heating with each new hatchline. This effect has two different causes. Typically the line offset is smaller than the beam diameter in order to achieve overlapping meltpools. This however leads to a heating of neighboring melt tracks. In addition the heat from previous hatch lines is able to diffuse towards the position of the subsequent hatch lines along the negative temperature gradient.

The increasing temperature prior effects the meltpool geomentry, which increases with each subsequent hatch line. The melt pool geometry changes in the **transient** phase of the hatch and converges when the temperature prior reaches its maximum. This is the case when the heat diffusion from previous hatch lines does not influence the current hatchline anymore. In this **quasi-stationary** state the meltpool geometry changes in a periodical fashion over the remaining course of the hatch.

<figure>
  <img src="https://github.com/theexitstrategy/theexitstrategy.github.io/blob/master/imgs/Temperature_Prior.png?raw=true" alt="Overhang Areas" style="width: 90%; display: block; margin: 0 auto;">
    <figcaption><b>Figure 3.</b> (a) Temperature prior: Temperature at the surface at the start of each new hatch line. The temperature piror increase in the transient phase and reaches its maximum after a specific number of lines. (b) Melt pool depth map: Two-dimensional spatial representation of the maximum melt pool depth at each position of the hatch.
  </figcaption>
</figure>

Figure 3 (b) shows the melt pool depth map for $P=600W,v=4m/s$ where the melt pool depth increases from the first hatch line with each additional hatch line in the transient phase until a constant melt pool depth is reached over the complete hatch in the quasi-stationary state. In addition, boundary effects due to the gaussian beam shape and the conduction of heat in the colder solid at the boundaries can be observed.


> This section has to be reworked

The meltpool geomtery in the quasi-stationary state of the hatch also changes with respect to the processing parameters $P,v,L_{off},T_{preheat},\sigma_{beam}$, similar to the single line. However, second-order interactions make for a complex system that has to be described.

If we increase the velocity $v$ of the beam and keeping the energy input constant $\frac{P}{v}=const.$, the temperature at the end of the hatch line increases continously since the time for heat diffusion decreases and the heat is still concenrated at the former beam position. As a result, the subsequent hatch line also melts on a surface with an higher temperature and the meltpool size increases more compared to a lower velocity. If we continue to increase the velocity $v$, we reach the point where the meltpool of the previous hatchline is still liquid when the beam starts at the next following hatch line and as a result a **persistent**, line shaped meltpool emerges that traverses the surface.

These variations in meltpool geometry can be expressed in **meltpool-geometry-maps**, which describe the `meltpool-depth`, `lateral-meltpool-extension` as well as the `persistence-regime`.

Based on these representations, simple conditions can be formulated that create boundaries for processing of dense samples with a high degree of consolidation and connection to previous layers as well as an even surface.

- Consolidation Boundary: 
- Persistence Boundary:
- Meltpool Stability Limit Boundary:


# Chapter 2: Quasi-stationary State
