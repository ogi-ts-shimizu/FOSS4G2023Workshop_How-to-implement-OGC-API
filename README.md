# FOSS4G2023Workshop_How-to-implement-OGC-API
FOSS4G 2023 Seoul Half-day workshop >  OGC API – MF, an introduction with MF-API Server based on pygeoapi and MobilityDB > How to implement OGC API – MF with pygeoapi and MobilityDB?
Each section describes the commands and sample data used.

## Recommended PC specifications
- [x] HDD：At least 20GB free space
- [x] memory >= 6GB
- [x] Install Docker on local PC (https://www.docker.com/get-started)

---
## <5 mins> A brief explanation of pygeoapi (overall architecture, etc.) and install MF-API Server (using Docker)
Execute the following three commands in order at the command prompt

Step1
```bash
docker pull ghcr.io/taehoonk/mf-api-server:1.0
```

Step2
```bash
docker run -p 8085:8085 -p 25432:5432 -d --name mf-api-server ghcr.io/taehoonk/mf-api-server:1.0
```

Step3
```bash
docker exec mf-api-server ./run.sh
```
---
## <10 mins> A brief explanation of MobilityDB and the functions (and structure) used to handle temporal geometry and properties.
> [!NOTE] 
> * There are no commands or data to use.
---

## <20 mins> Describe how you extended pygeoapi to support OGC API – MF (libraries to use OpenAPI and MobilityDB (pyMEOS, python-mobilitydb, etc.) and extension structure, etc.)
> [!NOTE] 
> * There are no commands or data to use.
---
## <30 mins> Verify that each API works properly using Swagger
## Moving Feature Collection
#### **[POST]** Moving Feature Collection

Request body(application/json)
```json
{
  "title": "moving_feature_collection_sample1",
  "updateFrequency": 1000,
  "description": "FOSS4G2023 Seoul Workshop"
}
```
---
#### **[GET]** Moving Feature Collection
collectionID
> [!NOTE] 
> * The last part of `location` link when POST response
![image](https://github.com/ogi-ts-shimizu/FOSS4G2023Workshop_How-to-implement-OGC-API/assets/120169253/934a7555-a796-4289-a7bf-a18d4c962204)
---
#### **[PUT]** Moving Feature Collection
collectionID : The last part of `location` link when POST response

Request body(application/json)
```json
{
  "title": "moving_feature_collection_sample2",
  "updateFrequency": 1000,
  "description": "FOSS4G2023 Seoul Workshop PUT test"
}
```
---
#### **[DELETE]** Moving Feature Collection
> [!NOTE] 
> Skip the DELETE request for the next demonstration

---
## Moving Feature
#### **[POST]** Moving Features
collectionID : ID of the response at the time of **Moving Feature Collection**

Request body(application/json) : **Default Value**

---
#### **[GET]** Moving Features (/collections/{collectionId}/items)
collectionID : ID of the response at the time of **Moving Feature Collection**

datetime : Empty

limit : 10

---

#### **[GET]** Moving Features (/collections/{collectionId}/items/{mFeatureId})
collectionId : ID of the response at the time of **Moving Feature Collection**
mFeatureId
> [!NOTE]
> The last part of `location` link when Moving Features POST response
![image](https://github.com/ogi-ts-shimizu/FOSS4G2023Workshop_How-to-implement-OGC-API/assets/120169253/c609d523-6f45-40b8-aec1-9b6903a8797f)
---
#### **[DELETE]** Moving Features (/collections/{collectionId}/items/{mFeatureId})
> [!NOTE] 
> Skip the DELETE request for the next demonstration
---
## TemporalGeometryCollection
#### **[POST]** Temporal Geometry(/collections/{collectionId}/items/{mFeatureId}/tGeometries)
collectionId : ID of the response at the time of **Moving Feature Collection**

mFeatureId : ID of the response at the time of **Moving Features**

Request body(application/json) : **Default Value**

---
#### **[GET]** Temporal Geometry(/collections/{collectionId}/items/{mFeatureId}/tGeometries)
collectionId : ID of the response at the time of **Moving Feature Collection**

mFeatureId : ID of the response at the time of **Moving Features**

leaf : Empty

bbox : Empty

datetime : Empty

limit : 10

---
#### **[DELETE]** Temporal Geometry(/collections/{collectionId}/items/{mFeatureId}/tGeometries/{tGeometryId})
collectionId : ID of the response at the time of **Moving Feature Collection**

mFeatureId : ID of the response at the time of **Moving Features**

tGeometryId :
> [!NOTE] 
> * The last part of `location` link when POST response
![image](https://github.com/ogi-ts-shimizu/FOSS4G2023Workshop_How-to-implement-OGC-API/assets/120169253/d394eedd-efbe-4c97-845a-e5e909d4dd4b)


---
## TemporalPropertyCollection
#### **[POST]** Temporal Property (/collections/{collectionId}/items/{mFeatureId}/tProperties)
collectionId : ID of the response at the time of **Moving Feature Collection**

mFeatureId : ID of the response at the time of **Moving Features**

Request body(application/json) : **Default Value**

---
#### **[POST]** Temporal Property (/collections/{collectionId}/items/{mFeatureId}/tProperties/{tPropertyName})
collectionId : ID of the response at the time of **Moving Feature Collection**

mFeatureId : ID of the response at the time of **Moving Features**

tPropertyName
> [!NOTE] 
> * The last part of `location` link when POST response

Request body(application/json) : **Default Value**

---
#### **[GET]** Temporal Property (/collections/{collectionId}/items/{mFeatureId}/tProperties/{tPropertyName})
collectionId : ID of the response at the time of **Moving Feature Collection**

mFeatureId : ID of the response at the time of **Moving Features**

tPropertyName : ID of the response at the time of **Temporal Property**

leaf : Empty

datetime : Empty

limit : 10

---
#### **[DELETE]** Temporal Property(/collections/{collectionId}/items/{mFeatureId}/tProperties/{tPropertyName})
collectionId : ID of the response at the time of **Moving Feature Collection**

mFeatureId : ID of the response at the time of **Moving Features**

tPropertyName : ID of the response at the time of **Temporal Property**

---

## References
MF-API Server based on pygeoapi
 https://github.com/aistairc/mf-api

OGC API – Moving Features official GitHub repository
 https://github.com/opengeospatial/ogcapi-movingfeatures

MobilityDB (and its Python driver, PyMEOS, and MEOS)
https://github.com/MobilityDB

STINUUM（The installation of each program will use a Docker file.）
https://github.com/aistairc/mf-cesium

OGC API – MF helpful information
 https://ogcapi.ogc.org/movingfeatures/
