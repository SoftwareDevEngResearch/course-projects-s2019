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

## Anomaly Detection for Mode-Specific Counter

Most transportation mode counting mechanisms (e.g., Automated Passenger Counters (APC) or ground-laid pneumatic tubes) are created to detect and count a specific transportation mode. As counters stray from calibration the resulting miscounts are slow to be identified by transit agencies for the change may be assumed to be a change in actual mode participants. With newly-developed mode-agnostic data sources for human mobility, a secondary data source may be employed to identify potential degradation in data quality of mode-specific counters. By identifying mode choices in the second dataset, mode users present in that dataset can be counted. By employing long short-term memory networks as unsupervised multivariate anomaly detection mechanisms, it is possible to identify when the relation between the two data sources' counts changes. This allows transportation organizations to intervene when the framework detects an anomaly and data integrity needs to be investigated. It also allows the saving of resources for no longer will it be necessary to schedule periodic inspections to ensure counts remain accurate.
 
### Components
+ Generate multiplex transportation network graph
    - Uses OSMnx to download single-mode graph layers
+ Import single-mode counter datasets
    - Identify node associated to count
    - Produce time-series for mode-node pair
+ Train LSTM network to identifiy anomalies in relationship of multiple same-mode time-series
    - Uses Keras for LSTM module

### Inputs
- Mobility datasets

### Outputs
- Time-series report of anomaly probability

## Potential Users
The package will be useful to transportation providers using any single-mode counting mechanisms. It will require a secondary data source containing some sample of the target population, but those are increasing in availability as new exploits are discovered.

## Own Past Work
I have previously pulled OSM data for generation of a single-layer mode-specific network for transportation analysis. I have acquired mode-specific and mode-agnostic mobility datasets for an overlapping geographic area. The datasets have known periods of anomalous counts, so empirical testing of the framework will be possible.

## References
[1]P. S. Chodrow, Z. al-Awwad, S. Jiang, and M. C. González, “Demand and Congestion in Multiplex Transportation Networks,” PLOS ONE, vol. 11, no. 9, p. e0161738, Sep. 2016.

[2]“Downloading data - OpenStreetMap Wiki.” [Online]. Available: https://wiki.openstreetmap.org/wiki/Downloading_data. [Accessed: 10-Apr-2019].
