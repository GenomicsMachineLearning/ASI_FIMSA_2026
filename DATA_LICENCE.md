# Data sources and licences

The Workshop uses three public 10x Genomics datasets. Two are downloaded directly from
10x's CDN at run time; the third is redistributed here in derived form, which the licence
below permits with attribution.

## Atera — whole-transcriptome Xenium, FFPE human breast cancer

**Source:** 10x Genomics, *Preview Data: Atera In Situ Gene Expression, FFPE Human Breast
Cancer* — https://www.10xgenomics.com/datasets/atera-wta-ffpe-human-breast-cancer
**Licence:** Creative Commons Attribution 4.0 International (CC BY 4.0) —
https://creativecommons.org/licenses/by/4.0/
**Attribution:** Data © 10x Genomics, used under CC BY 4.0.

This dataset is **pre-release**: 18,028-target "Human WTA (pre-release)" panel,
`chemistry_version: "Atera v1"`, on a Gen2 prototype instrument. 10x notes that preview
data was generated with development versions of the panel, user guides and analysis
software and may be replaced by data from the final workflow.

**What we redistribute is derived, not the original bundle.** From the ~65 GB original we
publish two small artifacts (~38 MB total) at
`https://huggingface.co/datasets/xiao233333/asi-fimsa-workshop-2026`:

- `atera_wholeslide_cells.h5ad` — all 170,057 cells: aligned centroids, the vendor's own
  graph-based and k-means clusterings, UMAP and PCA, our merged cell-type labels, and a
  69-gene marker counts matrix. No images.
- `atera_crop.zarr.zip` — a 2,000 µm square containing 16,006 cells, with an H&E overview,
  a native-resolution zoom, per-cell boundary polygons and the annotated table.

**One further derived artifact is committed to this repository rather than staged.**
`notebooks/assets/atera_crop_he.jpg` (2.1 MB) and its `atera_crop_he.json` sidecar are the
Crop's H&E overview, JPEG-encoded, plus the micrometres it covers. Those are the same
downsampled pixels already published inside `atera_crop.zarr.zip`, re-encoded so that
Tutorial 3 can draw its maps on tissue without installing the spatialdata stack; nothing new
about the slide is disclosed. The attribution travels with the image, in the `licence` field
of the JSON. Built by `prep/build_he_backdrop.py`.

Changes made to the original: spatial subsetting to one window; restriction of the
expression matrix to a 69-gene marker panel; image downsampling; and the addition of
cell-type labels derived by us (see below). The full derivation is reproducible from the
scripts in `prep/`.

**Cell-type labels are ours, not 10x's.** They were derived automatically from the
vendor's shipped per-cluster differential expression, merging 34 graph-based clusters into
12 named populations, then reviewed by a human. 14 of the 34 clusters are flagged
`low_confidence` in `prep/atera_cluster_annotation.csv`, and three are deliberately left
`Unassigned` or `Mixed`. Treat them as teaching material, not as a reference annotation.

## Xenium — FFPE human breast cancer, 313-gene panel

**Source:** 10x Genomics, `Xenium_FFPE_Human_Breast_Cancer_Rep1` —
https://www.10xgenomics.com/datasets/xenium-ffpe-human-breast-with-custom-add-on-panel-1-standard
**Attribution:** Data © 10x Genomics. Please also cite the accompanying publication:

> Janesick A, Shelansky R, Gottscho AD, *et al.* High resolution mapping of the tumor
> microenvironment using integrated single-cell, spatial and in situ analysis.
> *Nature Communications* **14**, 8353 (2023). https://doi.org/10.1038/s41467-023-43458-x

Downloaded live from 10x's CDN by the Tutorials. Not redistributed here.

## Visium — human breast cancer, Block A Section 1

**Source:** 10x Genomics, `V1_Breast_Cancer_Block_A_Section_1` —
https://www.10xgenomics.com/datasets/human-breast-cancer-block-a-section-1-1-standard-1-0-0
**Attribution:** Data © 10x Genomics.

Downloaded live from 10x's CDN by the Tutorials. Not redistributed here.

## connectomeDB2020 — the ligand–receptor pair list

Used by `prep/06_build_cci_table.py` to decide which genes the `atera_crop_lr.h5ad`
panel contains, and quoted for contrast in Tutorial 3.

- **Source:** connectomeDB2020, published as part of NATMI — Hou R., Denisenko E.,
  Ong H.T., Ramilowski J.A., Forrest A.R.R., "Predicting cell-to-cell communication
  networks using NATMI", *Nature Communications* 11, 5011 (2020).
  <https://www.nature.com/articles/s41467-020-18873-z>
- **How it reaches this repo:** it does not. The prep script fetches the pair tables
  from the stLearn GitHub repository at build time
  (`stlearn/tl/cci/databases/connectomeDB2020_{lit,put}.txt`) and does not keep them.
  No Tutorial downloads them; Tutorial 3 reads only the per-database coverage counts
  that `prep/06_build_cci_table.py` recorded in `atera_crop_lr.h5ad`.
- **What IS committed here:** `prep/cci_panel_genes.txt`, a list of 1,673 HGNC gene
  symbols — the intersection of connectomeDB2020's gene set with the Atera panel,
  filtered by detection. A list of gene symbols is a fact about which genes this
  experiment measured, not a reproduction of the curated pair database, so no part of
  connectomeDB2020's content is redistributed by this repository.
- **Derived artifact:** `atera_crop_lr.h5ad` contains Atera expression counts for those
  genes. Its licence is the Atera licence (CC BY 4.0, above); connectomeDB2020 only
  chose the columns.
