---
title: From a pre-designed workflow
date : 2025-08-25
label: workflow
---

:::{important} Before starting
Before running your or a public workflow, be sure that your environement (@my-chapterG1 & @my-chapterG2) are ready!
:::

::::{important} Then !
:::{contents}
:depth: 1
:::
::::

### Run a public workflow

For running a public workflow:
- Click on **Workflows** on the vertical panel on the left of **<span style="color:gold">Galaxy action list</span>**. A new window opens in the central part
- Click on **Public Workflows** 
- Search [**Argo-Glider Nitrate QCV**](#AGQCV) or [others](#public) in the **<span style="color:gold">top search bar</span>** for run the workflow of one float
- Click on the name, a pop-up window is launched. There you can preview the workflow scheme.
- You can run the public instance by clicking on the top right **run** button. However, `it is advised to have your own copy`. For that, click on the **import** button just on the left side of the run button. Your local copy is now located on **Workflows/My workflows**
- When you click on run, a first panel asks you for the input files, they correspond to the data uploaded during the @my-chapterG2 phase for the Argo files and for the climatology. Once correctly filled in, click on **run** again. 
- When the workflow arrives at the ODV interactive step for the qualification part is active: 
    - open ODV (@interactivetool)
    - apply QC (@my-chapterODV)
    - @my-section24

:::{error}
@ehome

@eview
:::

:::{warning}
ODV has a time execution limitation of 24h. If you launch a workflow and waiting more than 1 day to open ODV, the workflow will continue automatically
:::
 
- Once the qualification step is finished and history exported, close ODV, the workflow will continue automatically
- When the workflow arrives at the ODV interactive step for the validation part is active :
    - follow @my-chapter5 phase

(public)=
### Available public workflow
:::{admonition} Argo-Glider Nitrate QCV
:label: AGQCV
To perform Qualification, Nitrate Calibration, Validation of One Argo float or One Glider by using Neural Network and Climatology. Copy past before running and change calibration parametrization if necessary
:::

more workflow coming soon