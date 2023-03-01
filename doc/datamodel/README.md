# Data model

## Diagram

[![](https://mermaid.ink/svg/pako:eNqNk8FugzAMhl8lyrnlAbhN7XbqtEMn7cIlI4ZGCgkKiaaO8O5LApQSCitIIOzPv2MbtziXFHCKQR0ZKRWpMoHcdSAaSqmuyNokkS06Ek0a0ChFGXZ3YEZbJ5PEtuhDlUSwX6KZFIGTPwJUDFsP2yVcm2_OmssywKtLi04sB9HAwwN4TXfGT1I-di9LUMBdgXRJ7vcu11fVnKVR-Uq2ASqegSr9BPVSs_-gFr0xDhtU2392_at_zpo8AbPAg-Qc8kB0NsxxY9R38NDUec_X4Dj37e-KHV4utt0VHrumxsWeaYRD-05QgqCzoiZmEV2seqaBbgnrtfiBHs14hytQFWHUrWAwZlhfoIIMe0EKBTFce12Pmpq6xr1SpqXCaUF4AztMjJbnq8hxqpWBERqW-UZBCHrvdz2sfPcHBxdFIA?type=svg)](https://mermaid.live/view#pako:eNqNk8FugzAMhl8lyrnlAbhN7XbqtEMn7cIlI4ZGCgkKiaaO8O5LApQSCitIIOzPv2MbtziXFHCKQR0ZKRWpMoHcdSAaSqmuyNokkS06Ek0a0ChFGXZ3YEZbJ5PEtuhDlUSwX6KZFIGTPwJUDFsP2yVcm2_OmssywKtLi04sB9HAwwN4TXfGT1I-di9LUMBdgXRJ7vcu11fVnKVR-Uq2ASqegSr9BPVSs_-gFr0xDhtU2392_at_zpo8AbPAg-Qc8kB0NsxxY9R38NDUec_X4Dj37e-KHV4utt0VHrumxsWeaYRD-05QgqCzoiZmEV2seqaBbgnrtfiBHs14hytQFWHUrWAwZlhfoIIMe0EKBTFce12Pmpq6xr1SpqXCaUF4AztMjJbnq8hxqpWBERqW-UZBCHrvdz2sfPcHBxdFIA)

<!--
[![](https://mermaid.ink/img/pako:eNrdWG1P4zgQ_itWPoFUCm0pB_2GYJFWx96hbRHSiS9uM2mti-2s40BLw3-_sfNOXtruSifu4AN4_Mwzk_HMeJKts5AuOBMH1C2jS0X5syD4c0M1LKXakDju9-WW3FJNQ9BkQp4d_LWYTPYu-_14S_5USyrYG9VMCouTrwLUR3BswHEdHERzn4WruoJhlzG5ZwsQIbQ6gBCzvGd0znymN9dLBcBBdLgckwcl3WhhfJhuQg28EWs8xgjM6LJ5Oz45QeNfOV0m3ulVxOeCMr-OrIVSgY-Bdls4n3g4lZFaQJfhJ28fENd7oK4Dtgu0JXfMhw7UNlman1ArJpYkUOCxNUKnK6k0EZRDGFBUZy4eD_MYKCskR5FgPyIgr0yvrOQ4Iy-xWWTG1cmQ2G3i0Ez7BYldNaBcCBeKBTZDn517iSIPc4poWOsGOAdNXQyCwTLxN9GSIBCUoH6-16AWRkGAXtxIoelCo_IXjqlDqKsgDIlUhPqWRLOXipNzKX3iKuoZnZnCh2ZeuqbCJUJqYktqUVO6vbmeTTdiker1rKeCzjEkoRHj0mXLEAOzUjJarqzCyfXDye3vGdf7s6jnBraABwUvDF6LWsgUKhsWXK6YRlQpkRhWsVQunvKzg5gQDz1pHInwSMGPiClweyQ5_-Oan5V2s7tiG5S2-2RRloBNSUfnc_N4NM2nCnllr4OjPSXfmlKSavw7j1L4dWmVVksYUd_fVMw3mY2UX8rqleQQYOhqQa5102139ZZL9vgnC7CSiQ3N_19woTVQrlxExomar9ldtsM5P4XtcrJqNdWqGa1VVaP2nGlOA8L4xwOu1PuN9H2wJ03eY3v5d8wHJXB6A7ZcpRVgd4m26f1ylR6Uc6UhqcvdD-Adp24s1TzMTZrQ_RJB0d6SS_wRj79OCOKFKSlsCVWUaonz-P0e0W4gTZPGBHp0X8ratdsnuWnc_PIxt5Y5xmSiYGEOYKKNK3-WYhSZbQKw2RW3DigfwK1BNDiiDcQIGmqgxJ9aLCJpDGJc6jYb7GXtwbbdxzyYFXEe2gNTFVs6osxAcSQtgvr1VMjHvXL0mmfAKrQ1dgjrDF1Bbq3F7ZErkJ8wcMVcvusxykg7Pd_DEj2rxLbAfJ5HLVH4dGMHr6dv0_T_8uGWJ1m9sZ3WAJP_k4uri_wFVJj4hnOdBwqHOGL0M_mRCx6NfE0G_VH_rInBk4pTXSOwF1i2yRkO4CYtczq7fRqIZYXSlZGZgjkT3yGUfjY4faNrxiNOVCHkpwFbg9_ycBkPXVd5mNifp0g2b-9k8z4kWzbxVWu5gH3KfDMH9UfSTp7upvly3-S5a0ieYf-slDylMtb717Hep5D1f6SSZ3uX8qxcy01vvRT_rqegM3QiIGYWbFExb8VC27qy0HSNh4X1YZ9vITmnSBFQVf46UjP71Q0LmkJ0EFNRjCWusvAgtsZuhFHRZqj4P3SjNO1bX-HT_e2h31x2veK3jbNFi2sdSvD1IOLiNFAyAKU3iRiny2TkPPzz0M9_jXB6DgfMAeY6E8f6a94UwFSJiWGaDgZuoFGAgzF8cZmWypl41A-h59BIS_PxJhckqPTbbS4NqPhLSlxrM2SbpTPZOmtncjIYDfsXg4vReDwYX16MR8Nhz9k4k8HleX90eTW8ujz_bXR2hYD3nvNmKQb98eD8YjzAvfFweHV-NXz_B-jsRQY?type=png)](https://mermaid-js.github.io/mermaid-live-editor/view#pako:eNrdWG1P4zgQ_itWPoFUCm0pB_2GYJFWx96hbRHSiS9uM2mti-2s40BLw3-_sfNOXtruSifu4AN4_Mwzk_HMeJKts5AuOBMH1C2jS0X5syD4c0M1LKXakDju9-WW3FJNQ9BkQp4d_LWYTPYu-_14S_5USyrYG9VMCouTrwLUR3BswHEdHERzn4WruoJhlzG5ZwsQIbQ6gBCzvGd0znymN9dLBcBBdLgckwcl3WhhfJhuQg28EWs8xgjM6LJ5Oz45QeNfOV0m3ulVxOeCMr-OrIVSgY-Bdls4n3g4lZFaQJfhJ28fENd7oK4Dtgu0JXfMhw7UNlman1ArJpYkUOCxNUKnK6k0EZRDGFBUZy4eD_MYKCskR5FgPyIgr0yvrOQ4Iy-xWWTG1cmQ2G3i0Ez7BYldNaBcCBeKBTZDn517iSIPc4poWOsGOAdNXQyCwTLxN9GSIBCUoH6-16AWRkGAXtxIoelCo_IXjqlDqKsgDIlUhPqWRLOXipNzKX3iKuoZnZnCh2ZeuqbCJUJqYktqUVO6vbmeTTdiker1rKeCzjEkoRHj0mXLEAOzUjJarqzCyfXDye3vGdf7s6jnBraABwUvDF6LWsgUKhsWXK6YRlQpkRhWsVQunvKzg5gQDz1pHInwSMGPiClweyQ5_-Oan5V2s7tiG5S2-2RRloBNSUfnc_N4NM2nCnllr4OjPSXfmlKSavw7j1L4dWmVVksYUd_fVMw3mY2UX8rqleQQYOhqQa5102139ZZL9vgnC7CSiQ3N_19woTVQrlxExomar9ldtsM5P4XtcrJqNdWqGa1VVaP2nGlOA8L4xwOu1PuN9H2wJ03eY3v5d8wHJXB6A7ZcpRVgd4m26f1ylR6Uc6UhqcvdD-Adp24s1TzMTZrQ_RJB0d6SS_wRj79OCOKFKSlsCVWUaonz-P0e0W4gTZPGBHp0X8ratdsnuWnc_PIxt5Y5xmSiYGEOYKKNK3-WYhSZbQKw2RW3DigfwK1BNDiiDcQIGmqgxJ9aLCJpDGJc6jYb7GXtwbbdxzyYFXEe2gNTFVs6osxAcSQtgvr1VMjHvXL0mmfAKrQ1dgjrDF1Bbq3F7ZErkJ8wcMVcvusxykg7Pd_DEj2rxLbAfJ5HLVH4dGMHr6dv0_T_8uGWJ1m9sZ3WAJP_k4uri_wFVJj4hnOdBwqHOGL0M_mRCx6NfE0G_VH_rInBk4pTXSOwF1i2yRkO4CYtczq7fRqIZYXSlZGZgjkT3yGUfjY4faNrxiNOVCHkpwFbg9_ycBkPXVd5mNifp0g2b-9k8z4kWzbxVWu5gH3KfDMH9UfSTp7upvly3-S5a0ieYf-slDylMtb717Hep5D1f6SSZ3uX8qxcy01vvRT_rqegM3QiIGYWbFExb8VC27qy0HSNh4X1YZ9vITmnSBFQVf46UjP71Q0LmkJ0EFNRjCWusvAgtsZuhFHRZqj4P3SjNO1bX-HT_e2h31x2veK3jbNFi2sdSvD1IOLiNFAyAKU3iRiny2TkPPzz0M9_jXB6DgfMAeY6E8f6a94UwFSJiWGaDgZuoFGAgzF8cZmWypl41A-h59BIS_PxJhckqPTbbS4NqPhLSlxrM2SbpTPZOmtncjIYDfsXg4vReDwYX16MR8Nhz9k4k8HleX90eTW8ujz_bXR2hYD3nvNmKQb98eD8YjzAvfFweHV-NXz_B-jsRQY)
-->

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

