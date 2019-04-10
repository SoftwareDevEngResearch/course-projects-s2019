# Constructing Multiplex Transportation Network from OpenStreetMap
>Sylvan Hoover, ME599 Spring 2019

Building networks representing human mobility presents numerous challenges. First, humans move by many different modes (e.g., pedestrian, bike, bus, etc.) requiring their parameters. Second, humans take less obvious (sometimes illogical) factors into consideration, so the route that may appear optimal in some models, may not be the chosen path. Finally, the environment in which mobility takes place is ever-changing, so a network construct is not likely to reflect reality for very long.

As a result, what is needed is an efficient automated means to construct multiplex transportation networks from a regularly updated dataset.

## Why
In 2018 Sidewalk Labs (Alphabet/Google) released a product called [Replica](https://replica.sidewalklabs.com). It aims to use large-scale spatiotemporal data (suspect a combination of App analytics and Call Detail Records) to build models of how populations move about urban environments. They generate a synthetic population and have it function in the client's urban environment (a network likely sourced from Google's Maps platform). Achieving such from open source data would be amazing, but not practical at this point. Instead, let's start with the first step: build the environment.

## OpenStreetMap
OpenStreetMap (OSM) is a crowdsourced mapping project to construct an online map. It's built under the Open Database License, which is a copyleft license, and so is well suited to academic research usage. Elements added cover different modes, and so by selecting elements relevant only to a given mode, a network layer may be constructed for a said mode.

## Multiplex Transportation Network
In 2016 a joint MIT/King Abdulaziz City for Science and Technology (KACST) team published an analysis of the impacts of a prospective transit network for Riyadh, Saudi Arabia \[1\]. They aimed to develop methods to analyze the effects different transportation layers have on the overall transportation landscape. They used road data from the Arriyadh Development Authority for their single-mode street network and added a network layer representing the proposed transit system. Their analysis ultimately showed the difficulty of getting transit right, but introduced methods to start working with multi-modal transportation in other contexts.

While Sidewalk Labs and the MIT/KACST team used proprietary data sources to construct their network layers, such isn't necessary with OSM. OSM has several API routes for accessing data, with the Overpass API optimized for data downloads from OSM \[2\]. By defining an area of interest with a geographic bounding box and selecting desired modes, a multiplex transportation network can be created from OSM data.
 
### Components
- Text-based front-end for inputting desired network parameters
- Back-end will:
    + Generate and execute API GET for map data
    + Parse data based on desired modes
    + Produce mode-specific network layers
    + Check layers for intra- and inter-connectivity

### Inputs
- Bounding coordinates
- Desired modes

### Outputs
- Network nodes (including inter-layer transfer parameters)
- Network edges (including mode-specific parameters/weights)
- Formatting will initially be designed for analysis with the [networkx](https://networkx.github.io) package, but as necessary/time permits will be expanded as user selectable to allow integration with more efficient packages like [graph-tool](https://graph-tool.skewed.de)

## Potential Users
The package will exist as a starting point for any party looking to investigate the flow of human mobility in multi-modal environments using open source data. The analytical pipeline created for the Riyadh analysis is [available](https://github.com/PhilChodrow/riyadh_multiplex) and could be adapted to other environments using the newly generated multiplex network.

## Own Past Work
I have previously pulled OSM data for generation of a single-layer mode-specific network for transportation analysis. That effort remained preliminary, and this package will further develop the approach for multi-modal networks so future research will not require bespoke network generation.

## References
[1]P. S. Chodrow, Z. al-Awwad, S. Jiang, and M. C. González, “Demand and Congestion in Multiplex Transportation Networks,” PLOS ONE, vol. 11, no. 9, p. e0161738, Sep. 2016.

[2]“Downloading data - OpenStreetMap Wiki.” [Online]. Available: https://wiki.openstreetmap.org/wiki/Downloading_data. [Accessed: 10-Apr-2019].
