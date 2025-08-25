---
title: How to run Easy Q.C.V BGC on Galaxy
date : 2025-08-20
label: galaxyUserManual1
---

The next sections explain how to qualify and calibrate the nitrate sensor mounted on the argo float 4903881 tool by tool or running a pre-design galaxy workflow. For your information, execution time for running tools depends on the number of files, their size and/or the number of people working on Galaxy.

:::{warning}
DO NOT change file names to ensure that any changes you make with ODV will be carried over. However, it is possible to change the name of <span style="color:green">galaxy collections</span> to make them easier to find.
:::

### Prerequisites

:::{admonition} Galaxy account
:class: dropdown
Create or Login to your [Galaxy europe account](https://earth-system.usegalaxy.eu/login/start)
:::

:::{admonition} Galaxy tips and tricks
:class: dropdown
Once you are login, Galaxy is divided into 4 vertical panels whose : 
- the far left : `Galaxy action list` with “interactive Tools”, “Upload”, “Tools” …
- the far right : `History section`.

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
    - Click on the symbol “+” on the top-right in the history section 
    - Click on the pencil aligned to “Unnamed history”
    - Give an explicit name, annotation (optional), tag (optional)
    - Save
- Switching from one history to another one
    - Click on the symbole “ ⇄” on the top-right in the history section
    - Select the history in the pop-up
- Copy/paste dataset from one history to another one
    - Click on {Operations} - See figure below
    - Select “Copier des jeux de données” in the pop-up
    - In the central panel left to history section, select the file(s) you want to copy from the “source” history (left) to the destination history (right)


```{image}  ../../embedded-ressources/figures/S141a_operations.png
:alt: figb
:width: 500px
:align: center
```
:::

### Manage your data

:::{admonition} Get data from the S3 server
:class: dropdown
For uploading the argo data files (meta, core and BGC) of the float 4903881 from the S3 service: 
- (a) Click on “Upload” on the “Galaxy action list” vertical panel on the left. A pop-up is launched
- (b) Click on “Choose from repository” at the bottom of the popup

:::

:::{admonition} Get data from your computer
:class: dropdown

:::

:::{admonition} Organize your data
:class: dropdown

:::