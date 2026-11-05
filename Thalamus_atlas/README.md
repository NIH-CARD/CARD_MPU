# Thalamus Atlas: Analysis Hub

Landing repository for the downstream analyses of the multi-cohort thalamus single-nucleus RNA-seq atlas (Alzheimer's disease and frontotemporal dementia). Each analysis lives in its own repository, linked here as a Git submodule, so methods stay independent and can be versioned and run separately.

## Start here

| I want to... | Go to | Tools |
|---|---|---|
| Test whether cell-type abundance differs by disease | [`Differential_cell_type_proportion`](https://github.com/ambertrujillo/Thalamus_atlas_differential_cell_type_proportion.git) | Propeller |
| Find disease-associated genes within each cell type | [`Pseudobulked_differential_gene_expression`](https://github.com/ambertrujillo/Thalamus_atlas_differential_gene_expression.git) | RUVSeq, DESeq2 |
| Compare ligand-receptor signaling between conditions | [`Cell_cell_communication`](https://github.com/ambertrujillo/Thalamus_atlas_cell_cell_communication.git) | CellChat |
| Detect STMN2 cryptic exons and check spatial expression | [`STMN2_CE_and_Spatial_Omics`](https://github.com/Mira0507/th_atlas.git) | Regtools, LeafCutter, Visium, Seurat |

## Workflow

All analyses start from the same annotated, integrated atlas. 

## Inputs and outputs at a glance

| Module | Main input | Key outputs |
|---|---|---|
| Differential cell-type proportion | Atlas metadata: one row per cell with sample ID, cell type, disease, and covariates | Per-sample cell-type proportions; per-cell-type test statistics (effect size, p-value, FDR) |
| Pseudobulked DEG | Atlas counts and cell-type annotation; sample metadata (disease, sex, age at death, PMI, cohort) | Per cell type and disease: pseudobulk count matrix, RUVSeq factors (`metadata_RUVs_k*.csv`), DESeq2 results (log2FC, shrunken log2FC, adjusted p-value) |
| Cell-cell communication | Atlas expression and cell-type labels, split by condition | One CellChat object per condition; comparative interaction and pathway plots |
| STMN2 CE and spatial omics |  |  |

## Getting the code

You must clone a specific submodule and cannot clone all submodules at once. 

## Shared conventions

- **Cell-type names** must match between modules (for example `ExNeu RNF220+`, `InNeu SOX14-`, `Astrocyte`, `OL`, `OPC`, `Microglia`, `BVC`). Use the atlas annotation column as the single source of truth.
- **Unit of replication** is the sample (donor), never the cell.
- **Disease sets** are analyzed separately (AD versus control, FTD versus control).

## Data availability

Processed and raw data will be available upon publication of <manuscript link>

