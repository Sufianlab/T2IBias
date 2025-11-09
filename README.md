# T2IBias

Uncovering Societal Bias Encoded in the Latent Space of Text-to-Image Generative Models

Authors: Abu Sufian, Cosimo Distante, Marco Leo, Hanan Salam  

Accepted at: First Interdisciplinary Workshop on Responsible AI for Value Creation — Copenhagen, Denmark, Dec. 1st 2025

---

## Short Abstract

In this research we generated 5,000 text-to-image (T2I) outputs using 10 profession-related, demographically neutral prompts using five pouplar open-source T2I generation models. Each evaluated model generated 1,000 images (100 images per profession). After evaluating these images by a nine-member diverse human team, we found that the majority of the open-source models examined display demographic biases: high-profile professions were disproportionately depicted as white males, caregiving roles were predominantly feminized, and marginalized groups were underrepresented or stereotyped.

Generated Dataset: https://drive.google.com/file/d/1gQkKor-4dtKx9tJWf7z3N753ETY759bA/view?usp=drive_link

---

## Repository summary

This repository contains the code, notebooks, and supporting materials used to (1) Images from multiple open-source text-to-image models using a fixed prompt set, (2) post-process and filter generated images, (3) automatically and manually infer perceived demographic attributes, and (4) compute and visualize bias metrics across professions and models.

The uploaded notebooks each contain code to generate images from one pretrained text-to-image model using operations in the model's latent/feature space. Together they produce the experiment set described in the paper.

---

## Notebooks (uploaded)

Each notebook corresponds to a single pretrained open-source text-to-image model and includes sampling code, seeds, and generation hyperparameters. Replace the placeholder filenames below with the actual notebook filenames you uploaded if they differ.

- notebooks/
  - 01_modelA_generate.ipynb — sampling and checkpoint info for Model A
  - 02_modelB_generate.ipynb — sampling and checkpoint info for Model B
  - 03_modelC_generate.ipynb — sampling and checkpoint info for Model C
  - 04_modelD_generate.ipynb — sampling and checkpoint info for Model D
  - 05_modelE_generate.ipynb — sampling and checkpoint info for Model E

For reproducibility, each notebook records:
- the prompt list (10 demographically neutral profession prompts),
- random seed(s),
- sampling hyperparameters (guidance scale, steps, temperature, sampler),
- exact model checkpoint / Hugging Face repo id (or commit hash),
- output folder layout.

---

## Suggested folder structure

- notebooks/                    — the five uploaded notebooks
- data/
  - prompts.txt                  — the 10 profession prompts used
  - generated_images/            — per-model subfolders with PNG/JPEG outputs
  - annotations/                 — human labels and automatic inference outputs (CSV/JSON)
- results/
  - figures/                     — plots produced by analysis
  - aggregated_metrics.csv       — computed bias metrics per model/profession
- requirements.txt
- README.md
- LICENSE

Note: Large image artifacts are not stored in the Git repository. Use Git LFS or the provided Google Drive dataset.

---

## Quick start — reproduce the experiments

1. Clone the repository
   - git clone https://github.com/Sufianlab/T2IBias.git
   - cd T2IBias

2. (Optional but recommended) Create a virtual environment
   - python -m venv .venv
   - source .venv/bin/activate  # macOS / Linux
   - .venv\Scripts\activate     # Windows

3. Install dependencies
   - pip install -r requirements.txt
   - Typical packages used: jupyterlab, numpy, pandas, torch, transformers, diffusers, pillow, opencv-python, matplotlib, seaborn, scikit-learn, tqdm

4. Download the dataset (images, prompts, annotations)
   - Use the shared Google Drive link above and place the contents under data/ or update paths in the notebooks.

5. Run notebooks in order (or open them in Colab)
   - Each generation notebook is self-contained and can be run end-to-end (GPU recommended).
   - Notebooks for automatic inference and analysis assume generated images and annotation CSVs exist in data/.

6. Recompute metrics and figures
   - Run the analysis notebook(s) to regenerate figures in results/figures and aggregated_metrics.csv.

---

## Prompts and generation protocol

