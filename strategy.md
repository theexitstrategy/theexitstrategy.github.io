---
layout: page
title: Strategy
---

The strategy of this project can be seperated into three distinct parts:

### 1. Spatio-temporal meltpool evolution
The first part focuses on the description of the spatio-temporal evolution of temperature fields to understand the underlying relationships between process parameters and the emerging temperature field.
<br>
The temperature fields for *single-lines* are determined and the meltpool geometry is described using the `meltpool-depth` and the `meltpool-length`. The underlying relationship between *energy-input* by the electron beam and *heat-diffusion* away from the beam path can be clearly shown with the elongation of the meltpool at higher $v$ with the same energy input at each point $\frac{P}{v}=const.$. In this case the time for heat diffusion is lower when the beam reaches the end of the single line and as a result, the heat is still concentrated within the melt pool and the meltpool elongates.
<br>
The standard hatching process, where parallel lines with a defined line-offset $l_{off}$ are molten subsequently, introduces the superposition of temperature fields. As the $l_{off} is typically smaller then the beam diameter, neighboring hatch lines are already heated from previous lines and therefore melt on a higher temperature baseline. This effects the meltpool geometry, which increases with each subsequent hatchline due to the superposition of temperature fields. This change of the meltpool geometry in the **transient** phase of the hatch converges in the **quasi-stationary** state and the meltpool geometry changes in a periodical fashion over the remainder of hatch. 
<br>
The meltpool geomtery in the quasi-stationary state of the hatch also changes with respect to the processing parameters $P,v,L_{off},T_{preheat},\sigma_{beam}$, similar to the single line. However, second-order interactions make for a complex system that has to be described.
If we increase the velocity $v$ of the beam and keeping the energy input constant $\frac{P}{v}=const.$, the temperature at the end of the hatch line increases continously since the time for heat diffusion decreases and the heat is still concenrated at the former beam position.
As a result, the subsequent hatch line also melts on a surface with an higher temperature and the meltpool size increases more compared to a lower velocity.
If we continue to increase the velocity $v$, we reach the point where the meltpool of the previous hatchline is still liquid when the beam starts at the next following hatch line and as a result a **persistent**, line shaped meltpool emerges that traverses the surface.
<br>
These variations in meltpool geometry can be expressed in **meltpool-geometry-maps**, which describe the `meltpool-depth`, `lateral-meltpool-extension` as well as the `persistence-regime`.

Based on these representations, simple conditions can be formulated that create boundaries for processing of dense samples with a high degree of consolidation and connection to previous layers as well as an even surface.

- Consolidation Boundary: 
- Persistence Boundary:
- Meltpool Stability Limit Boundary:





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

