---
title: Context & Backgrounds
date : 2025-07-22
---

*Here below is adapted from the text written in the frame of the OSCARS proposal regarding the technical section. The proposal aims at developing the sequel of the Q.C.V service (proposal to continue the pilot development with the Chlorophyll-a workflow and the integration of an embedded web service into testbed) and reaching an overall TRL8.*

The Ocean BGC pilot aims at implementing and reaching a Technical Readiness Level (TRL) of 7 at least for a web service that seamlessly orchestrates and parameterizes the unitary tools needed for the Qualification, Calibration and Validation (Q.C.V) of oceanic BioGeoChemical (BGC) variables. It focuses on the Q.C.V workflow of BGC playing a key role in the carbon cycle:  
* **Nitrate**, a key phytoplankton nutrient : [https://biogeochemical-argo.org/measured-variables-nitrate.php](https://biogeochemical-argo.org/measured-variables-nitrate.php)
* **Chlorophyll-*a* concentration** (Chlorophyll-*a* hereafter), the universal proxy for the phytoplankton biomass (*in prorgess*): [https://biogeochemical-argo.org/measured-variables-chlorophyll-a.php](https://biogeochemical-argo.org/measured-variables-chlorophyll-a.php)

```{image}  https://github.com/fair-ease/book-ocean-bgc/blob/vracape/embedded-ressources/S111-F1_BGC-QCV-webPlatform_workflow_user-actions.png
:alt: userWorkflow
:width: 500px
:align: center
```

<!-- ```{image}  
:alt: argo_network
:width: 500px
:align: center
```
```{image}  
:alt: glider_network
:width: 500px
:align: center
``` -->

The specificity of Argo floats and sensors are two-folds: real-time transmission and remote calibration. The real-time transmission is performed through satellite communication, and data are distributed within 6 to 12 hours of the collection to all users, including a first round of real-time quality control checks (robust and conservative tests to detect gross outliers, such as spikes, which are mostly coming from transmission isolated issues). This quick transmission specifically benefits Argo operational users (climate and ocean forecasts and reanalyses). Regarding the remote calibration: as Argo floats are autonomous and stay for long periods of time at sea, they can not be recalibrated in lab conditions. Thus other remote techniques are employed and are fully described hereafter within the Q.C.V workflows.

Q.C.V workflows aim at providing end-users with high-quality dataset. Indeed, sensors can be affected by various phenomena: quality codes must be applied (qualification), sometimes data must be adjusted (calibration) and adjustments must be validated against independent datasets (validation). 
The most known phenomenon affecting sensors is the drift in time, for which calibration is needed after some time, using close-by accurate reference data (as there is no access to the sensor for a direct calibration). For some parameters, reference data are not accessible and neural-network techniques are used to build them from a proxy (e.g. oxygen), which slightly increases the uncertainty. Other sensor-specific phenomena exist. For instance the Chlorophyll-a measurements are affected by the quenching: a non-linearity arising in the relationship between fluorescence (what the sensor primarily measures) and Chlorophyll-a when the sun is at the zenith.

Q.C.V operators (also called delayed mode operators) are facing many challenges. They must use and chain several tools, specific to the phenomena influencing the variable and to the reference data availability. Several coding languages coexist (R, python, Matlab, etc.), depending on the preference of the tool developer. Added to this complexity are the platform used (HPC, own laptop, linux/windows, etc.), and ancillary data access performances. This is a major barrier for Q.C.V processing efficiency for two reasons: long and complex installation and uptake of the tools. This implies difficulty to on-board new human resources in a context of growing demand, which is particularly true for the Argo array dataset.
Following Open Science and subsequent FAIR principles, the Ocean BGC pilot provides operators with a seamless orchestration of the necessary tools, to easily perform complete Q.C.V workflows and provide guidance for the tools parameterisation. This service will be integrated in two infrastructures, allowing engaging different kinds of users: 

* the **[Galaxy](https://earth-system.usegalaxy.eu/login/start)** orchestrator for creation of individual workflows, which facilitates the integration of other in-situ arrays (cross-domain or cross-RI), 
* the **Testbed** cloud infrastructure for a multi-user application (*in progress*)

