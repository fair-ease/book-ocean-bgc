---
title: Ocean Data View (ODV)
date: 2025-08-20
label: odv
---

[ODV](https://odv.awi.de/) is a software package for the `interactive exploration, analysis and visualization` of the oceanographic and other geo-referenced profile, time-series, trajectory or sequence data. 

ODV is also declined in various web instances, specific to dataset as for [Argo](https://argo-webodv.vm.fedcloud.eu/login).

The instance contains all the [documentation](https://odv.awi.de/fileadmin/user_upload/odv/docs/ODV_guide.pdf) to run and parameterize the tool.


In the framework of FAIR-EASE and to meet the needs of our demonstration, ODV 5.8.1 has been `deployed on Galaxy`. This version includes developments performed by the AWI team to match needs specifically expressed for the easy Q.C.V BGC, but that can interest the wider user base of (web) ODV:
- superimposition of data from various sources needed for the validation phase of the easy Q.C.V BGC.
- containerization of the (web) ODV instance
- addition of information in the ODV logs for helping the history report in the original files

Further more, some interface developments within the easy Q.C.V BGC were performed to:
- prepare the input data into an ODV collection format
- retrieve and process the ODV logs containing the list of Quality Codes changes to apply to the original data files.
