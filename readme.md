# OpenStreetMap

This document is meant to introduce the reader to OpenStreetMap - what it is, how to use it, and when and why you might want to. I will primarily write this for an audience that has some interest in making maps, especially in an urban setting, and who may want to go beyond maps (visuals) to think about how data can be used for analytic, spatial analysis applications. I hope the reader will have some familiarity with QGIS, and/or Python for which there will be some example code, but most of the information here should generalize to other applications as well.

I mean only to tease and entice here. OpenStreetMap is a deep, _deep_ resource and also a community. I myself have been involved in that community since 2012, when I first started mapping parts of my hometown in Ohio as a way of goofing off during a graduate course on spatial statistics. Since then, I've published many maps based on OpenStreetMap data, and in turn have contributed over two million individual map edits and counting. I mostly edit around Toronto now, where I live and work, as a data scientist for the City. Perhaps you'll find some of my work useful in your own projects.

-Nate Wessel, Toronto, April 2025

## What is OpenStreetMap?

OpenStreetMap (OSM) is a wide-ranging, collaborative mapping project spanning the entire world. You might think of it as Wikipedia, if Wikipedia were a map. Anyone with a computer can contribute edits and can also download and use that data, along with the contributions of millions of others, for a wide range of uses. [Specifically](https://www.openstreetmap.org/copyright):

> You are free to copy, distribute, transmit and adapt our data, as long as you credit OpenStreetMap and its contributors. If you alter or build upon our data, you may distribute the result only under the same licence. The full [legal code](https://opendatacommons.org/licenses/odbl/1.0/) explains your rights and responsibilities.

This openness has led to a huge number of applications based on OSM, including large commercial applications which you've likely used before.

## What's on the map?

The types of things included on the map range widely, from the glacial rivers of Greenland to the cafe around the corner from you. Train lines are on there, as are buildings, many millions of them, all the way down to your apartment or your neighbour's shed. However OpenStreetMap does not cover all subject matter. The basic rule is that data should be, in some sense, verifiable by a person on the ground in a real tangible way. This allows us to map sidewalks if they're there, but not the fact that a census tract contains people 37.8% of whom spoke French at home in the year 2021. It's [not a map of everything](https://wiki.openstreetmap.org/wiki/Scope). You could map that a restaurant exists and serves Tibetan food (that's on their menu, along with their hours and address), but it would be impossible to indicate that the neighbourhood contains many people from Tibet, because... I guess you'd have to ask them all? What would be meant by "many"? People will come to very different conclusions on that one. That's not verifiable. Whether there is or is not a bus stop here is much more verifiable. In a given context at least, we can probably all agree what counts as a bus stop. This verifiability requirement leads OSM to a sort of discreteness that not all mapping efforts share. Something does or does not exist, is this type of thing or that type of thing. OSM doesn't allow things to kind of exist, or exist to a degree.

One important exception to the verifiability rule is political boundaries, which often have no tangible signifier in the real world. These are included for completeness, and because they rarely change, but should generally not be considered as authoritative.

OSM also doesn't include private or identifiable information. You can map a house, but not say who lives there, and you also won't find any property lines in OSM, unless they're marked by some physical boundary.

## How is the data stored?

OSM uses a _vector_ data model, not a _raster_ model. Rasters are pixels covering an area with a gradation of values. Vectors are discrete points and lines in space. In OSM, the fundamental types of spatial data are *nodes*, *ways*, and *relations*.

* **Nodes**: Nodes or points have a single coordinate location. They may exist on their own or be members of the other types. You might map a post box as a node.
* **Ways**: Ways consist of an ordered series of two or more points. A way that starts and ends at different nodes is a line while one that starts and ends at the same node is often (but not always)  considered a closed polygon. You would map a street as a line, and a cemetery as a polygon.
* **Relations**: Relations are grouped collections of any of these data types, including, reflexively, relations. These are the most complex type. A tram route would be a relation. It has a route (the tracks it follows) and also some stops or platforms which could be represented as points or polygons. Relations can also used be used to break up very large features like the shore of Lake Erie, which might otherwise cause your computer to overheat. 




