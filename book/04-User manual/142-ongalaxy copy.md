---
title: How to run Easy Q.C.V BGC on Galaxy
date : 2025-08-25
label: galaxyUserManual1
---

The next sections explain how to qualify and calibrate the nitrate sensor mounted on the argo float 4903881 tool by tool or running a pre-design galaxy workflow. For your information, execution time for running tools depends on the number of files, their size and/or the number of people working on Galaxy.

:::{warning}
DO NOT change file names to ensure that any changes you make with ODV will be carried over. However, it is possible to change the name of <span style="color:green">galaxy collections</span> to make them easier to find.
:::

### Prerequisites

#### Galaxy
:::{admonition} Galaxy account
<!-- :class: dropdown -->
Create or Login to your [Galaxy europe account](https://earth-system.usegalaxy.eu/login/start)
:::

:::{admonition} Galaxy tips and tricks
:class: dropdown
Once you are login, Galaxy is divided into 4 vertical panels whose (@figure-1): 
- the far left : **<span style="color:gold">Galaxy action list</span>** with “interactive Tools”, “Upload”, “Tools” …
- the far right : **<span style="color:gold">History</span>** section.


```{figure}  ../../embedded-ressources/figures/S141a_history.png
:label: figure-1
:width: 500px
:align: center
Galaxy organisation
```

All symbols have a name that appears when you point your mouse on the symbol. Their name will be indicated with *{}* in the following tutorial.

The history section stores all your job results with the following color code :
- <span style="color:grey">grey : canceled</span>
- <span style="color:orange">orange : running</span>
- <span style="color:green">green : finished with success</span>
- <span style="color:red">red : failed</span>


It is possible to organise your history with *sub-directory* :
- Creation of new history 
    - Click on the symbol **+** on the top-right in the history section 
    - Click on the pencil aligned to **Unnamed history**
    - Give an explicit name, annotation (optional), tag (optional)
    - Save
- Switching from one history to another one
    - Click on the symbole **⇄** on the top-right in the history section
    - Select the history in the pop-up
- Copy/paste dataset from one history to another one
    - Click on {**<span style="color:gold">Operations</span>**} (@figure-2)
    - Select **Copier des jeux de données** in the pop-up
    - In the central panel left to history section, select the file(s) you want to copy from the **source** history (left) to the **destination** history (right)


```{figure}  ../../embedded-ressources/figures/S141a_operations.png
:label: figure-2
:width: 500px
:align: center
Galaxy operation symbol
```
:::

#### Nitrate Calibration
:::{important}
Because oxygen concentration is implied in the estimation of the `nitrate adjustment from neural network method`, platforms to be calibrated need to have `oxygen with a good quality` that means adjusted in real time or delayed mode for Argo float or glider.
:::

::: {note} World Ocean Atlas
The nitrate calibration needs a potential reference data set such as the nitrate WOA annual climatology. For that, upload the [nitrate WOA annual climatology with NetCDF format](https://www.ncei.noaa.gov/thredds-ocean/catalog/woa23/DATA/nitrate/netcdf/all/1.00/catalog.html?dataset=woa23/DATA/nitrate/netcdf/all/1.00/woa23_all_n00_01.nc) directly from your computer.
:::

### Manage your data

#### Step1 : Get your data
::::{tab-set}
:::{tab-item} from the S3 server
For uploading the argo data files (meta, core and BGC) of the float 4903881 from the S3 service: 
- Click on **Upload** (see `a` on @figure-3) on the **<span style="color:gold">Galaxy action list</span>** vertical panel on the left. A pop-up window will open.
- Click on **Choose from repository** (see `b` on @figure-3) at the bottom of the pop-up. A new pop-up window will open.
- Search *argo* in the top search bar. *<span style="color:LightSkyBlue">Argo marine floats data and metadata from Global Data Assembly Centre (Argo GDAC)</span>* appears in the label column just below
- Select it, then *<span style="color:LightSkyBlue">pub/dac/coriolis/4903881</span>* and tick *4903881_meta.nc* & *profiles/* 
- Click on **Select** on the bottom right of the pop-up. The list of the files to download is displayed (see `c` on @figure-3)
- Remove the Synthetic files *SR4903881_*.nc* (not useful for qualification & calibration actions) by clicking on the corresponding trash icon on the right
- Click on **Start** on the bottom of the pop-up. Once the download is completed (green color), close the window;

Wait until all files are stored in your history on the right (green color).

```{figure}  ../../embedded-ressources/figures/S142-S3.png
:label: figure-3
:width: 500px
:align: center
Get your data from S3 server
```
:::

:::{tab-item} from your computer
<!-- :class: dropdown -->
for uploading the argo data files (meta, core and BGC) of the float 4903881 or Word Ocean Atlas climatology from your computer: 
- Click on **Upload** (see `a` on @figure-4) on the **<span style="color:gold">Galaxy action list</span>** vertical panel on the left. A pop-up window will open.
- Click on **Choose local file** (see `b` on @figure-4) at the bottom of the popup. Your directory window will open.
- Select file(s) to be added and Click on **Open** at the bottom of the popup. The list of the files to download is displayed (see `c` on @figure-4)
- Click on **Start** on the bottom of the pop-up. Once the download is complete (green color), close the window.

Wait until all files are stored in your history on the right (green color).


```{figure}  ../../embedded-ressources/figures/S142-fromComputer.png
:label: figure-4
:width: 500px
:align: center
Get your data from your computer
```
:::
::::

#### Step2 : Organize your data
##### Creation of a dataset list/collection
For creating a dataset list/collection, useful for platforms with many NetCDF original files as the Argo float 4903881.

Not useful for WOA

Choose below the case corresponding to your **<span style="color:gold">history</span>** section before dowloading 4903881 files
::::{tab-set}
:::{tab-item} From empty history
- Click on {**Select item**}  (see `a` on @figure-5)
- Click on **Select all** that has just appeared on the right  (see `b` on @figure-5)
- Click on  **All ## selected** that just replaced **Select all**. A window will pop up just below
- Select **Auto build list**. A pop-up window will open in the central panel
- Enter the name of the data collection : 4903881 (see `c` on @figure-6)
- Turn off **Remove the file extension** (see `d` on @figure-6)
- Click on **Build** on the bottom right of the pop-up (see `e` on @figure-6)

Once the collection is ready, everything is green in the history panel. It is possible to limit the history to useful files or collections by clicking on the eyes above the files list in the history.

  ```{figure}  ../../embedded-ressources/figures/S142-historyempty.png
  :label: figure-5
  :width: 900px
  :align: center
  Select data from empty history
  ```
  ```{figure}  ../../embedded-ressources/figures/S142-collection.png
  :label: figure-6
  :width: 900px
  :align: center
  Dataset creation list
  ```
:::

:::{tab-item} From NOT empty history
- Click on {**Select item**}  (see `a` on @figure-7)
- Tick all interesting files
- Click on  **## of ## selected**  (see `b` on @figure-7). A window will pop up just below
- Select **Auto build list**. A pop-up window will open in the central panel
- Enter the name of the data collection : 4903881 (see `c` on @figure-8)
- Turn off **Remove the file extension** (see `d` on @figure-8)
- Click on **Build** on the bottom right of the pop-up (see `e` on @figure-8)

Once the collection is ready, everything is green in the history panel. It is possible to limit the history to useful files or collections by clicking on the eyes above the files list in the history.

  ```{figure}  ../../embedded-ressources/figures/S142-historyNotempty.png
  :label: figure-7
  :width: 900px
  :align: center
  Select data from not empty history
  ```
  ```{figure}  ../../embedded-ressources/figures/S142-collection.png
  :label: figure-8
  :width: 900px
  :align: center
  Dataset creation list
  ```
:::
::::

##### File change extension
Because galaxy does not manage h5 extension very well, please change it for WOA(if needed). In the history section, 
- Select *woa###_.nc* file
- Click on the **pencil** on the right. A new window opens in the central panel (see `a` on @figure-9)
- Select **Datatype** (see `b` on @figure-9)
- Inform the *New Type* with *NetCDF* (see `c` on @figure-9)
- Save (see `d` on @figure-9)

  ```{figure}  ../../embedded-ressources/figures/S142-changeExtension.png
  :label: figure-9
  :width: 900px
  :align: center
  Change of file extension
  ```

### Harmonize your data
#### In vocabulary and format
Run `QCV harmonizer` (see section [Before starting](#startingPoint) for more details) for creating the harmonized in format and vocabulary NetCDF file by following these instructions : 
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
If your file is not listed in the window, you can **drag and drop**  it from the history section to *Select value* box.
:::

- Run the tool by clicking on the corresponding button below (see `b` on @figure-10).

Once the @harmnizeroutput are ready, the harmonized file is  available in the **<span style="color:gold">history</span>** section (green color) 

::: {note}
Run the tool one by one for all platforms and/or reference data set (such as WOA) import in your **<span style="color:gold">history</span>** section and need to perform the full QCV workflow
:::

```{figure}  ../../embedded-ressources/figures/S142-harmonizer.png
:label: figure-10
:width: 900px
:align: center
Q.C.V harmonizer tool on Galaxy
```
#### Tool outputs
::: {admonition} Q.C.V harmonizer tool output
:label:harmnizeroutput
<!-- :class: dropdown -->
one file by platform name ***###_harm.nc*** (since version 3.0 of the tool)
:::

### Qualify your data
#### Step1 : Creation of the ODV collection
##### How to create ODV collection spreadsheet
Run `ODV collection manager`  (see section [Before starting](#startingPoint) for more details) for creating Ocean Data View (ODV) spreadsheet collection and qualifying the dataset. Please, follow the instructions : 
- Click on **Tools** just below **Upload** on the **<span style="color:gold">Galaxy action list</span>** vertical panel on the left (see `a` on @figure-11). A new vertical panel appears. 
- Search `ODV collection manager` in the top search bar (@figure-11)
- Select the tool. Its parametrization page appears on the center (@figure-11)
- For *Input raw data*,
    - Select {*Multiple Datasets*}, then click on *Select Value* (@figure-11)
    - A window with files listed in your history opens
    - Select *4903881_harm.nc*

:::{important}
Multiple datasets could be selected for merging them in a unique ODV collection and working on multiple platforms at the same time.
:::

:::{admonition} Add reference datasets (optional)
:class: dropdown
It is possible to add a reference dataset as WOA in the ODV collection spreadsheet for comparison. For that, add the harmonized reference data file in the section *Input reference data* (see “b” @figure-11). 

For big file, a subsetting is possible. Please report to the @default section.
:::


- (optional) It is possible to change the @default by selecting *Yes, I to write my own configuration file* at the question *Select if you want to write your own configuration file or not* (see `c` on @figure-11) : 
    - *operator name* = Enter your name
    - *QC convention  for the output file* = Select one [QC flag scale understanding by ODV](https://odv.awi.de/fileadmin/user_upload/odv/docs/ODV_quality_flag_sets.pdf)
    - *Subsetting* = 1 (yes it is), 0 (no), -1 (for float crossing 180°E/W)
    - *plt*  = 0 (no plot), 1( yes)
- Run the tool by clicking on the corresponding button below (see `d` on  @figure-11).

Once the @odvcolloutput are ready, files and galaxy collection are available in the history (green color) (@figure-11)


```{figure}  ../../embedded-ressources/figures/S142-odvcoll.png
:label: figure-11
:width: 900px
:align: center
ODV collection manager tool on Galaxy
```
##### Default parametrization
:::{admonition} Default parametrization
:label: default 
<!-- :class: dropdown -->
- *operator name* = anonymmous
- *QC convention  for the output file* = ARGO QC flag scale (reference table 2 in [argo data management manual](https://archimer.ifremer.fr/doc/00228/33951/32470.pdf))
- *Subsetting* = 1 (yes it is, even there are no “input reference data”)
- *plt* or plot = 0 (no plot showing the subsetting results) 
:::

##### Tool outputs
::: {admonition} ODV collection manager tool output
:label:odvcolloutput
<!-- :class:dropdown -->
***ODV tool collection*** (a galaxy collection)
- ***odv_collection.txt***  (ODV spreadsheet collection with all files selected in *Input raw data* and *Input reference data*)
- ***qualification_startingPoint_nitrate.xview*** (useful ODV view for helping in the qualification step)
- ***YYYY-MM-DDTHHMM_galaxy_odv-coll-manager_QV.log*** (summarizing all actions performed by the tool)
- other technical /log and .state

***“ODV collection manager output”*** (galaxy file), that is an extraction of the ***odv_collection.txt*** mentioned above
:::

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
:::{admonition}
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