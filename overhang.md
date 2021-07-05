---
layout: page
title: Scanstrategies for Overhang areas
---

One of the problems of complex geometries in additive manufacturing are overhang structures, where the beam has to consolidate powder on top of a powder layer, without any connection to the base plate. This environment has significantly different properties comparted to the bulk material. The powder las limited thermal conductivity and as a result, the combination of process parameter lead to a different meltpool geometry. It is assumed that the melt pool depth increases significantly, as the heat cannot be conducted away from the melt pool through the power and the melt pool therefore increases is size. In addition, the melt pool lifetime should increase drastically as heat is still concentrated and not able to leave the melt pool through the powder.

> It is important to get information about the powder properties - Link to Paper with powder properties.

From first observerations, the first molten layer on powder exhibits a higher melt pool depth. In addition, the observed surface of the ELO images show a *labyrinth* like surface structure as observed when exceeding the melt pool stability limit. This indicates that the melt pool geometry ratio of melt pool depth to lateral extension exceeds the threshold limit. This effect can also be traced back towards the reduced heat diffsion through the powder. When the heat is still concentrated and the melt pool is still liquid several lines back the melt pool extension increases and the stability limit is reached.

<figure>
  <img src="https://github.com/theexitstrategy/theexitstrategy.github.io/blob/master/imgs/Overhang_Areas_H_400W.png?raw=true" alt="Overhang Areas" style="width: 60%; display: block; margin: 0 auto;">
  	<figcaption><b>Figure 1.</b> ELO images of overhang areas build with a beam power of 400W and different velocities.
	</figcaption>
</figure>

<br>

Two main problems arise:
-	Increased melt pool depth -> does not match the CAD geometry of the part.
-	Melt pool geometry exceeds the melt pool stability limit -> provides an uneven surface for further defect propagation

The feature size of the *labyrith* like structure is also very interesting, as it increases with higher leine energy, which should correspond to a higher melt pool lifetime and additional time for the melt to aggregate in the liquid pool. This effect can also be observed for samples with the same line energy but higher absolut power/velocity values, which should decrease the time for diffusion from the lower return time of the beam.

#### Solutions

In order to compensate for different "material properties" of the powder, the process parameters have to be changed locally in order to create an layer that matches the underlying CAD of the final part. 

**Velocity Adaptation**
Currently the only available option is the *ARCAM Thickness Function*, which scales the velocity of the beam according to the distance of the overhang area. This decreases the energy input and the depth of the melt pool should be smaller compared to the bulk process parameter set. This approach however leads to an even reduced time for heat diffusion for each of the single melt lines and the lateral melt pool extension should further increase in size and the melt pool stability limit should be reached in any case.

**Return Time Compensation**
The second approach is the introduction of and additional waiting time for diffusion after each single line in the overhang area. The hypothesis is that this can compensate the smaller diffusion coefficient by a higher time component and that the final residual energy is comparable to the bulk material. This should decrease the overall melt pool depth, but also compensate the lateral melt pool extension and the melt pool stability limit.
