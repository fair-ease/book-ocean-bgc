---
title: Before starting
date : 2025-08-25
label: startingPoint
---

This user manual is accompanied by screenshots to guide you in the **Q**ualification, **C**alibration, **V**alidation of your BGC dataset measured by Argo Float and by Glider for the moment. If you have any difficulties, or suggestions for improvement, [please contact us](#contact).

The easy Q.C.V BGC toolkit is organized like this :

:::{contents}
:depth: 3
:::

### Preprocessing of original files 
The original files must be pre-processed in order to use the same tools regardless of their origin. This pre-processing is performed by the *`QCV harmonizer`* tool.

:::{admonition} QCV harmonizer details
:label: qcvharmonizer
This tool : 
- harmonizes vocabulary and format 
- aggregates multiple files from the same platform into one single file.

Its `output` is : 
- a single NetCDF file named `###_harm.nc` (since version 3.0 of the tool)

This tool is currently operational for Argo float, World Ocean Atlas, and Gliders.
It should be run as many time as there are dataset/platforms
:::

### Visualisation tools
The visualisation tools for the qualification, the validation and the extraction or the reporting of the user actions include `ODV` software, the *`ODV collection manager`* and *`ODV history manager`*. Read details below.

:::{admonition} Ocean Data View (ODV)
`ODV` is a software for visualizing and/or qualifying scientific data. It can be used localy or directly on [Galaxy instance](#odv)
:::

::::{admonition} ODV collection manager details
:label: odvcollmanager

This tool creates :
- Ocean Data View (ODV) spreadsheet collection from the QCV harmonized file(s) based on the [ODV user's guide version 5.7.0](https://odv.awi.de/fileadmin/user_upload/odv/docs/ODV_guide.pdf) by bringing together as many plastform or reference harmonized datasets are needed
- ODV view for Nitrate qualification

This tool is able : 
- to map the input with expected output QC flag scale if the information is available in the harmonized file and in the [odv software](https://odv.awi.de/fileadmin/user_upload/odv/docs/ODV_quality_flag_sets.pdf)
- to subset harmonized reference data set used for comparison. subsetting option : 1 (subset), 0 (no subset), -1 (inverse subset for float crossing 180°E/W)

:::{admonition} ODV collection manager default parametrization
:label: defaultODV 
:class: dropdown
- *operator name* = anonymmous
- *QC convention  for the output file* = ARGO QC flag scale (reference table 2 in [argo data management manual](https://archimer.ifremer.fr/doc/00228/33951/32470.pdf))
- *Subsetting* = 1 (yes it is, even there are no “input reference data”)
- *plt* or plot = 0 (no plot showing the subsetting results) 
:::

Its `outputs` are : 
- `odv_collection.txt`,  an ODV spreadsheet collection merging raw (argo or glider) and reference hamonized file
- `qualification_startingPoint_nitrate.xview`, a ODV view made helping in the Nitrate qualification step
- `YYYY-MM-DDTHHMM_galaxy_odv-coll-manager_QV.log`, a log file summarizing all actions performed by the tool with success or not
- other technical /log and .state

::::

::::{admonition} ODV history manager details
:label: odvhistmanager
This tool extracts the QC changes (EDITFLAGS) and edit data (EDITDATA) from the ODV history file and reports them into the QCV harmonized file(s).
The tool manages 2 types of ODV history file : 
- *synthetic* from the manual export
- *extended* from the automatic export (not available on galaxy for the moment)
it is also able to map the QC flag scale used by [odv software](https://odv.awi.de/fileadmin/user_upload/odv/docs/ODV_quality_flag_sets.pdf) and asked during the ODV spreadsheet creation (see above) with the output harmonized file if the information is available 

:::{admonition} Default parametrization
:label: defaultHistory 
:class: dropdown
- *QC convention  for the ODV output file* = ARGO QC flag scale (reference table 2 in [argo data management manual](https://archimer.ifremer.fr/doc/00228/33951/32470.pdf))
- *ODV convention regarding changes performed on the ODV collection* =
    - EDITFLAGS (report QC changes from the history to the data collection) 
    - EDITDATA (report data changes from the history to the data collection).
:::

Its `outputs` are :
- `###_harm_qced.nc` : extended NetCDF files including changes (as many files as platform have been qualified)
- `###_harm_history.csv` : csv files summarizing user changes (as many files as platform have been qualified)
- `YYYY-MM-DDTHHMM_galaxy_odv-history-manager_history.log` : log file summaring status of the QC & data changes by platform
- other technical log and state files
 
::::

### Biogeochemical calibration tool
Currently, the `Biogegeochemical calibration` tool is operational for **nitrate** and using [Method 1](#Nitrate1).

:::{important}
Because oxygen concentration is implied in the estimation of the `nitrate adjustment from neural network method`, platforms to be calibrated need to have `oxygen with a good quality` that means adjusted in real time or delayed mode for Argo float or glider.
:::

:::{note} for Argo floats
The calibration tool includes “DMfiller” functionalities to report DMQC (adjustment information and/or QC changes and DM operator information) in the original files and create BD argo files.
:::
