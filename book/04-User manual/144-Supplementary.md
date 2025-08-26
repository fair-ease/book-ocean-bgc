---
title: Supplementation
date : 2025-08-25
---

(my-chapterODV)=
### How to use ODV
Here below are a few tips for ODV beginners, answering the very basic needs necessary for performing the QCV BGC qualification.

#### Open ODV collection spreadsheet
:::{admonition} ODV is open with its home page. 
:label: openODV
To open new data set, click on the top left : 
- Click on **Import**
- Click on **ODV spreadsheet...**, The *Select Spreadsheet File(s)* popup window opens
- Go to the directtory *working/Documents/ODV/galaxy/data/*
- Be sure that *Files of Types* (at the bottom of the pop-up window) is *Spreadsheet Files (*.txt, *.csv)* 
- Selection your ODV collection spreadsheet
- Click on **Open**

Your collection is now open.
:::

#### Qualify your data with ODV
:::{admonition} How to create the bottom right figure from a virgin view !!!.
- Right click in a void area on the ODV panel, select **layout** then **layout template**  then **1 SCATTER window**.
- In the right panel, under the **Sample** section. Right click on any of the parameters and select **derived variables …**.
- In the pop-up window, select *Special/Quality Flag value* and click on **add**. 
- In the new pop-up window, select nitrate_raw [micromole/kg], then click on **ok**, and **ok** again. The new derived variable is appended at the end of the **Sample** list. 
- Back on the plot, right click on the middle of the plot. Select **X-Variable**, in the pop-up window, select **nitrate_raw [micromole/kg]**, then click on **ok**.  
- Again right click on the middle of the plot. Select **Z-variable**; in the pop-up window, select **drvd: QF_nitrate_raw**, then click on **ok**. 
- Again right click on the middle of the plot. Select **properties**. In the **General** sheet, select **Palette = Ferret_blue_orange**. In the *Data* sheet, select **Z-Axis/Colorbar settings**, and indicate minimum = 49 (ODV QC for Argo QC1) and maximum =  52 (ODV QC for Argo QC4).
:::

:::{admonition} How to zoom inside a figure
- Right click on the figure, select **Zoom**. A red rectangle appears on the figure. 
- Adapt the shape as desired by left-clicking on the corner or middle of a segment and moving the mouse. 
- Once ok, left-double click in the figure.

N.B.: Sometimes, while selecting the Zoom menu several times in a row, the Zoom menu can appear as “unselectable” in grey color. Just be patient, wait a few seconds, and try again.

N.B.2: to zoom out: either select **Full range** or **Auto-Zoom out**.
:::

:::{admonition} How to change a QC for a point
on the vertical profile figure, 
- select the point for which the QC must be changed. 
- On the right panel, section **Sample**, 
- go to the parameter **Nitrate_raw** .
- On its line, right click on the value or on the QC value. 
- Select **Assign quality flag** and then **Current sample**. 
- In the pop-up window that opens, select the new quality flag (e.g. “4: bad data”), then **Ok**. 

If the Z-value is defined as the derived parameter as described above, then you can observe that the dot color in the figure has changed. If the Z-value is defined as the **original qc value**, you won’t see anything on the figure (unless you change the qc value of this variable).
:::

:::::{admonition} How to change a QC for a series of point
::::{tab-set}
:::{tab-item}	for a whole profile
Perform the same steps as for changing the QC for one observation point, but select **All samples of Current Station**
:::

:::{tab-item}	for all the points visible in the **zoomed** figure.
Zoom for the visible window to encompass only the points for which you want to change the QC value. Perform the same steps as for changing the QC for one observation point, but select **All samples of Window x**. To know which window you must select, when your mouse is on the plot, read the bottom line with the coordinate values of the mouse pointer, the number of the current plot window is mentioned.
:::
::::
:::::
#### Load view from ODV
:::{admonition} (re)load view
:label:loadview
if the view has not properly launched, you can load it from the ODV menu. On the top bar:
- click on **View**, then **Load Views …**. 
- In the pop-up window, navigate in the repository, up to *…/working/Documents/ODV/galaxy/views*
- Select ***qualitfication_startingPoint_nitrate.xview.xview*** file (ot other one) and click on Open. 

The figure xx view should appear now.
:::

### xView creating by the ODV collection manager

#### Supplemental analyses using Galaxy

```{image}  https://github.com/fair-ease/book-ocean-bgc/blob/vracape/embedded-ressources/sign-2408065_1280.png
:alt: travaux
:width: 500px
:align: center
```