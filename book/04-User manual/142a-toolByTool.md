---
title: Tool by tool
date : 2025-08-25
label: toolbytool
---

:::{important} Before starting
Before running the QCV procedure tool by tool, be sure that your environement ([prerequisite and data management](#galaxyUserManual1)) are ready!
:::

::::{important} Then !
:::{contents}
:depth: 1
:::
::::


### Harmonize your data
Run `QCV harmonizer` ([What is it?](#qcvharmonizer)) for creating the harmonized in format and vocabulary input data file(s) by following these instructions : 
- Click on **Tools** just below **Upload** on the  **<span style="color:gold">Galaxy action list</span>** vertical panel on the left (see `a` on @figure-10) . A new vertical panel called **Tools** appears next to the **<span style="color:gold">Galaxy action list</span>** vertical panel.
- Search `QCV harmonizer` in the **<span style="color:gold">top search bar</span>** (@figure-10)
- Select the tool. Its **<span style="color:gold">parametrization page</span>** appears on the center (@figure-10)
- In the blue box and below *Input the Netcdf data files* (@figure-10)
    - for a dataset collection such as 4903881,
        - Select {*Dataset collection*} then click on *Select Value*. A window with files listed in your history opens.
        - Select *4903881*
    - for WOA,
        - Select {*Single dataset*} 
        - Then click on *Select Value*.  A window with files listed in your history opens. 
        - Select *woa###.nc* file

:::{note}
:label: draganddrop
If your file is not listed in the window, you can **drag and drop**  it from the history section to *Select value* box.
:::

- Run the tool by clicking on the corresponding button below (see `b` on @figure-10).

Once the [QCV harmonizer outputs](#qcvharmonizer) are ready, the harmonized file is  available in the **<span style="color:gold">history</span>** section (green color) 

::: {note}
Run the tool one by one for all platforms and/or reference data set (such as WOA) import in your **<span style="color:gold">history</span>** section and need to perform the full QCV workflow
:::

```{figure}  ../../embedded-ressources/figures/S142-harmonizer.png
:label: figure-10
:width: 900px
:align: center
Q.C.V harmonizer tool on Galaxy
```
### Qualify your data
#### Step1 : Creation of the ODV collection

Run `ODV collection manager`  ([What is it?](#odvcollmanager)) for creating Ocean Data View (ODV) spreadsheet collection and qualifying the dataset. Please, follow the instructions : 
- Click on **Tools** just below **Upload** on the **<span style="color:gold">Galaxy action list</span>** vertical panel on the left (see `a` on @figure-11). A new vertical panel appears. 
- Search `ODV collection manager` in the **<span style="color:gold">top search bar</span>** (@figure-11)
- Select the tool. Its **<span style="color:gold">parametrization page</span>** appears on the center (@figure-11)
- For *Input raw data*,
    - Select {*Multiple Datasets*}, then click on *Select Value* (@figure-11)
    - A window with files listed in your history opens
    - Select *4903881_harm.nc*

:::{note}
Multiple datasets could be selected for merging them in a unique ODV collection and working on multiple platforms at the same time.
:::

:::{admonition} Add reference datasets (optional)
:class: dropdown
It is possible to add a reference dataset as WOA in the ODV collection spreadsheet for comparison. For that, add the harmonized reference data file in the section *Input reference data* (see “b” on @figure-11). 

For big file, a subsetting is possible. Please report to the [tool details](#odvcollmanager) or just below.
:::


- (optional) It is possible to change the @defaultODV by selecting *Yes, I to write my own configuration file* at the question *Select if you want to write your own configuration file or not* (see `c` on @figure-11) : 
    - *operator name* = Enter your name
    - *QC convention  for the output file* = Select one [QC flag scale understanding by ODV](https://odv.awi.de/fileadmin/user_upload/odv/docs/ODV_quality_flag_sets.pdf)
    - *Subsetting* = 1 (yes it is), 0 (no), -1 (for float crossing 180°E/W)
    - *plt*  = 0 (no plot), 1( yes)
- Run the tool by clicking on the corresponding button below (see `d` on  @figure-11).

Once the [ODV collection manager outputs](#odvcollmanager) are ready, files are available in the **<span style="color:gold">history</span>** section (green color) (@figure-11) through :
- the galaxy collection ***ODV tool collection*** (include all outputs)
- the galaxy file ***ODV collection manager output***  (= *odv_collection.txt*)


```{figure}  ../../embedded-ressources/figures/S142-odvcoll.png
:label: figure-11
:width: 900px
:align: center
ODV collection manager tool on Galaxy
```

#### Step 2 : Launch ODV automatically
##### ODV interactive tool parametrization
For launching ODV interactive tool automatically, follow the instructions : 
- Click on **Tools** just below **Upload** (see `a` on @figure-12) or **Interactive Tools** just above (see `b` on @figure-12) in the **<span style="color:gold">Galaxy action list</span>** vertical panel on the left. A new vertical panel appears. 
- Search **ODV** interactive tool in the **<span style="color:gold">top search bar</span>**  (@figure-12)
- Select the tool. Its parametrization page appears on the center (@figure-12)

:::{warning}
Before selecting the ODV collection to be visualized, be sure that the **<span style="color:green">tool version</span>** is v5.8_1 at least the first grey headband on the top of the central panel (@figure-12). For changing the version, please click on the 3 cubes available on the left.
:::

- At the question *Do you want your data to be automatically load when ODV is launched?*  (see `c` on @figure-12), answer *Yes, I want my data to be loaded directly*. This is useful to open directly the odv collection, and with a specific view if this last one is available.
- At the question *Netcdf or tabular text file. For text file, odv format is recommanded* (see `d` on @figure-12), 
    - select {*Dataset collection*}, then “ODV collection manager output,
**or**
    - select {*single dataset*}, drag and drog ****odv_collection.txt*** from ***odv tool collection*** available in the **<span style="color:gold">history</span>** section
- At the question **Do you have a view?** (see `e` on @figure-12), answer *Yes, I have my own view*. A *Data view* selection panel appears (see `f` on @figure-12).
- Click on ***ODV tool collection*** in the **<span style="color:gold">history</span>** section
- Drag and Drop ***qualification_startingPoint_nitrate.xview*** in the Data view panel
- Run the tool (see `g` on @figure-12)

```{figure}  ../../embedded-ressources/figures/S142-ODVlaunch1.png
:label: figure-12
:width: 900px
:align: center
Parametrisation of ODV interactive tool on Galaxy
```
:::{error} ODV is open with its home page!!!!
:class:dropdown
[Read me](#openODV) for opening your collection
:::

:::{error} ODV is open with map view!!!!
:class:dropdown
[Read me](#loadview) for reload the qualification view
:::

##### Open ODV interactive tool
:::{admonition} launch an interactive tool
:label: interactivetool
When the ODV interactive tool is ready,
- a red dot with the number “1” appears on the **Interactive tool** button in the vertical panel on the left of the **<span style="color:gold">Galaxy action list</span>**. Click it (see `a` on @figure-13). A new vertical panel appears in the center. 
- Launch the ODV interactive tool by clicking the “expended” symbol (see `b` on @figure-13). This can take a few minutes. Don’t hesitate to refresh the page. ODV opens in a new window automatically with the selected view (@figure-14)
:::

```{figure}  ../../embedded-ressources/figures/S142-ODVlaunch2.png
:label: figure-13
:width: 900px
:align: center
How to launch ODV interactive tool on Galaxy

```
:::{note}
3 potential ODV output appears in the history section in orange. These become green when ODV will be close properly (at the end of your actions) (see  @figure-12 and @odvoutput)
:::

:::{note}
After a few minutes of inactivity, the ODV window may turn off. Don't panic, just refresh the web page.
:::


```{figure}  ../../embedded-ressources/figures/S142-nitrateView.png
:label: figure-14
:width: 900px
:align: center
Default view when performing called ***qualification_startingPoint_nitrate.xview*** creating by `ODV collection manager` 

```

#### Step3 : Qualify the dataset with ODV 
Many useful information are available in the [Supplementation section for ODV](#my-chapterODV)

#### Step4 : Export history once qualification is finished.
:::{warning}
Be sure that all filters ([how to do?](#filterout))or zoom windows are relaxed ([How to do?](#outzoom)).
:::

To export history information, 
- Click on the top left **Export** > **History**
- The *Export station history* opens, with a default name ***history_from_odv_collection.txt*** with our example; 
- Go to *working/Documents/ODV/galaxy/outputs*
:::{important}
DO NOT CHANGE THE DEFAULT NAME OF THE HISTORY FILE
:::
- **Save** > **OK** > **OK**
- close ODV by clicking on top left **File** > **exit**

Once the ODV interactive tool closed, the 3 potential odv outputs are now available (green color) in the **<span style="color:gold">History</span>** section (@figure-12). Only 2 are useful for the next steps.

##### ODV Tool outputs
::: {admonition} ODV interactive tool outputs
:label:odvoutput
***ODV all outputs*** (galaxy collection)
- ***data_odv_collection.zip*** (all odv output files in a zip)
- ***history_from_odv_collection.txt***
- ***odv_collection.odv***
- ***odv_collection.txt*** (creating with odv collection manager)

***ODV history extracted*** with the history txt files (same as history_from_odv_collection.txt).
:::

#### Step5 : (optional) Report QC & Data changes 
For reporting your QC flags & data changes into the harmonized dataset before calibrating the nitrate sensor, run `ODV history manager` tool (tool details in [Before starting](#startingPoint)). For that, please : 
- Click on **Tools** just below **Upload** on the vertical panel **<span style="color:gold">Galaxy action list</span>** on the left (see `a` on @figure-15). A new vertical panel appears. 
- Search `ODV history manager` in the **<span style="color:gold">top search bar</span>** (@figure-15)
- Select the tool. Its **<span style="color:gold">configuration page</span>** appears on the center (@figure-15)

Please below, select the odv collection spreadsheet open with ODV to have futher instructions
::::{tab-set}
:::{tab-item} collection manager output 
- In **Tool Parameters** section (see `b,c,d` on @figure-15):
    - **Input NetCDF data** : Select the harmonized NetCDF file(s) ***###_harm.nc*** created by `Q.C.V harmonizer`
    - **Input history text file** : Select ***ODV history extracted*** txt file extracted from ODV after changes by step 4
    - **Input ODV file** : Select ***ODV collection manager output***, the ODV spreadsheet txt collection created by `ODV collection manager` and visualize with ODV for QC changes
:::

:::{tab-item} odv_collection.txt
- In **Tool Parameters** section (see `b,c,d` on @figure-15):
    - **Input NetCDF data** : Select the harmonized NetCDF file(s) ***###_harm.nc*** created by `Q.C.V harmonizer`
    - **Input history text file** : Select ***history_from_odv_collection.txt*** txt file from ***ODV all output*** extracted from ODV after changes by step 4
    - **Input ODV file** : Select ***odv_collection.txt*** from ***ODV tool collection***, the ODV spreadsheet txt collection created by `ODV collection manager` and visualize with ODV for QC changes

:::
::::

- (optional) It is possible to change the @defaultHistory by selecting *Yes, I to write my own configuration file* for the question *Select if you want your own configuration file* (see `e` on @figure-15) : 
    - *QC convention for the ODV output file* = Select one [QC flag scale understanding by ODV](https://odv.awi.de/fileadmin/user_upload/odv/docs/ODV_quality_flag_sets.pdf)
    - ODV edits to be reported: 
        - EDITFLAGS (report QC changes from the history to the data collection) 
        - EDITDATA (report data changes from the history to the data collection).
:::{note} ODV edits parametrization
You can unselect one of them (if you want to report only QC changes or only data changes). However, you can not unselect both of them. If you do so in the interface, the contrary will happen: both edit types will be reported in the backend routine.
:::

-  Run the tool by clicking on the corresponding button below (see `f` on @figure-15). 

At the end of the process, the tool outputs are now available (green color) in the **<span style="color:gold">History</span>** section (@figure-15) and ready for running the `Biogechemical Calibration` tool.

- Check the tool logs, once the tool has finished. Indeed, at present, when it does not succeed, it is not yet correctly color-coded. This will be managed in the future. In the meantime, within the “ODV history manager log files” collection, view the first file ***YYYY-MM-DDTHHMM_galaxy_odv-history-manager_history*** by clicking on the “eye” icon on the right of the file. Check that the QC changes you performed were correctly reported. If you encounter issues, make sure you respect the file name conventions at step 4. If you still don’t find why it does not work, send an email to the [contact point](#contact).

```{figure}  ../../embedded-ressources/figures/S142-history.png
:label: figure-15
:width: 900px
:align: center
ODV history manager parametrization

```

##### Default parametrization
:::{admonition} Default parametrization
:label: defaultHistory 
<!-- :class: dropdown -->
- *QC convention  for the ODV output file* = ARGO QC flag scale (reference table 2 in [argo data management manual](https://archimer.ifremer.fr/doc/00228/33951/32470.pdf))
- *ODV convention regarding changes performed on the ODV collection* =
    - EDITFLAGS (report QC changes from the history to the data collection) 
    - EDITDATA (report data changes from the history to the data collection).
:::

##### Tool output
:::{admonition} ODV history manager outputs
:label: outputHistory 
<!-- :class: dropdown -->
***ODV history manager log files*** (galaxy collection)
- ***YYYY-MM-DDTHHMM_galaxy_odv-history-manager_history*** (log including results of all tool actions like QC reporting)
- other technical log and state files

***ODV history manager csv collection*** (galaxy collection)
- ***###_harm_history*** csv files summarizing user changes (as many files as platform have been qualified)

***ODV history manager netcdf collection*** (galaxy collection)
- ***###_harm_qced.nc*** extended NetCDF files including changes (as many files as platform have been qualified)

:::

### Calibrate your data
### Validate your data