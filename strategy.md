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
    for i in range(layers_to_consider):
      combined_polygon = []
      for k in range(i-1):
        combined_polygon.append(overhang_areas[k])
      overhang_areas_new[i] = clip_current(combined_polygon)
    combined_polygon_new = []
    for i in range(len(overhang_areas_new)):
      combined_polygon_new.append(overhang_areas_new[i])
    non_overhang_contour = clip_contour(combined_polygon_new)
    ```



