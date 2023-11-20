# FOSS4G2023Workshop_How-to-implement-OGC-API
FOSS4G 2023 Seoul Half-day workshop >  OGC API – MF, an introduction with MF-API Server based on pygeoapi and MobilityDB > How to implement OGC API – MF with pygeoapi and MobilityDB?
Each section describes the commands and sample data used.

### Recommended PC specifications
- [x] HDD：At least 20GB free space
- [x] memory >= 6GB

### <5 mins> A brief explanation of pygeoapi (overall architecture, etc.) and install MF-API Server (using Docker)
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
### <10 mins> A brief explanation of MobilityDB and the functions (and structure) used to handle temporal geometry and properties.
> [!NOTE] 
> * There are no commands or data to use.

### <20 mins> Describe how you extended pygeoapi to support OGC API – MF (libraries to use OpenAPI and MobilityDB (pyMEOS, python-mobilitydb, etc.) and extension structure, etc.)
> [!NOTE] 
> * There are no commands or data to use.

### <30 mins> Verify that each API works properly using Swagger


