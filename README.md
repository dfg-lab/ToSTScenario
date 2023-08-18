# Tokyo SUMO Traffic(ToST) Scenario
[![License: MIT](https://img.shields.io/github/license/dfg-lab/ToSTScenario?style=flat)](LICENSE)

This project is licensed under the terms of the MIT license.

Over and above the legal restrictions imposed by this license, if you use this scenario for an academic publication then you are obliged to provide proper attribution.
The reference for the paper is provided in the section of [publication](#publication).
The first one (ITSC paper) is preferable as a citation for academic publications.

## Overview
ToST scenario is a realistic open traffic scenario in a district of Tokyo, Japan, for a 12-hour period.
The scenario is designed for SUMO (Simulator of Urban MObility) traffic simulator.

The scenario includes a map data and 12-hour traffic demand for the Itabashi ward, a residential district of Tokyo.
The map data provides the road network of 33.22 $\mathrm{km}^2$, originally exported from [OpenStreetMap](https://openstreetmap.org).
The traffic demand includes 298,310 normal vehicles from 7:00 a.m. to 7:00 p.m.

![Map](Map.png)
![Simulation](Snapshot.png)

### Note
ToST scenario is developed and tested with SUMO 1.14.1.
The scenario should work with other versions, but the simulation result may differ.
The recommend version is SUMO 1.14.1 or later version.

### Limitations
The ToST scenario currently has several limitations as follows;
- It only includes normal vehicles so far. Public transportations will be added later.
- It does not provide any information about traffic lights, vehicular controlling mechanisms, etc. Lacking these information causes a lot of collisions in a siumulation.


## Publication
1. Y. Yamazaki, Y. Tamura, X. Défago, E. Javanmardi, and M. Tsukada. <i>ToST: Tokyo SUMO traffic scenario</i>. The 26th IEEE International Conference on Intelligent Transportation Systems (ITSC 2023), Sep. 2023. (accepted)
2. Y. Yamazaki. <i>ToST (Tokyo SUMO Traffic) scenario: 現実的なモビリティパターンを再現した東京の交通シナリオの作成</i>. Master’s thesis, Graduate Major in Computer Science, School of Computing, Tokyo Institute of Technology, Jan. 2023. (in Japanese)

[Bibtex file](ToST.bib) is included in this repository.


## How to simulate the ToST scenario
Simple simulation can be run with the following command.
```
sumo-gui -c scenario/itabashi/itabashi.sumocfg
```
Or, the following command gives the same execution.
```
sumo-gui \
    --net-file scenario/itabashi/map/ToST_itabashi.net.xml \
    --route-files scenario/itabashi/trip/ToST_0700_1900.trips.xml \
    --begin 25200 \
    --end 68400 \
    --ignore-junction-blocker 15 \
    --device.rerouting.probability 1.0 \
    --device.rerouting.period 300 \
    --collision.action remove
```

The activity after 7:00 p.m. is not taken into account in the scenario.

Please refer to the [SUMO wiki](https://sumo.dlr.de/docs/index.html) for further detailed simulations and data collecting methods.
Available options are listed [here](https://sumo.dlr.de/docs/sumo.html).
