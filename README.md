# X-MAD: A Public Multi-Anatomy X-ray Dataset for Self-Supervised Learning

This repository contains the code and exploratory self-supervised learning benchmark accompanying the X-MAD dataset manuscript, currently being prepared for submission to **Data in Brief (Elsevier)**.

**X-MAD** is a collection of **5,595 unlabeled JPG radiographic images** acquired at **Ibn Hayyan Specialist Hospital, Sana'a, Yemen**. The images represent several anatomical regions, including the chest, skull, spine, abdomen, pelvis, and extremities. The collection is intended for research on self-supervised learning, unsupervised representation learning, masked image modeling, clustering, and annotation-efficient medical image analysis.

> **Dataset and code are separate.** This GitHub repository is for the benchmark implementation. The image collection is referenced on Zenodo. The dataset does **not** provide diagnostic labels, anatomy labels, patient demographics, examination identifiers, or radiology reports.

## Dataset

- **Dataset:** X-MAD
- **Images:** 5,595
- **File format:** JPG
- **Organization:** One unlabeled image collection; anonymous sequential filenames `XMAD_000001.jpg` through `XMAD_005595.jpg`
- **Anatomical coverage:** Chest, skull, spine, abdomen, pelvis, and extremities (no per-image anatomical labels supplied)
- **Repository:** Zenodo
- **DOI:** [10.5281/zenodo.20125279](https://doi.org/10.5281/zenodo.20125279)

**Access note:** Verify that the Zenodo record is publicly accessible, that the images and documentation can be downloaded, and that the deposited license and permissions permit the stated reuse before describing the dataset as publicly released. The manuscript identifies **CC BY 4.0** as the intended dataset license; the Zenodo record and institutional authorization must agree.

## Benchmark overview

The accompanying workflow covers:

1. Loading JPG radiographs and converting them to three-channel grayscale
2. Resizing to `224 × 224` for baseline model input and applying training normalization
3. Self-supervised masked image modeling (masked autoencoder-style baseline)
4. Tracking training and validation reconstruction losses
5. Producing masked image reconstruction examples
6. Extracting image-level feature embeddings
7. Principal component analysis (PCA)
8. t-SNE and UMAP embedding visualizations
9. K-means clustering, silhouette analysis, and representative cluster images

The baseline is a **demonstration of possible analyses using the unlabeled dataset**, not a clinically validated diagnostic system or a new supervised classification benchmark.

## Reported baseline configuration

The manuscript reports the following settings. For precise architecture details, normalization constants, random seeds, and analysis parameters, consult the released notebook or source code and ensure they match the implementation.

| Component | Setting |
| --- | --- |
| Input size | `224 × 224` |
| Image representation | Three-channel grayscale |
| Patch size | `16 × 16` |
| Patches per image | `196` |
| Masking ratio | `0.75` |
| Train/validation split | `80/20` (image-level) |
| Batch size | `32` |
| Training epochs | `30` |
| Optimizer | AdamW |
| Initial learning rate | `1e-4` |
| Weight decay | `0.05` |
| Learning-rate schedule | Cosine annealing |
| Training | From scratch, without annotations |

**Splitting limitation:** No patient or examination identifiers are released. Therefore, the reported image-level split cannot establish patient-level independence between training and validation sets.

## Running the benchmark

The manuscript references the notebook:

```text
notebooks/X-MAD.ipynb
```

1. Obtain the X-MAD images from the Zenodo record, subject to applicable permissions and access conditions.
2. Set the input image directory in the notebook to the location of the downloaded JPG files.
3. Install the software dependencies required by the notebook and configure the relevant device (CPU/GPU).
4. Run the preprocessing, model-training, embedding extraction, and analysis cells in order.

**Before release:** Confirm that `notebooks/X-MAD.ipynb` exists, runs from a clean environment, and documents its dependencies and paths. These instructions intentionally do not invent an installation command or file path that has not been verified.

## Experimental outputs

Depending on the notebook's output settings, an analysis run may produce feature embeddings, PCA summaries, 2D projections, cluster assignments, reconstruction examples, and figures. The directory structure below is **illustrative**, not a claim that these files are currently committed or automatically generated:

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

For reproducibility, preserve the experiment configuration and trained model checkpoint alongside the generated outputs when sharing results.

## Manuscript and authors

**Manuscript title:** *X-MAD: A Public Multi-Anatomy X-ray Dataset for Self-Supervised Learning*

**Target journal:** *Data in Brief* (manuscript in preparation; no published article DOI is claimed).

**Authors:** Ahmed Alasri; Zhihua Cai; Abdulrahman Noman; Kamal Sharha; Roobaea Alroobaea; Ali Elrashidi; Saleh Naijb; Al-Baraa Abdulrahman; Abdullah Alhamdani.

The author list above reflects the current manuscript draft. Please confirm all authors' consent and contributions before submission.

## Citation

**For the images:** Cite the [Zenodo dataset record](https://doi.org/10.5281/zenodo.20125279), using the citation/BibTeX exported by Zenodo to ensure that the author names, title, publication date, and version exactly match the deposited record. Update the record's metadata if the dataset creators have changed.

**For the manuscript:** The following is a *draft unpublished-manuscript entry*, not a citation to an accepted or published paper:

```bibtex
@unpublished{xmad_manuscript_2026,
  title  = {X-MAD: A Public Multi-Anatomy X-ray Dataset for Self-Supervised Learning},
  author = {Alasri, Ahmed and Cai, Zhihua and Noman, Abdulrahman and
            Sharha, Kamal and Alroobaea, Roobaea and Elrashidi, Ali and
            Naijb, Saleh and Abdulrahman, Al-Baraa and Alhamdani, Abdullah},
  year   = {2026},
  note   = {Manuscript in preparation for Data in Brief}
}
```


## Licenses and permissions

- **Dataset:** The manuscript describes an intended **CC BY 4.0** release. Check the actual license on Zenodo and the hospital's authorization for public redistribution before reuse or public promotion.
- **Code:** Consult this repository's `LICENSE` file for the applicable software license. If no license file has been published, do not assume that the code is available under an open-source license.

## Contact

**Ahmed Alasri**  
School of Computer Science  
China University of Geosciences, Wuhan, China  
Email: [hezhamu@cug.edu.cn](mailto:hezhamu@cug.edu.cn)  
ORCID: [0009-0000-3133-8782](https://orcid.org/0009-0000-3133-8782)

## Disclaimer

The X-MAD dataset and benchmark are intended for research and education only. They are **not** intended for clinical diagnosis, treatment decisions, or direct patient care. Users are responsible for meeting applicable privacy, ethical, institutional, legal, and regulatory requirements. Image-level benchmarks without patient identifiers should not be interpreted as demonstrating patient-independent or clinical performance.
