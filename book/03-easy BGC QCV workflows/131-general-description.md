---
title: General description
date: 2025-08-20
---

The easy Q.C.V BGC  is composed of standalone, reusable and cloud deployable components that are spread into four thematic layers :

:::{contents}
:depth: 1
:::

The internal architecture, adapted to the case of the Nitrate and Chlorophyll-a processing, is presented in @oscar_generalWF. It is meant to be deployed within two infrastructures: the Galaxy orchestrator for workflow chained operations and the Testbed cloud infrastructure for the web application itself (in Future). These two deployments are complementary, allowing engaging different kinds of users. The Galaxy deployment is functional, while the testbed deployment requests further funding to be achieved.

```{figure}  ../../embedded-ressources/figures/S131_OSCARS_QCV_BGC_2.0_architecture_graph.png
:label: oscar_generalWF
:width: 900px
:align: center
easy Q.C.V BGC architecture and color-coded by the development status and foreseen updates, credit @ POKaPOK
```

The architecture of the easy Q.C.V BGC can be described through its thematic layers:

### Hosting layer
The easy Q.C.V BGC will be hosted on the Testbed (developed within FAIR-EASE) based on an openshift/kubernetes subsystem. It follows open source and generic cloud deployment principles and uses the premise hosting capabilities, such as local and remote data storage services (nfs, s3) and flexible node execution resources (RAM, CPU, GPU, NPU).

### Social Layer
The social layer consists of two items: the Galaxy platform and the Testbed user manager. Galaxy is a scientific social sharing platform, which allows publishing online executable tools and chaining them together in order to create customized workflows. The Testbed user manager is the authentication provider for the Q.C.V platform users and groups.

### Data manipulation layer
The data manipulation layer consists of **7 tool categories**:
- The `Ingestor` executes asynchronously data download queries based on the UDAL (Universal Data Access Layer) developed in the frame of the FAIR-EASE project

:::{seealso} See Also!
:class: dropdown
Description of the UDAL in [general](https://fairease.eu/kers/uniform-data-access-layer-revolutionising-data-fairness-fair-ease) and throug [easy QCV BGC usage](#udal). 
:::
 
- The `QCV Harmonizer` standardizes the input data into a converged internal data format
- The `BGC calibration` tools estimate adjustment from reference data. This is detailed in the next pages.
- The `ODV collection manager` merges several dataset into a single generic v5.7.0 ODV spreadsheet
- The `ODV history manager` reports user operation on qualification code or data
- The `In-situ vs satellite colocation` tool fetches the satellite data necessary for the Chlorophyll-a calibration tools
- The `Output delayed mode data delivery` tool inserts the input archive with Q.C.V. operations

### User interface layer
There are **3 User Interfaces** in the Q.C.V BGC : (Web)ODV, the Q.C.V. interface and Galaxy. 
- The `(Web) Ocean Data View (ODV)` software is the Q.C.V visualization interface available on the Testbed and on Galaxy. The software allows the operator to change the qualification code, compare calibration formulas, and overlay additional reference data thanks to specific FAIR-EASE developments. 
- The `Q.C.V interface` is the multi-user dashboard that allows the operator to create jobs, to perform the service parameterisation and to query the execution of data manipulation tools (to be deployed on the TestBed). 
- Finally, `Galaxy` is also a graphical user interface for designing and executing individual linear workflows.
