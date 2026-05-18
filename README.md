# X-MAD Benchmark Code

This repository contains the benchmark code for the X-MAD dataset paper:

**X-MAD: A Public Multi-Anatomy X-ray Dataset for Self-Supervised Learning in Low-Resource Radiographic Imaging**

X-MAD is a public multi-anatomy X-ray dataset collected from Ibn Hayyan Specialist Hospital in Sana'a, Yemen. The dataset contains **5,595 de-identified JPG radiographic images** and is intended for research on self-supervised learning, unsupervised representation learning, clustering, masked image modeling, and annotation-efficient medical imaging.

> **Note:** This repository contains the code and benchmark pipeline. The dataset images are hosted separately on Zenodo.

---

## Dataset

The X-MAD dataset is available on Zenodo:

**DOI:** `10.5281/zenodo.20125279`

The dataset contains:

- 5,595 de-identified JPG radiographic images
- Multi-anatomy plain X-ray images

The dataset is released under the **Creative Commons Attribution-NonCommercial 4.0 International License (CC BY-NC 4.0)**.

---


## Benchmark Overview

The benchmark pipeline includes:

1. Image loading and preprocessing
2. Three-channel grayscale conversion
3. Resizing to `224 × 224` pixels for baseline experiments
4. Normalization for model training
5. Masked autoencoder-style self-supervised learning
6. Feature extraction from the trained encoder
7. PCA feature-space analysis
8. t-SNE and UMAP visualization
9. K-means clustering
10. Masked image reconstruction

---

## Baseline Configuration

| Component | Setting |
|---|---|
| Input size | `224 × 224` |
| Image format | Three-channel grayscale |
| Patch size | `16 × 16` |
| Number of patches | `196` |
| Mask ratio | `0.75` |
| Train/validation split | `80/20` |
| Batch size | `32` |
| Epochs | `30` |
| Optimizer | AdamW |
| Learning rate | `1e-4` |
| Weight decay | `0.05` |
| Scheduler | Cosine annealing |

---



## Running the Benchmark

### 1. Train the self-supervised model

Run the notebook or training script:


```text
notebooks/X-MAD.ipynb
```



## Outputs

Typical outputs include:

```text
outputs/
├── features.npy
├── pca_results.csv
├── tsne_embeddings.csv
├── umap_embeddings.csv
├── cluster_assignments.csv
├── reconstruction_examples/
└── figures/
```

---



## Citation

If you use this code or the X-MAD dataset, please cite the dataset and paper:

```bibtex

```

Dataset DOI:

```text
10.5281/zenodo.20125279
```

---

## License

The benchmark code is released for research use. Please check the repository license file for the exact software license.

The X-MAD dataset images are released separately under **CC BY-NC 4.0**, which permits sharing and adaptation for non-commercial purposes only with appropriate attribution.

---

## Contact

For questions, please contact:

```text
Ahmed Alasri
School of Computer Science
China University of Geosciences, Wuhan, China
ORCID: https://orcid.org/0009-0000-3133-8782
```

---

## Disclaimer

The X-MAD dataset and benchmark code are provided for research and educational purposes only. They are not intended for clinical diagnosis, clinical decision-making, treatment planning, or direct patient care. Users are responsible for ensuring that their use of the dataset and code complies with applicable ethical, legal, institutional, and regulatory requirements.
