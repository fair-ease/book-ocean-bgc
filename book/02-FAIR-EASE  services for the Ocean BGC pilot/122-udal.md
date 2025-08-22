---
title: Unified Data Access Layer (UDAL)
date: 2025-08-20
label: udal
---

As recommended by the FAIR-EASE technical team for the data access layer, the easy Q.C.V BGC has used the proposed UDAL service. The core of the UDAL implementation has been developed and proposed by Marc Portier {sup}`[![alt text](../../embedded-ressources/logo/orcid.png)](https://orcid.org/0000-0002-9648-6484)` and Jorge Mendes. Specific implementations for new data sources and the integration layer with the easy Q.C.V BGC have been developed by the POKaPOK team. 
UDAL aims to simplify data access to data consumers by abstracting the way of querying datasets. It is similar to a catalog of data with its own language. This language and its associated simplified and harmonized query language is common to all datasets. This allows the users to discover and get data without knowing the specificities of the accesses to the various datasets. The data access and querying schemes have to be written by each data provider, which knows the access specificity of its own dataset. Also, UDAL is able to manage cache, data storage and avoid duplication of data. 

```{figure}  ../../embedded-ressources/figures/S122_udalWF.png
:label: udalWorkFlow
:width: 900px
:align: center
UDAL is to support different broker implementations. Figure extracted from [D4.3 Status and expectations of the FAIR-EASE data lake](https://zenodo.org/records/13933551)
```

The easy Q.C.V BGC uses UDAL both as a data broker and a download manager.


### UDAL Download Manager 
The download manager of UDAL does the data download action. It has been modified to integrate the notion of file size to ensure the full download of data. Before downloading, it first checks if the file already exists in the cache repository. If it exists, it checks if the file to download has the same size as the file found on the cache repository. If the sizes are matching, it considers the file is already fully downloaded and skip the download part. If not, it considers the previous download may have failed and downloads the file again. If the file does not exist in the cache repository, it downloads it. 
Also, the download manager can be used as a timestamp fetcher : it gets the last modification date on queried remote data and returns it.
Within the easy Q.C.V BGC, the UDAL Download manager has been modified to download data only if the remote timestamp has changed or if the download is suspected to have been corrupted.


### UDAL Cache Manager
Within the easy Q.C.V BGC, the cache manager has also been modified to bypass the file storage management by the UDAL. This bypass is performed by setting the key “bypass_arch_folder” in the configuration file. 


### UDAL Data Broker
In order to get the data, the easy Q.C.V BGC uses the UDAL as a data broker. It transforms a simple query (in a way proposed by the data provider) into a real download request on the server. 
During FAIR-EASE, contrary to the wanted philosophy of the UDAL, where the data providers are responsible for the exposition of their asset and the associated query, queries were written by the data experts from the project use cases (including the Ocean BGC use case). 
For the easy Q.C.V BGC, UDAL is now able to get data access to Argo floats, Gliders, World Ocean Atlas (WOA) and Copernicus datastore (still under development - untested) from original repositories (API, http). Each type of data has its own vocabulary and query philosophy and are corresponding to the needs of each data source and type.
Stemming from the easy Q.C.V BGC needs, credential management was also added, as it was necessary to fetch data on copernicus marine datastore. This part is not fully functional but it works as a proof of concept to address UDAL in future developments including Copernicus data. 

### UDAL Queries
Each data source has its own vocabulary and query detailed in the next sections for Argo, Glider, World Ocean Atlas (WOA) and Copernicus Marine Service.

In the easy Q.C.V BGC, only URNs ending with ‘files’ (urn:pokapok:udal:XXX:files) have been used. The processing of files is performed by the easy Q.C.V BGC as it needs to keep original data.
 
The specific implementation of UDAL developed by the POKaPOK team for the needs of the easy Q.C.V BGC can be found  on the [POKaPOK docker hub account](https://gitlab.com/pokapok-projects/easy-qcv-bgc/libraries/py-udal-pokapok)


#### Argo queries
1. 'urn:pokapok:udal:argo:meta' - `return argo meta parameters file`
    - Args : ['float_type']
2. 'urn:pokapok:udal:argo:data' - `return argo float dataset (xarray)`; all cycles concatenated
    - Args : ['dac', 'float_mode', 'float_type', 'float', 'descending_cycles']
3. 'urn:pokapok:udal:argo:files' - `return argo files` (data and meta)
    - Args : ['dac', 'float_mode', 'float_type', 'float', 'descending_cycles', 'incl_meta', 'bypass_out_arch_building']


#### Glider queries
1. 'urn:pokapok:udal:glider:files - `return glider files` 
    - Args : ['name', 'deployment_date', 'descending_cycles', 'bypass_out_arch_building']


#### WOA queries
1. 'urn:pokapok:udal:woa23 - `return WOA 2023 dataset (xarray)` 
    - Args : ['decade', 'grid', 'time_res', 'variable']
2. 'urn:pokapok:udal:woa23:files - `return WOA 2023 files` 
    - Args : ['decade', 'grid', 'time_res', 'variable', 'lon_min', 'lon_max', 'lat_min', 'lat_max']


#### Copernicus Marine Service queries
(still under development)
1. 'urn:pokapok:udal:copernicus:files - `return Copernicus files` 
    - Args : ['dataset_id', 'variables', 'minimum_longitude', 'maximum_longitude', 'minimum_latitude', 'maximum_latitude',  'start_datetime', 'end_datetime', 'minimum_depth', 'maximum_depth', 'output_filename', 'overwrite', 'netcdf_compression_level', 'bypass_out_arch_building', 'lon_min', 'lon_max', 'lat_min', 'lat_max']

#### Example of usage
To run the UDAL, [clone the POKaPOK git](https://gitlab.com/pokapok-projects/easy-qcv-bgc/libraries/py-udal-pokapok) and follow the instructions of installation on the readme. Below, there is an example of usage with python (only language available for now) to download and store Gliders files.

```{code-block} python
---
lineno-start: 1
caption: |
    Glider files example
---
from pokapok.udal import UDAL, Config
from pokapok.glider.types import *


query_args = {
   'name': 'sea019',
   'deployment_date': '20180724',
   'descending_cycles': True,
   'url': 'https://co.ifremer.fr/co/ego/ego/v2/',
   'bypass_out_arch_building': True
   }


config = Config(cache_dir='.')
glider = UDAL(query_args["url"], config=config)


result = glider.execute('urn:pokapok:udal:glider:files', query_args)
result.data()
```