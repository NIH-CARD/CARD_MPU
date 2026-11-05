# Thalamus Atlas: Analysis Hub

Landing repository for the downstream analyses of the multi-cohort thalamus single-nucleus RNA-seq atlas (Alzheimer's disease and frontotemporal dementia). Each analysis lives in its own repository, linked here as a Git submodule, so methods stay independent and can be versioned and run separately.

## Start here

| I want to... | Go to | Tools |
|---|---|---|
| Test whether cell-type abundance differs by disease | [`Differential_cell_type_proportion`](./Differential_cell_type_proportion) | Propeller |
| Find disease-associated genes within each cell type | [`Pseudobulked_differential_gene_expression`](./Pseudobulked_differential_gene_expression) | RUVSeq, DESeq2 |
| Compare ligand-receptor signaling between conditions | [`Cell_cell_communication`](./Cell_cell_communication) | CellChat |
| Detect STMN2 cryptic exons and check spatial expression | [`STMN2_CE_and_Spatial_Omics`](./STMN2_CE_and_Spatial_Omics) | Regtools, LeafCutter, Visium, Seurat |

## Workflow

All analyses start from the same annotated, integrated atlas. The two cell-type-resolved analyses (DEG and communication) can be run independently. STMN2 cryptic exon detection starts from raw alignments instead of the atlas.

## Inputs and outputs at a glance

| Module | Main input | Key outputs |
|---|---|---|
| Differential cell-type proportion | Atlas metadata: one row per cell with sample ID, cell type, disease, and covariates | Per-sample cell-type proportions; per-cell-type test statistics (effect size, p-value, FDR) |
| Pseudobulked DEG | Atlas counts and cell-type annotation; sample metadata (disease, sex, age at death, PMI, cohort) | Per cell type and disease: pseudobulk count matrix, RUVSeq factors (`metadata_RUVs_k*.csv`), DESeq2 results (log2FC, shrunken log2FC, adjusted p-value) |
| Cell-cell communication | Atlas expression and cell-type labels, split by condition | One CellChat object per condition; comparative interaction and pathway plots |
| STMN2 CE and spatial omics |  | Cryptic exon junction counts and calls per sample; spatial expression maps |

## Getting the code

Clone with submodules so each analysis repository is pulled at the pinned commit:

```bash
git clone --recurse-submodules <[this-repo-url](https://github.com/NIH-CARD/CARD_MPU/tree/main/Thalamus_atlas)>

# if you already cloned without submodules
git submodule update --init --recursive
```

Each submodule is pinned to a specific commit. To move one to its latest version:

```bash
git submodule update --remote Pseudobulked_differential_gene_expression
git add Pseudobulked_differential_gene_expression
git commit -m "Update Pseudobulked DEG submodule"
```

## Shared conventions

- **Cell-type names** must match between modules (for example `ExNeu RNF220+`, `InNeu SOX14-`, `Astrocyte`, `OL`, `OPC`, `Microglia`, `BVC`). Use the atlas annotation column as the single source of truth.
- **Unit of replication** is the sample (donor), never the cell.
- **Disease sets** are analyzed separately (AD versus control, FTD versus control).

## Data availability

Processed and raw data will be available upon publication of <manuscript link>

