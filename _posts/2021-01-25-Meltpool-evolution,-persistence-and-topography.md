---
layout: post
title:  "Meltpool evolution, persistence and topography"
subtitle: "Contrary to popular belief the emerging meltpool is not constant over the course of a hatch. Different regions with specific meltpool regimes emerge that have vastly different behavior."
date: 2021-01-25 20:05:00 +0100
categories: model, meltpool, visualization
---

### Meltpool evolution - The effect of the cross snake strategy

The standard strategy for contour filling in electron beam powder based additive manufacturing is the *cross-snake* scan strategy. Parallel lines with a defined spacing (*line-offset*) are used to fill the contour. For the melting process the beam follows one line and changes direction when changing lines at the end of one line.

Consider the most simple case of a cuboid with constant scan length. Even in this simple case, the cross-snake strategy inherently leads to variable return times at each position of the domain. After melting the first melt line of a pristine surface, the beam changes direction one line offset further away. The corresponding return time at the turning point position is $t_{ret}(x_{tp}, y_{tp})=0$. Along the second scan line, the return time increases as a linear function of the current position until the end of the scan line is reached, where it takes two lines worth of time until the beam returns at the same position one line offset away $t_{ret} = 2 \cdot \frac{l_m}{v}$. For the next line this alternating phenomena continuous. [Figure 1](*Figure 1: Return times of two subsequent hatch lines of  a cuboid hatch domain with 15 mm scan length. Vector n depicts the second vector of the hatch which starts at a position of 15 mm*) shows the nature of the return times for two subsequent hatch vectors in this case. In the center line of the hatch a mean return time can be measured, that is equal for both moving directions of the beam. The mean return time is equal to one complete hatchline traveled by the beam $t_{ret} = \frac{l_m}{v}$ . 

<img src="https://theexitstrategy.github.io/assets/img//Return_times.png" align="center" alt="Return_times" style="zoom:25%;"  />



*Figure 1: Return times of two subsequent hatch lines of  a cuboid hatch domain with 15 mm scan length. Vector n depicts the second vector of the hatch which starts at a position of 15 mm*

Depending on the beam power and velocity the first hatch line creates a meltpool with a defined meltpool geometry (length & depth) when it reaches a *quasi-stationary state*[^1]. This meltpool has a defined meltpool lifetime (time until the meltpool solidifies at each point) depending on the initial temperature of the material and the energy input of the beam.

When the return time of the beam is smaller then the meltpool lifetime $t_{ret} <t_{ml}$, the meltpool of the previous melt line is still liquid when the beam returns. This condition corresponds to the definition of the **persistence**.  On the other hand, when the beam return time is higher than the meltpool lifetime $t_{ret} > t_{ml}$ the meltpool is already solidified when the beam returns. 

As a result a persistent meltpool emerges at the turning points towards the center of the hatch for the second hatchline, while the area with higher return times, returns to a already solidified meltpool. [Figure 2]() shows this relationship. The blue line equals the meltpool lifetime of the first hatchline. Return times below the threshold are marked, and result in a persistent meltpool. With increasing return time, the condition is not fulfilled anymore, therefore no persistence occurs.

<img src="https://theexitstrategy.github.io/assets/img/Return_times_Meltpool_Lifetime_Persistence_increase.png" align="center" alt="Return_times" style="zoom:25%;"  />

*Figure 2: Return times of two subsequent hatch lines of a cuboid hatch domain with 15 mm scan length. blue: corresponding meltpool lifetimes, black: resulting areas where the persistence condition is fulfilled, red: resulting persistent area*

For the third hatchline, the conditions change. Residual heat from the first hatchline influences the meltpool geometry at the end of the second line. As a result the meltpool size increases and the cooling rate as well as the solidification velocity decreases. The meltpool lifetime is higher (second blue line in [Figure 2]()). As a consequence, the size of the persistent area increases further towards the center. 

This preheating effect increases further for the following hatch lines until the *quasi-stationary state* of the hatch is reached and both sides show the same extension of the persistence. In this case the persistence is still alternating between the sides, since there is still an area where the return time is bigger than the meltpool lifetime.

For higher beam velocities with the same energy input (line energy), the return time of the beam decreases. In this case, the slopes of the vectors change as seen in [Figure 3](). The decrease in return time also leads to a faster increase of the meltpool lifetime, as the time for heat diffusion decreases and a higher amount of residual heat from previous hatch lines is present. 

<img src="https://theexitstrategy.github.io/assets/img/Return_times_Meltpool_Lifetime_Persistence_higher_velocity.png" align="center" alt="Return_times" style="zoom:25%;"  />

*Figure 3: Return times of two subsequent hatch lines of a cuboid hatch domain with 15 mm scan length and increased velocity. The resulting persistent areas are identified*

The persistent areas reach further into the center of the hatch. However in this case, the persistence still only occurs in an alternating fashion, for each side of the turning point towards the center of the hatch.

If the meltpool lifetime is higher than the mean return time $t_{mean} < t_{ml}$ a special case arises [Figure 4](). In this case the persistence range from each side into the opposite side, crossing the center and forming a permanent persistence in the center of the hatch. In this area, the meltpool is always liquid when the beam returns in the next line, independent from what side the beam arrives.

<img src="https://theexitstrategy.github.io/assets/img/Return_times_Meltpool_Lifetime_Persistence_higher_velocity_overlapp.png" align="center" alt="Return_times" style="zoom:25%;"  />

*Figure 4: Persistence formation of two subsequent hatch lines with a cuboid hatch domain with 15 mm scan length and high velocity. The persistent area overlap in the center region*



[^1]: The temperature field does not change in the moving  coordinate system

