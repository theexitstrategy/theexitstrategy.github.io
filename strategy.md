---
layout: page
title: Strategy
---

The strategy of this project can be seperated into three distinct parts:

### Chapter 1: Spatio-temporal meltpool evolution
The first Chapter focuses on the spatio-temporal evolution of temperature fields to built intuition about the underlying relationships between process parameters and emerging temperature fields.

#### Single Lines
The temperature fields for single lines are calculated using the semi-analytical solution of the transient temperature field. The emerging meltpool geometry is described using the *meltpool-depth* and the *meltpool-length*. Different combinations of Beam Power $P$ and Beam Velocity $v$ have been used to study the parameter dependence. For each series, the energy input at each point in $[J]$ was kept constant by choosing parameters in a way that the line energy $\frac{P}{v}=const.$. Figure 1. shows the fraction of energy input at each position for a gaussian distribution with $\sigma = 400e-6m$. The cumulative sum accounts to 1. Therefore the total beam power in $J/s$ is deposited at each point the beam crosses. The total amount of energy can be calcualted by multiplying the time needed for the passing with the energy input per second.

<figure>
  <img src="https://github.com/theexitstrategy/theexitstrategy.github.io/blob/master/imgs/Gaussian_Sum.png?raw=true" alt="Overhang Areas" style="width: 100%; display: block; margin: 0 auto;">
    <figcaption><b>Figure 1.</b> (a) Cross Section of a gaussian distribution with $\sigma = 400e-6 m$ and the cumulative sum. (b) Meltpool geometries of single lines with equal energy input and increasing velocity.
  </figcaption>
</figure>

The underlying relationship between the energy-input by the electron beam and the heat-diffusion away from the beam path is visible by comparing the temperature fields of single lines with same energy input but higher velocities. With higher beam velocity, the time for heat diffusion is lower when the beam reaches the end of the single and as a result, the heat is still concentrated within the melt pool and the meltpool elongates further back. In this case however, the meltpool-depth does not change since the total amount of energy is still the same for each case. 

<figure>
  <img src="https://github.com/theexitstrategy/theexitstrategy.github.io/blob/master/imgs/Single_Line_Geometry.png?raw=true" alt="Overhang Areas" style="width: 100%; display: block; margin: 0 auto;">
    <figcaption><b>Figure 2.</b> Constant Meltpooldepth of single lines with different line energies $E_l = [125,150,175,200,225] J/m$ and linear dependency of meltpool length with increasing velocity.
  </figcaption>
</figure>

Figure 2 shows, the different meltpool depth levels for each respective line energy. A higher line energy results in a higher amount of energy deposited on the surface and hence a higher meltpooldepth. The elongation of the meltpool however increase linearly with the beam velocity.

#### Hatching - Line Strategy
In case of a hatching process, where parallel lines with a defined line offset $l_{off}$ are molten in sucession introduce the superposition of temperature fields. In case of the first hatch line the temperature prior, the temperature below the beam, is the preheating temperature (in this case 1023K). The temperature prior of subsequent hatch lines however increases due to cumulative heating with each new hatchline. This effect has two different causes. Typically the line offset is smaller than the beam diameter in order to achieve overlapping meltpools. This however leads to a heating of neighboring melt tracks. In addition the heat from previous hatch lines is able to diffuse towards the position of the subsequent hatch lines along the negative temperature gradient.

The increasing temperature prior effects the meltpool geomentry, which increases with each subsequent hatch line. The melt pool geometry changes in the **transient** phase of the hatch and converges when the temperature prior reaches its maximum. This is the case when the heat diffusion from previous hatch lines does not influence the current hatchline anymore. In this **quasi-stationary** state the meltpool geometry changes in a periodical fashion over the remaining course of the hatch.

<figure>
  <img src="https://github.com/theexitstrategy/theexitstrategy.github.io/blob/master/imgs/Temperature_Prior.png?raw=true" alt="Overhang Areas" style="width: 90%; display: block; margin: 0 auto;">
    <figcaption><b>Figure 3.</b> (a) Temperature prior: Temperature at the surface at the start of each new hatch line. The temperature piror increase in the transient phase and reaches its maximum after a specific number of lines. (b) Melt pool depth map: Two-dimensional spatial representation of the maximum melt pool depth at each position of the hatch.
  </figcaption>
