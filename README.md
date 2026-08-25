# ASI-FIMSA Spatial Omics Workshop 2026

A two-hour, hands-on introduction to spatial omics for immunologists, run at the
ASI-FIMSA meeting. Everything happens in your browser through Google Colab — there is
nothing to install, and you do not need to be a Python programmer. We look at **one
tissue, breast cancer, through three different technologies**. You will read
and plot the data yourself, find the tissue niches that make up a tumour
microenvironment, and finish by training a small Vision Transformer that predicts gene
expression straight from an H&E image. Four Tutorials, each self-contained, each a
single notebook you open with one click.

## The Tutorials

Click a badge to open that Tutorial in Google Colab. Start with the setup check
**before** you arrive.

| | Tutorial | What you do | Rough time |
|---|---|---|---|
| [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/GenomicsMachineLearning/ASI_FIMSA_2026/blob/main/notebooks/00_setup_check.ipynb) | **00 · Setup check** | Confirms Colab can install the packages and reach the data. (Ideally, run it at home, not in the room.) | ~10 min |
| [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/GenomicsMachineLearning/ASI_FIMSA_2026/blob/main/notebooks/01_read_and_visualise.ipynb) | **01 · Read and visualise** | Load and plot data from each of the three platforms (Visium spots, Xenium cells, and the whole-transcriptome Atera) to see what each one can and cannot resolve. | ~35 min |
| [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/GenomicsMachineLearning/ASI_FIMSA_2026/blob/main/notebooks/02_niche_analysis.ipynb) | **02 · Niche analysis** | Find tissue niches in the tumour microenvironment (e.g., immune infiltration, tumour boundary, stroma), based on which cells sitting next to which. | ~35 min |
| [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/GenomicsMachineLearning/ASI_FIMSA_2026/blob/main/notebooks/02b_cell_cell_interaction.ipynb) | **02b · Cell–cell interaction** | Run stLearn's spatially-constrained ligand–receptor test on the same cells to see how neighbouring cells interact and how this method reduces noisy predictions. | ~30 min |
| [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/GenomicsMachineLearning/ASI_FIMSA_2026/blob/main/notebooks/03_vit_gene_expression.ipynb) | **03 · ViT for gene expression** | Train a small Vision Transformer that predicts gene expression from H&E morphology alone, then look honestly at which genes it gets right and which it does not. | ~40 min |

**Code and teaching material** are [MIT licensed](LICENSE) — reuse, adapt and teach from
them freely. 
