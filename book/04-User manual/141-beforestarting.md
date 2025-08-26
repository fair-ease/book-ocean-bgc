---
title: Before starting
date : 2025-08-25
label: startingPoint
---

This user manual is accompanied by screenshots to guide you in the **Q**ualification, **C**alibration, **V**alidation of your BGC dataset measured by Argo Float and by Glider for the moment. If you have any difficulties, or suggestions for improvement, [please contact us](#contact).

### Preprocessing of original files 
The original files must be pre-processed in order to use the same tools regardless of their origin. This pre-processing is performed by the *`QCV harmonizer`* tool, which :
- harmonizes vocabulary and format 
- aggregates multiple files from the same platform.

This tool is currently operational for Argo float, World Ocean Atlas, and Gliders.

### Visualisation tools
The visualisation tools include : 
- *`ODV collection manager`* for creating Ocean Data View (ODV) spreadsheet collection from the QCV harmonized file(s). This tool also create an ODV view for Nitrate qualification 
- *`ODV history manager`* for reporting QC changes in the QCV harmonized file(s)
- [Embedded](#odv) `ODV` software for visualizing or qualifying the dataset

### Biogeochemical calibration tool
Currently, the `Biogegeochemical calibration` tool is operational for **nitrate**.

:::{important}
Because oxygen concentration is implied in the estimation of the `nitrate adjustment from neural network method`, platforms to be calibrated need to have `oxygen with a good quality` that means adjusted in real time or delayed mode for Argo float or glider.
:::

:::{note} for Argo floats
The calibration tool includes “DMfiller” functionalities to report DMQC (adjustment information and/or QC changes and DM operator information) in the original files and create BD argo files.
:::
