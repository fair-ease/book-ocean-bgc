---
title: Context & Backgrounds
authors:
  - D. Dobler
  - V. Racapé
---

The Ocean BGC pilot aims at implementing and reaching a Technical Readiness Level (TRL) of 7 at least for a web service that seamlessly orchestrates and parameterizes the unitary tools needed for the Qualification, Calibration and Validation (Q.C.V.) of oceanic BioGeoChemical (BGC) variables.  It focuses on the Q.C.V workflow of BGC playing a key role in the carbon cycle: 
* **Nitrate**, a key phytoplankton nutrient : https://biogeochemical-argo.org/measured-variables-nitrate.php
* **Chlorophyll-*a* concentration** (Chlorophyll-*a* hereafter), the universal proxy for the phytoplankton biomass : https://biogeochemical-argo.org/measured-variables-chlorophyll-a.php (*IN PROGRESS*)

The service will primarily be used on BGC variables measured by the Argo array, but also tested for measurements from the Glider array. Argo international array is composed of autonomous float profilers deployed in the global ocean, measuring from 2000m depth to the surface, every 10-days, during 5 years on average. It has been providing a synoptic view of the ocean state and health since the early 2000s, with an optimal coverage of temperature and salinity and an increasing coverage for BGC variables, which implies an increased data management and associated Q.C.V. volume and pace. Euro-Argo ERIC coordinates the European contribution to the Argo program. The Gliders are oceanic in-situ piloted platforms, so far dedicated to shallower areas and deployed at regional scale  for a shorter period of time.

Q.C.V workflows aim at providing end-users with high-quality dataset. Indeed, sensors can be affected by various phenomena: quality codes must be applied (qualification), sometimes data must be adjusted (calibration) and adjustments must be validated against independent datasets (validation). The most known phenomenon affecting sensors is the drift in time, for which calibration is needed after some time, using close-by accurate reference data (most often, there is no access to the sensor for a direct calibration). For some parameters, reference data are not accessible and neural-network techniques are used to build them from a proxy (e.g. oxygen), slightly increasing the uncertainty. Other sensor-specific phenomena exist. For instance the Chlorophyll-a measurements are affected by the quenching: a non-linearity arising in the relationship between fluorescence (what the sensor primarily measures) and Chlorophyll-a when the sun is at the zenith.

Q.C.V. operators (also called delayed mode operators) are facing many challenges. They must use and chain several tools, specific to the phenomena influencing the variable and to the reference data availability. Several coding languages coexist (R, python, Matlab, etc.), depending on the preference of the tool developer. Added to this complexity are the platform used (HPC, own laptop, linux/windows, etc.), and ancillary data access performances. This is a major barrier for Q.C.V. processing efficiency for two reasons: long and complex installation and uptake of the tools. This implies difficulty to on-board new human resources in a context of growing demand, which is particularly true for the Argo array dataset.

Following Open Science and subsequent FAIR principles, the Ocean BGC pilot provides operators with a seamless orchestration of the necessary tools, to easily perform complete Q.C.V. workflows and provide guidance for the tools parameterisation. This service will be integrated in two infrastructures, allowing engaging different kinds of users: 
* the **Galaxy** orchestrator for creation of individual workflows, which facilitates the integration of other in-situ arrays (cross-domain or cross-RI), 
* the **Testbed** cloud infrastructure for a multi-user application (IN PROGRESS)

