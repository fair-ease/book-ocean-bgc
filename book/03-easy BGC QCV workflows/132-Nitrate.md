---
title: Nitrate
date: 2025-08-20
label: nitratepage
---

The Nitrate calibration methodology follows the Argo reference documentation [BGC-Argo quality control manual for nitrate concentration](https://doi.org/10.13155/84370) and recommendation from Euro-Argo RISE project  [D4.5: Recommendations for enhancement of NO3 QC Methods](https://zenodo.org/records/7369098⁠).

Briefly, this consists of 4 main steps: 
:::{contents}
:depth: 3
:::


### Step 1: Selection of the equation for the adjustment computation

Two sets of equation(s) are possible:

:::{admonition} Method 1: OFFSET and DRIFT
:label:Nitrate1
The method calculates at depth (at the reference pressure *Pref*, where there should be the minimum of the variability) the difference between the measurements and reference data and fits this difference as a linear function of time. When needed, the linear function can be estimated by segments of time. The same correction estimated at *Pref* is used along the whole vertical profile.

```{math}
nitrate\_adjusted_{(c,P)} = nitrate_{raw(c,P)} - correction_{(c,Pref)}
```
```{math}
correction_{(c,Pref)} = offset_{(i,Pref)}  + drift_{(i,Pref)}*(time_c -time_i)/365
```

Where : 
- ***offset*** (in µmol/kg) and ***drift*** (in µmol/kg/year) are respectively the intercept and the slope of the linear regression of {math}`nitrate_{raw_(P=Pref)} - nitrate_{ref(P=Pref)}` as a function of ***time*** expressed in julian day.
- ***c*** corresponds to the cycle vertical profile (in Argo, the vertical profile is performed once every 10 days for the usual mission configuration)
- ***i*** corresponds to the time segment number if necessary - i.e. if the slope value changes by part during the lifetime of the sensor.	
- ***Pref*** is set equal correspond to the referenced pressure
- ***time{sub}`i`*** corresponds to the time (in julian day) when the segment i starts. 

:::

:::{admonition} Method 2: OFFSET, DRIFT and GAIN
<!-- :class: dropdown  -->

> [!WARNING]
> implementation in progress

The second method applies a corrective gain to method 1 to account for a potential pressure effect on the sensor. This effect can be highlighted by strong negative values of the nitrate concentration at the surface at some locations (e.g., in the Pacific Ocean) while this nitrate concentration is correctly adjusted at depth. Several criteria must be accounted for to choose the application of a gain rather than the first method solely:
known oligotrophic region
reference nitrate suggests value is zero (from Glodap close-by cross-overs or from shipboard data)
values are constantly biased
flat lines

**to be completed**
:::

### Step 2: Selection of the method to assess the reference value of Nitrate
Several methodologies are available to assess *nitrate{sub}`ref`*. They all have their specificities, pros and cons.  The B.G.C QCV proposed the methodologies recommended by the Euro-Argo RISE [D4.5: Recommendations for enhancement of NO3 QC Methods](https://zenodo.org/records/7369098)⁠ :
- Neural network prediction system
  * CANYON-B 
  * CANYON-MED (Mediterranean Sea)
- Gridded climatologies
  * World Ocean Atlas monthly climatology
  * World Ocean Atlas decadal climatology

### Step 3: Selection of the methodologies for evaluating referenced pressure P
Two options are possible:
- From nitrate measured by the platform (minimum variability zone)
- From the operator

Diagnostic figures are made by the tool for explaining its choice.

:::::{admonition} Diagnostic figure examples!
:class: dropdown
::::{tab-set}
  :::{tab-item} From nitrate measured by platform
  ```{figure}  ../../embedded-ressources/figures/S132b_6990636_harm_C4-nitrateZvar_ref_results.png
  :label: toolPref_results
  :width: 900px
  :align: center
  Z reference for the nitrate calibration estimated by the tool (red)
  ```
  :::

  :::{tab-item} From operator
  ```{figure}  ../../embedded-ressources/figures/S132a_4903881_harm_C1-nitrateZvar_ref_results.png
  :label: userPref_results
  :width: 900px
  :align: center
  User Z reference (green) for  the nitrate calibration agains tool evaluation (red)
  ```
  :::
::::
:::::

### Step 4: Definition of the number of linear regression / segment in time 
This option defines the number ***offset*** + ***drift*** that should be used for estimating the adjustment.
Three options are possible : 
- Automatically defined by the tool
- defined by the user
- favors one linear regression

Diagnostic figures are made by the tool for explaining its choice.
::::{admonition} Diagnostic figure examples!
:class: dropdown
```{figure}  ../../embedded-ressources/figures/S132c_3902124_harm_qced_C1-nitrateRaw-Ref_Analysis_ref#01_LinearModel.png
:label: LinearReg
:width: 900px
:align: center
Single and Multiple Linear Regression defined by the tool
```
::::