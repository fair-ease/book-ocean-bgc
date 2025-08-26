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
Once you are login, Galaxy is divided into 4 vertical panels whose : 
- the far left : **<span style="color:gold">Galaxy action list</span>** with “interactive Tools”, “Upload”, “Tools” …
- the far right : **<span style="color:gold">History</span>** section.

See figure below.

```{image}  ../../embedded-ressources/figures/S141a_history.png
:alt: figa
:width: 500px
:align: center
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
    - Click on {**<span style="color:gold">Operations</span>**} - See figure below
    - Select **Copier des jeux de données** in the pop-up
    - In the central panel left to history section, select the file(s) you want to copy from the **source** history (left) to the **destination** history (right)


```{image}  ../../embedded-ressources/figures/S141a_operations.png
:alt: figb
:width: 500px
:align: center
```
:::

#### Nitrate Calibration
:::{important}
Because oxygen concentration is implied in the estimation of the `nitrate adjustment from neural network method`, platforms to be calibrated need to have `oxygen with a good quality` that means adjusted in real time or delayed mode for Argo float or glider.
:::

### Manage your data

#### Step1 : Get your data
::::{tab-set}
:::{tab-item} from the S3 server
For uploading the argo data files (meta, core and BGC) of the float 4903881 from the S3 service: 
- Click on **Upload** (see `a` on the figure below) on the **<span style="color:gold">Galaxy action list</span>** vertical panel on the left. A pop-up window will open.
- Click on **Choose from repository** (see `b` on the figure below) at the bottom of the pop-up. A new pop-up window will open.
- Search *argo* in the top search bar. *<span style="color:LightSkyBlue">Argo marine floats data and metadata from Global Data Assembly Centre (Argo GDAC)</span>* appears in the label column just below
- Select it, then *<span style="color:LightSkyBlue">pub/dac/coriolis/4903881</span>* and tick *4903881_meta.nc* & *profiles/* 
- Click on **Select** on the bottom right of the pop-up. The list of the files to download is displayed (see `c` on the figure below)
- Remove the Synthetic files *SR4903881_*.nc* (not useful for qualification & calibration actions) by clicking on the corresponding trash icon on the right
- Click on **Start** on the bottom of the pop-up. Once the download is completed (green color), close the window;

Wait until all files are stored in your history on the right (green color).

```{image}  ../../embedded-ressources/figures/S142-S3.png
:alt: figc
:width: 500px
:align: center
```
:::

:::{tab-item} from your computer
<!-- :class: dropdown -->
for uploading the argo data files (meta, core and BGC) of the float 4903881 or Word Ocean Atlas climatology from your computer: 
- Click on **Upload** (see `a` on the figure below) on the **<span style="color:gold">Galaxy action list</span>** vertical panel on the left. A pop-up window will open.
- Click on **Choose local file** (see `b` on the figure below) at the bottom of the popup. Your directory window will open.
- Select file(s) to be added and Click on **Open** at the bottom of the popup. The list of the files to download is displayed (see `c` on the figure below)
- Click on **Start** on the bottom of the pop-up. Once the download is complete (green color), close the window.

Wait until all files are stored in your history on the right (green color).


```{image}  ../../embedded-ressources/figures/S142-fromComputer.png
:alt: figd
:width: 500px
:align: center
```

:::
::::

#### Step2 : Organize your data
For creating a dataset list/collection, useful for platforms with many NetCDF original files as the Argo float 4903881.

Not useful for WOA

Choose below the case corresponding to your **<span style="color:gold">history</span>** section before dowloading 4903881 files
::::{tab-set}
:::{tab-item} From empty history
- Click on {**Select item**}  (see `a` on the figure below)
- Click on **Select all** that has just appeared on the right  (see `b` on the figure below)
- Click on  **All ## selected** that just replaced **Select all**. A window will pop up just below
- Select **Auto build list**. A pop-up window will open in the central panel
- Enter the name of the data collection : 4903881 (see `c` on the figure above)
- Turn off **Remove the file extension** (see `d` on the figure above)
- Click on **Build** on the bottom right of the pop-up (see `e` on the figure above)

Once the collection is ready, everything is green in the history panel. It is possible to limit the history to useful files or collections by clicking on the eyes above the files list in the history.

  ```{figure}  ../../embedded-ressources/figures/S142-historyempty.png
  :label: fige
  :width: 900px
  :align: center
  ```
  ```{figure}  ../../embedded-ressources/figures/S142-collection.png
  :label: figf
  :width: 900px
  :align: center
  ```
:::

:::{tab-item} From NOT empty history
- Click on {**Select item**}  (see `a` on the figure below)
- Tick all interesting files
- Click on  **## of ## selected**  (see `b` on the figure below). A window will pop up just below
- Select **Auto build list**. A pop-up window will open in the central panel
- Enter the name of the data collection : 4903881 (see `c` on the figure above)
- Turn off **Remove the file extension** (see `d` on the figure above)
- Click on **Build** on the bottom right of the pop-up (see `e` on the figure above)

Once the collection is ready, everything is green in the history panel. It is possible to limit the history to useful files or collections by clicking on the eyes above the files list in the history.

  ```{figure}  ../../embedded-ressources/figures/S142-historyNotempty.png
  :label: figg
  :width: 900px
  :align: center
  ```
  ```{figure}  ../../embedded-ressources/figures/S142-collection.png
  :label: figh
  :width: 900px
  :align: center
  ```
:::
::::

### Harmonize your data
Run `QCV harmonizer` (see section [Before starting](#startingPoint) for more details) for creating the harmonized in format and vocabulary NetCDF file by following these instructions : 
- Click on **Tools** just below **Upload** on the  **<span style="color:gold">Galaxy action list</span>** vertical panel on the left (see `a` on the figure below) . A new vertical panel called **Tools** appears next to the **<span style="color:gold">Galaxy action list</span>** vertical panel.
- Search `QCV harmonizer` in the **<span style="color:gold">top search bar</span>**
- Select the tool. Its **<span style="color:gold">parametrization page</span>** appears on the center
- In the blue box and below *Input the Netcdf data files* (see on the figure)
    - for a dataset collection such as 4903881, select {*Dataset collection*} then click on **Select Value**. A window with files listed in your history opens. Select *4903881*
    - for WOA, select {*Single dataset*} then click on *Select Value*.  A window with files listed in your history opens. Select *woa###.nc* file

:::{note}
If your file is not listed in the window, you can drag and drop  it from the history section to *Select value* box.
:::

- Run the tool by clicking on the corresponding button below (see `b` on the figure below).

At the end of the process, the tool delivers an harmonized file, ***###_harm.nc*** (since version 3.0 of the tool), ready for analysis.

```{image}  ../../embedded-ressources/figures/S142-harmonizer.png
:alt: figharmo
:width: 500px
:align: center
```

<!-- ### Qualify your data
#### Step1 : Creation of the ODV collection
:::{admonition} How to run ODV collection manager
:class: dropdown
```{image}  ../../embedded-ressources/figures/sign-2408065_1280.png
:alt: travaux
:width: 500px
:align: center
```
::: -->

### Calibrate your data
### Validate your data