</figure>

Figure 3 (b) shows the melt pool depth map for $P=600W,v=4m/s$ where the melt pool depth increases from the first hatch line with each additional hatch line in the transient phase until a constant melt pool depth is reached over the complete hatch in the quasi-stationary state. In addition, boundary effects due to the gaussian beam shape and the conduction of heat in the colder solid at the boundaries can be observed.




The meltpool geomtery in the quasi-stationary state of the hatch also changes with respect to the processing parameters $P,v,L_{off},T_{preheat},\sigma_{beam}$, similar to the single line. However, second-order interactions make for a complex system that has to be described.

If we increase the velocity $v$ of the beam and keeping the energy input constant $\frac{P}{v}=const.$, the temperature at the end of the hatch line increases continously since the time for heat diffusion decreases and the heat is still concenrated at the former beam position. As a result, the subsequent hatch line also melts on a surface with an higher temperature and the meltpool size increases more compared to a lower velocity. If we continue to increase the velocity $v$, we reach the point where the meltpool of the previous hatchline is still liquid when the beam starts at the next following hatch line and as a result a **persistent**, line shaped meltpool emerges that traverses the surface.

#### Meltpool geometry maps
These variations in meltpool geometry can be expressed in **meltpool-geometry-maps**, which describe the `meltpool-depth`, `lateral-meltpool-extension` as well as the `persistence-regime`.

Based on these representations, simple conditions can be formulated that create boundaries for processing of dense samples with a high degree of consolidation and connection to previous layers as well as an even surface.

- Consolidation Boundary: 
- Persistence Boundary:
- Meltpool Stability Limit Boundary:




## Todo

**Prometheus**
- Implementation of waiting time segments around the current geometry instead of the complete preheating area to reduce the jump length back towards the actual hatch line and prevent potential inaccuracies.
  - Add center coordinates of the contour and the bounding rectangle to hdf5 output for better accessablity
  - Add new beam figure function `add_waiting_time_segment(x, y, offset, dx, time)` that uses the center coordiantes of the contour with a defined offset and creates paths around the position with a velocity of `1000 m/s` that match the defined time.
- Extend the implementation of the overhang detection to extract overhang areas with different overhang levels.
  - The geometric expression would be to find the contours of different colored polygons which are stacked on top of each other and cover parts of each other. This should yield seperate polygons for each layer and level which can be hatched and interleaved in the following step.
  
    ```python
    # Go through each Overhang Level
    for i in range(layers_to_consider):
      
      # Combine all lower levels into a polygon that lies above the current one
      combined_polygon = []
      for k in range(i-1):
        combined_polygon.append(overhang_areas[k])

      # Clip the current overhang level polygon with respect to the ones that lie above to obtain the new overhang polygon for the current level i. 
      overhang_areas_new[i] = clip_current(combined_polygon)

    # Combine each overhang level into the entirety of overhang contours
    combined_polygon_new = []
    for i in range(len(overhang_areas_new)):
      combined_polygon_new.append(overhang_areas_new[i])

    # Clip the cross-section contour with respect to the entirety of overhang contours to obtain the non-overhang contour segments.
    non_overhang_contour = clip_contour(combined_polygon_new)
    ```
- Implementation of a seperate hatching procedure for overhang segments vs. non-overhang segments.
  - Overhang segments should be hatch with additional waiting time segments to increase the time for heat diffusion and allow the solidification of single lines to prevent and exessive increase in melt pool size.
  - The time necessary for solidification of a single line will be computed using the transient heat source model with material properties that have been adjusted for [powder parameters](https://www.nature.com/articles/s41598-017-11243-8.pdf). The necessary time should be different for each parameter combination of `P,v` and has to be converted into a "wainting time scan length" for the calculation.
    - One important question to answer here is how these properties change over multiple layers with already consolidated material below. Effective material parameters have to be obtained in order to model the effects of the following layers and adjust the necessary waiting time.

- Implementation of return time maps for complex geometries in order to obtain the persistence maps for geometries with inhomogeneous scan lengths and return times