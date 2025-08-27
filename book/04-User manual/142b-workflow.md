---
title: From a pre-designed workflow
date : 2025-08-25
label: workflow
---

:::{important} Before starting
Before running your or a public workflow, be sure that your environement ([prerequisite and data management](#galaxyUserManual1)) are ready!
:::

### Run a public workflow

For running a public workflow:
- Click on **Workflows** on the vertical panel on the left of **<span style="color:gold">Galaxy action list</span>**. A new window opens in the central part
- Click on **Public Workflows** 
- Search [**Argo-Glider Nitrate QCV**](#AGQCV) or [others](#public) in the **<span style="color:gold">top search bar</span>** for run the workflow of one float
- Click on the name, a pop-up window is launched. There you can preview the workflow scheme.
- You can run the public instance by clicking on the top right **run** button. However, `it is advised to have your own copy`. For that, click on the **import** button just on the left side of the run button. Your local copy is now located on **Workflows/My workflows**
- When you click on run, a first panel asks you for the input files, they correspond to the data uploaded during the [environement preparation](#galaxyUserManual1) for the Argo files and step d.6 for the climatology. Once correctly filled in, click on **run** again. 
- When the workflow arrives at the ODV interactive step for the qualification part is active: 
    - open ODV ([further instructions](#interactivetool))
    - apply QC (REF)
    - perform steps d.4 to export ODV history.

Remarque 1 : la vue ODV ne s’est pas lancée automatiquement, il a fallu la recharger … Vu avec Marie: problème dans le chargement d’un dossier contenant autre chose que des xview. Marie  va corriger.

Remarque 2: j’avais laissé l’étape interactive ODV du “Qualify your data” en suspe  ns avant de partir en weekend. Au bout de 24h (timeout ?), le workflow est automatiquement passé à la suite.
 
l’étape de calibration a renvoyé 0 fichiers, et le workflow s’est terminé en erreur à l’étape interactive de la validation.

A few performance indicators:
Step 1 and 2: no time (input data)
Step 3: 3’ for 8’’ of CPU usage time
Step 4: 5’25’’ for 17’’ of CPU usage time
Step 5: 3’45’’ for 11’’ of CPU usage time
Step 6: 1h47’5’’ (includes interactive time) for 47’’ of CPU usage time
Step 7: xx’xx’’ for xx’’ of CPU usage time: It was a long history file (I tried back and forth the QC of a whole profile): the length of step 7 execution may be due to this (?).

(public)=
#### available public workflow
:::{admonition} Argo-Glider Nitrate QCV
:label: AGQCV
To perform Qualification, Nitrate Calibration, Validation of One Argo float or One Glider by using Neural Network and Climatology. Copy past before running and change calibration parametrization if necessary
:::

more workflow coming soon