- Prompt set: 10 demographically neutral prompts focused on professions (e.g., "A photo of a [profession name]").
- Per-model generation: 1,000 images (100 images × 10 professions).
- Total images per model: 1,000. Total images in the reported experiment (across five models): 5,000.
- Human evaluation: Nine annotators independently labeled perceived demographic attributes (gender presentation, perceived race/ethnicity, age group, and confidence/notes). Inter-annotator agreement statistics are computed and reported in the analysis.

---

## Models evaluated

List the exact model identifiers (Hugging Face model IDs or checkpoint sources) in each notebook and in this README for reproducibility. Example placeholders — replace with actual models used:

- model-A-id (Hugging Face or checkpoint URL)
- model-B-id
- model-C-id
- model-D-id
- model-E-id

Record versions/hashes and licensing information for each model. If a model’s license restricts redistribution, include only generation instructions and provide pointers to the original checkpoint.

---

## Evaluation methodology

Automatic inference:
- Where used, off-the-shelf classifiers or custom models infer perceived demographic attributes from images. Document classifier training data, thresholds, and limitations inside Notebook 3 (automatic inference).
- Report classifier performance on relevant validation sets where possible.

Human evaluation:
- Nine diverse annotators labeled images following a written instruction sheet (included in notebooks/ or data/).
- For each image annotators recorded perceived gender presentation, perceived race/ethnicity, age group, and an optional free-text rationale.
- Inter-annotator agreement and label aggregation procedures (majority vote, consensus thresholds) are computed and supplied with results.

---

## Key findings (high-level)

- Multiple open-source text-to-image models encode and amplify societal biases.
- High-prestige occupations were more frequently depicted as white males.
- Caregiving roles were predominantly depicted as female-presenting.
- Marginalized groups were underrepresented and often depicted via stereotyped cues.

See results/figures and aggregated_metrics.csv for full quantitative results, visualizations, and per-model breakdowns.

---

## Reproducibility checklist

For publication-quality reproducibility include:
- Exact model checkpoints, commit hashes, and sampling code.
- Random seeds and full sampling hyperparameters.
- Annotator demographics and annotation instructions.
- All code required to reproduce analyses in a requirements.txt and environment specification (e.g., conda env.yml).
- A small-scale deterministic example (e.g., 10 images per prompt with fixed seeds) for quick verification.

---

## Ethics, limitations, and responsible use

- The work concerns perceived demographic attributes inferred from images, which are noisy proxies for identity and can reinforce stereotypes. Automatic inferences are not ground-truth and should not be used for decision-making about individuals.
- Report and discuss limitations (classifier biases, annotator demographics, cultural context) prominently with any public release.
- If releasing generated images, verify licenses of the source models and obtain appropriate consent and ethical review where required.
- Provide clear usage guidelines and safeguards to prevent misuse.

---

## Citation

If you use this repository or data please cite:

BibTeX:

@inproceedings{Sufian2025T2IBias,
  title = {T2IBias: Uncovering Societal Bias Encoded in the Latent Space of Text-to-Image Generative Models},
  author = {Abu Sufian and Cosimo Distante and Marco Leo and Hanan Salam},
  booktitle = {First Interdisciplinary Workshop on Responsible AI for Value Creation},
  address = {Copenhagen, Denmark},
  month = {Dec},
  day = {1},
  year = {2025}
}

Plaintext: 

Abu Sufian, Cosimo Distante, Marco Leo, and Hanan Salam. T2IBias: Uncovering Societal Bias Encoded in the Latent Space of Text-to-Image Generative Models. In Proceedings of the First Interdisciplinary Workshop on Responsible AI for Value Creation, Copenhagen, Denmark, December 1, 2025.

---

## License

Choose and add a LICENSE file (e.g., MIT, Apache-2.0). Note: licensing restrictions may apply to included pretrained models and to redistribution of generated images; document these explicitly.

---

## Contributing & contact

- Contributions welcome — open an issue to discuss major changes.
- Preferred workflow: fork → feature branch → PR with tests or reproduction steps.
- Contact / maintainer: @Sufianlab (GitHub)

Thank you for sharing the notebooks and dataset — this README aims to make the repository easier to understand, reproduce, and extend while clearly documenting the paper, experiment protocol, dataset link, and ethics considerations.
