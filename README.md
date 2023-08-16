# Tokyo SUMO Traffic(ToST) Scenario
This project is licensed under the terms of the MIT license.

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


## Publication
- 山崎友路. ToST(Tokyo SUMO Traffic) scenario:現実的なモビリティパターンを再現した東京の交通シナリオの作成. Master’s thesis, 東京工業大学 情報理工学院 情報工学系 情報工学コース, jan 2023.


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
Further option is listed [here](https://sumo.dlr.de/docs/sumo.html).
