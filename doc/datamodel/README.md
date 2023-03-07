# Data model

## Diagram

[![](https://mermaid.ink/svg/pako:eNqNk8FugzAMhl8lyrnlAbhN7XbqtEMn7cIlI4ZGCgkKiaaO8O5LApQSCitIIOzPv2MbtziXFHCKQR0ZKRWpMoHcdSAaSqmuyNokkS06Ek0a0ChFGXZ3YEZbJ5PEtuhDlUSwX6KZFIGTPwJUDFsP2yVcm2_OmssywKtLi04sB9HAwwN4TXfGT1I-di9LUMBdgXRJ7vcu11fVnKVR-Uq2ASqegSr9BPVSs_-gFr0xDhtU2392_at_zpo8AbPAg-Qc8kB0NsxxY9R38NDUec_X4Dj37e-KHV4utt0VHrumxsWeaYRD-05QgqCzoiZmEV2seqaBbgnrtfiBHs14hytQFWHUrWAwZlhfoIIMe0EKBTFce12Pmpq6xr1SpqXCaUF4AztMjJbnq8hxqpWBERqW-UZBCHrvdz2sfPcHBxdFIA?type=svg)](https://mermaid.live/view#pako:eNqNk8FugzAMhl8lyrnlAbhN7XbqtEMn7cIlI4ZGCgkKiaaO8O5LApQSCitIIOzPv2MbtziXFHCKQR0ZKRWpMoHcdSAaSqmuyNokkS06Ek0a0ChFGXZ3YEZbJ5PEtuhDlUSwX6KZFIGTPwJUDFsP2yVcm2_OmssywKtLi04sB9HAwwN4TXfGT1I-di9LUMBdgXRJ7vcu11fVnKVR-Uq2ASqegSr9BPVSs_-gFr0xDhtU2392_at_zpo8AbPAg-Qc8kB0NsxxY9R38NDUec_X4Dj37e-KHV4utt0VHrumxsWeaYRD-05QgqCzoiZmEV2seqaBbgnrtfiBHs14hytQFWHUrWAwZlhfoIIMe0EKBTFce12Pmpq6xr1SpqXCaUF4AztMjJbnq8hxqpWBERqW-UZBCHrvdz2sfPcHBxdFIA)

## Entities

### Dataset

A Dataset represents almost any kind of data. Can be related to other Datasets as a form of metadata. Primarily the databaes contains data related to environment and is spatial data. The dataset entity contains Title, description attributes. 


### Organisation

Can be related to datasets as publisher or owners. Publisher is the organisation who houses the data, owners are the organisations that have copyright on the data. The organisation entity contains Title, Abbreviation and Description attributes.

### ProductionSystem

DMP interal system name. The entity contains name and description.

### License

License contains information about the the dataset in question is licensed by the owners of the dataset, the entity contains a name and a link to the license.

### DataLiabilityAgreement

DMP interal document.

### DatasetCollection

Represents a named collection of Datasets. A collection of datasets are datasets that are somehow related or datasets that should be seen together. There is a many-to-many relationship with the Datasets entity. The DatasetCollection contains Title and Description of the collection. 

### Category

Simple free text string category relating to a set of Datasets.

### Tag

Simple free text string tags.

### Image

User provided images. Intended for use as thumbnail for Dataset and DatasetCollection or Legends. There is a link to the Bitmap image. 

### (File/Api/Wms/Wfs/Wmts)Source

Dataset source/service metadata.

NOTE: Some attributes are only relevant for some of the source types in this section name.

| Name             | Type  | Nullable | Comment                                                                                  |
| ---------------- | ----- | -------- | ---------------------------------------------------------------------------------------- |
| Url              | url   | No       | URL endpoint                                                                             |
| DocumentationUrl | url   | Yes      | URL documentation endpoint                                                               |
| Description      | desc  | Yes      | Long free text abstract (optional)                                                       |
| TypeName         | name  | No       | WFS TypeName                                                                             |
| Layer            | name  | No       | WMS/WMTS layer name                                                                      |
| Style            | name  | No       | WMS style name (optional)                                                                |
| Extent           | name  | No       | Comma separated float values xmin,ymin,xmax,ymax to determine tilegrid origin and extent |
| MatrixSet        | name  | No       | Reference to the name of WMTS MatrixSet tilegrid                                         |
| MatrixIds        | name  | No       | Comma separated strings of identifiers in WMTS TileMatrixSet                             |
| Resolutions      | name  | No       | Comma separated float values in m/pixel corresponding to the zoom levels in a tilegrid   |
| Version          | name  | No       | Preferred WMS version (default 1.3.0)                                                    |
| Format           | name  | No       | Preferred WMS image format mimetype (default image/png)                                  |
| MinResolution    | float | Yes      | Maximum resolution m/pixel (optional)                                                    |
| MaxResolution    | float | Yes      | Minimum resolution m/pixel (optional)                                                    |

### Attribute

The attribute entity is used in the attribution component and is a short description of which organisation is attributed the dataset, often it is the owner of the dataset. Spatial sources might not have desired metadata or naming for attributes/columns to be useful in presentation. The Attribute entity is intended to be able to provide such optional source specific metadata.

## Common rules / types

Primary keys are named Id and of UUID type unless otherwise stated.

For strings we always require min 2 chars. For max length we have three categories:

- name - max 256
- shortdesc - max 1024
- desc - max 4096

We also have url as type to constrain content to valid URL.

All entities have Updated and Created attributes intended to be automatically maintained by persistence layer.

