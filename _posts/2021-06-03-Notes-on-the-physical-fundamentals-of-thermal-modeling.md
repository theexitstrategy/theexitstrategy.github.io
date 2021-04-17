---
layout: post
title:  "Notes on the physical fundamentals of thermal modeling"
date: 2021-06-03 20:05:00 +0100
categories: Basics
published: False
---

Temperature is a physical quantity that characterizes the degree of heat in a body. A temperature field is a set of temperature values $T$ at all points of the body at a given time:

<p>

$$
T = T(x, y, z, t) \ at \ t=const.
$$
<p>

where $x, y, z$ are the spatial coordinates in the Cartesian system; $t$ is the time. If the temperature at any point of the body does not change over time, the field is called stationary, otherwise its non stationary.

An isotherm is a geometric place of field points that have the same temperature. Different isotherms cannot intersect (one point of the body cannot have two different temperature values simultaneously). Isotherms cannot have boundaries within the body (They either close inside the body or end on its surface). The temperature does not change along the isotherm.

The greatest temperature difference per unit length occurs in the direction of the normal to the isotherm and is characterized by the *temperature gradient*:

<p>

$$
grad \ T = \partial T / \partial n \ [Km^{-1}]
$$
<p>

The temperature gradient at point $P$ is a vector direction a long the normal to the isotherm in the direction of temperature increase.

he *cooling rate* of the point $P$ at time $t$ is determined by the derivative:

<p>

$$
\partial T / \partial t \ (x, y, z, t) \ [Ks^{-1}]
$$

<p>