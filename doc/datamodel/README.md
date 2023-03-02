# Data model

## Diagram

[![](https://mermaid.ink/svg/pako:eNqNk8FugzAMhl8lyrnlAbhN7XbqtEMn7cIlI4ZGCgkKiaaO8O5LApQSCitIIOzPv2MbtziXFHCKQR0ZKRWpMoHcdSAaSqmuyNokkS06Ek0a0ChFGXZ3YEZbJ5PEtuhDlUSwX6KZFIGTPwJUDFsP2yVcm2_OmssywKtLi04sB9HAwwN4TXfGT1I-di9LUMBdgXRJ7vcu11fVnKVR-Uq2ASqegSr9BPVSs_-gFr0xDhtU2392_at_zpo8AbPAg-Qc8kB0NsxxY9R38NDUec_X4Dj37e-KHV4utt0VHrumxsWeaYRD-05QgqCzoiZmEV2seqaBbgnrtfiBHs14hytQFWHUrWAwZlhfoIIMe0EKBTFce12Pmpq6xr1SpqXCaUF4AztMjJbnq8hxqpWBERqW-UZBCHrvdz2sfPcHBxdFIA?type=svg)](https://mermaid.live/view#pako:eNqNk8FugzAMhl8lyrnlAbhN7XbqtEMn7cIlI4ZGCgkKiaaO8O5LApQSCitIIOzPv2MbtziXFHCKQR0ZKRWpMoHcdSAaSqmuyNokkS06Ek0a0ChFGXZ3YEZbJ5PEtuhDlUSwX6KZFIGTPwJUDFsP2yVcm2_OmssywKtLi04sB9HAwwN4TXfGT1I-di9LUMBdgXRJ7vcu11fVnKVR-Uq2ASqegSr9BPVSs_-gFr0xDhtU2392_at_zpo8AbPAg-Qc8kB0NsxxY9R38NDUec_X4Dj37e-KHV4utt0VHrumxsWeaYRD-05QgqCzoiZmEV2seqaBbgnrtfiBHs14hytQFWHUrWAwZlhfoIIMe0EKBTFce12Pmpq6xr1SpqXCaUF4AztMjJbnq8hxqpWBERqW-UZBCHrvdz2sfPcHBxdFIA)

## Common rules / types

Primary keys are named Id and of UUID type unless otherwise stated.

For strings we always require min 2 chars. For max length we have three categories:

* name - max 256
* shortdesc - max 1024
* desc - max 4096

We also have url as type to constrain content to valid URL.

All entities have Updated and Created attributes intended to be automatically maintained by persistence layer.

## Entities

### Dataset

A Dataset represents almost any kind of data. Can be related to other Datasets as a form of metadata.

| Name           | Type      | Nullable | Business rules                                                                                               |
|----------------|-----------|----------|--------------------------------------------------------------------------------------------------------------|
| Id             | name      | No       | URN. urn:dmp:ds:name_of_dataset name can only me lower-case letters, digits and '-'. Maximum 128 characters. |
| Uid            | guid      | No       |                                                                                                              |
| Title          | shortdesc | No       |                                                                                                              |
| Description    | desc      | Yes      |                                                                                                              |
| SupportContact | name      | Yes      | Valid email                                                                                                  |
| Metadata       | url       | Yes      |                                                                                                              |
| Draft          | bit       | no       |                                                                                                              |
| DCATSync       | bit       | no       |

### Organisation

Can be related to datasets as publisher or owners. Publisher is the organisation who houses the data, owners are the organisations that have copyright on the data.

| Name         | Type      | Nullable | Business rules |
|--------------|-----------|----------|----------------|
| Title        | shortdesc | No       |                |
| Abbreviation | name      | No       |                |
| Attribution  | name      | No       |                |
| Url          | url       | Yes      |                |
| Description  | desc      | Yes      |                |

### ProductionSystem

DMP interal system name.

| Name        | Type | Nullable | Business rules |
|-------------|------|----------|----------------|
| Name        | name | No       |                |
| Description | desc | Yes      |                |

### License

| Name | Type | Nullable | Business rules |
|------|------|----------|----------------|
| Name | name | No       |                |
| Url  | url  | Yes      |                |

### DataLiabilityAgreement

DMP interal document.

| Name | Type | Nullable | Business rules |
|------|------|----------|----------------|
| Name | name | No       |                |
| Url  | url  | Yes      |                |

### DatasetCollection

Represents a named collection of Datasets.

| Name        | Type      | Nullable | Business rules |
|-------------|-----------|----------|----------------|
| Title       | shortdesc | No       |                |
| Description | desc      | Yes      |                |

### Category

Simple free text string category relating to a set of Datasets.

| Name | Type | Nullable | Business rules |
|------|------|----------|----------------|
| Name | name | No       |                |

### Tag

Simple free text string tags.

| Name | Type | Nullable | Business rules |
|------|------|----------|----------------|
| Name | name | No       |                |

### FileSource

General purpose file based data source metadata.

| Name             | Type | Nullable | Business rules |
|------------------|------|----------|----------------|
| Url              | url  | No       |                |
| DocumentationUrl | url  | Yes      |                |
| Description      | desc | Yes      |                |

### FileSourceType

| Name | Type | Nullable | Business rules |
|------|------|----------|----------------|
| Name | name | No       |                |

### ApiSource

Non spatial general purpose API data source metadata.

| Name             | Type | Nullable | Business rules |
|------------------|------|----------|----------------|
| Url              | url  | No       |                |
| DocumentationUrl | url  | Yes      |                |
| Description      | desc | Yes      |                |

### Image

User provided images. Intended for use as thumbnail for Dataset and DatasetCollection or Legends.

| Name | Type | Nullable | Business rules |
|------|------|----------|----------------|
| Url  | url  | No       |                |

### (Wms/Wfs/Wmts)Source

Spatial data source/service metadata.

| Name             | Type  | Nullable | Business rules                                                                           |
|------------------|-------|----------|------------------------------------------------------------------------------------------|
| Url              | url   | No       |                                                                                          |
| DocumentationUrl | url   | Yes      |                                                                                          |
| Description      | desc  | Yes      |                                                                                          |
| TypeName         | name  | No       |                                                                                          |
| Layer            | name  | No       |                                                                                          |
| Style            | name  | No       |                                                                                          |
| Extent           | name  | No       | Comma separated float values xmin,ymin,xmax,ymax to determine tilegrid origin and extent |
| MatrixSet        | name  | No       | Reference to the name of WMTS MatrixSet tilegrid                                         |
| MatrixIds        | name  | No       | Comma separated strings of identifiers in WMTS TileMatrixSet                             |
| Resolutions      | name  | No       | Comma separated float values in m/pixel corresponding to the zoom levels in a tilegrid   |
| Version          | name  | No       |                                                                                          |
| Format           | name  | No       |                                                                                          |
| MinResolution    | float | Yes      |                                                                                          |
| MaxResolution    | float | Yes      |                                                                                          |

NOTE: Some attributes are only relevant for some of the source types in this section name.

### Attribute

Spatial sources might not have desired metadata or naming for attributes/columns to be useful in presentation. The Attribute entity is intended to be able to provide such optional source specific metadata.

| Name  | Type      | Nullable | Business rules |
|-------|-----------|----------|----------------|
| Name  | name      | No       |                |
| Title | shortdesc | No       |                |
| Order | int       | No       |                |

