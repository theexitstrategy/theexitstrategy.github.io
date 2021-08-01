---
layout: page
title: Notes on Prometheus
---

**Prometheus:** Generation of custom hatching strategies to precisely control the spatio-temporal energy input for arbitrary complex geometries from predefined CAD-models.

Hierarchical Code structure representing each abstraction layer of the process:

- *EBM-Process*: Represents the highest level of the EBM Process, where different Models can be added and global variables (Material, Layer-Thickness) are defined.
- *EBM-Model*: Represents one CAD-Model that can be added to the EBM-Process; A model can either be a support or standard model. A model can be sliced, hatch, contoured.
- *EBM-Slice*: Represents one Cross-Section of the sliced model at a defined gobal height, the corresponds to one global layer. Each slice of a model contains the minimum of one closed contour,  but may contain a complex structure of nested contours. From the availible contours, contour offsets may be computed or the hatching vectors in different fashions can be computed.
	
For each *EBM-Slice* contour offsets can be calculated to better match the dimensional accuracy depending on the beam diameter.(Add additional information about offset contour computation)

Currently different possibilites exist to compute the hatches from an arbitrary geometry, that can be grouped depending if they only cover one parent contour line or if many contours lines from one model in on slice are combined (longer scan lengths -> different thermal properties):

-	*Single Hatch Area* (Single parent contours are considered only): 
	- Normal Hatch: Parallel Lines with defined Line offset within the boundaries of the single contour. Possible Parameters (Line Offset, Rotation Angle, Line Order, Number of Multiple Melt Segments)
	- Radial Hatch: Radial Hatch lines from the center of the contour outwards. Possible Parameters (Line Offset at the mean distance of the geometry intersections, Number of Multiple Melt Segments, Line Order)
- *Combined Hatch Area* (Combination of all parent contours from the model in the current slice) [Possible Extension to group different parent contours together depending on shape, etc.]
	- Normal Hatch: Global grid of Parallel Lines starting from the common bounding box of each parent contour. Possible Parameters (Line Offset, Rotation Angle, Line Order, Number of Multiple Hatch Segments)
	-	Bucket Sort Hatch: Parallel Hatch Lines starting from the bounding box of each indivual parent contour combined into a global grid of buckets with the width of one line offset. (Pro: Contour of each individual contour can be matched in an exact fashion $\Leftrightarrow$ Error in the normal hatch due to global grid alignment). Possible Parameters (Line Offset, Rotation Angle, Line Order, Number of Multiple Melt Segments)
	- Radial Hatch: Radial Hatch lines from the center of the contour outwards over all combined parent contours. Possible Parameters (Line Offset at the mean distance of the geometry intersections, Number of Multiple Melt Segments, Line Order)



---
The goal is to determine hatching strategies and the final vectors using *Prometheus* and transfering the calculated hatches to the native machine format using appropriate interface modules.

<figure>
  <img src="https://github.com/theexitstrategy/theexitstrategy.github.io/blob/master/imgs/Process_prep.png?raw=true" alt="Overhang Areas" style="width: 100%; display: block; margin: 0 auto;">
  	<figcaption><b>Figure 1.</b> Overview of the process preparation steps: (1) Selection and addition of CAD models representing the build as either support or part; (2) Slicing of each CAD model according to a global layer sequence; (3) Hatching of the respective cross sections of each global layer; (4) Transfer of the hatch vectors with the help of appropriate interface modules to the native machine or simulation format.
	</figcaption>
</figure>