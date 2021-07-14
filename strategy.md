---
layout: page
title: Strategy
---

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

