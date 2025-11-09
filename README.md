# T2IBias

Uncovering Societal Bias Encoded in the Latent Space of Text-to-Image Generative Models

---

## Overview

T2IBias is a reproducible analysis and code collection for the study titled:

"T2IBias: Uncovering Societal Bias Encoded in the Latent Space of Text-to-Image Generative Models"

Abstract:  
In this research we generated 5,000 text-to-image outputs using 10 profession-related, demographically neutral prompts. Each evaluated model generated 1,000 images (100 images per profession). After evaluating these images, we found that the majority of the open-source models examined display demographic biases: high-profile jobs were biased toward white males, caregiving roles were disproportionately feminized, and marginalized groups were underrepresented or stereotyped.

This repository contains the notebooks and supporting materials used to generate, analyze, and evaluate the images produced by multiple open-source text-to-image models.

---

## Contents

- Notebooks (five .ipynb notebooks uploaded):
  - Notebook 1 — Data generation using pretrained text-to-image models (image sampling and prompt list)
  - Notebook 2 — Post-processing and quality filtering (image cleaning, deduplication)
  - Notebook 3 — Automatic demographic inference (tooling used to infer perceived demographic attributes)
  - Notebook 4 — Statistical analysis and visualization (aggregate bias metrics, charts)
  - Notebook 5 — Human-evaluation interface and results aggregation (manual labels, inter-annotator agreement)

Note: Replace the above notebook titles with the actual filenames if they differ. See "Folder structure" below.

---

## Folder structure (suggested)

- notebooks/
  - 01_generate_images.ipynb
  - 02_postprocess_images.ipynb
  - 03_demographic_inference.ipynb
  - 04_analysis_visualization.ipynb
  - 05_human_evaluation.ipynb
- data/
  - prompts.txt
  - generated_images/ (per-model subfolders)
  - annotations/
- results/
  - figures/
  - aggregated_metrics.csv
- requirements.txt
- README.md

Adjust paths to match the repository layout you uploaded.

---

## Getting started (reproduce the experiments)

1. Clone the repository
   - git clone https://github.com/Sufianlab/T2IBias.git
   - cd T2IBias

2. Recommended: create a Python virtual environment
   - python -m venv .venv
   - source .venv/bin/activate  (macOS / Linux)
   - .venv\Scripts\activate     (Windows)

3. Install dependencies
   - If you have a requirements.txt: pip install -r requirements.txt
   - Typical packages used in these notebooks:
     - jupyterlab / notebook
     - numpy, pandas
     - torch (or the framework used by the pretrained model)
     - transformers, diffusers (if using Hugging Face models)
     - pillow,opencv-python
     - matplotlib,seaborn
     - scikit-learn
     - tqdm

   Update the requirements file to match the exact dependencies used in your notebooks.

4. Open and run notebooks
   - jupyter lab
   - or open each .ipynb in Colab (if you add a Colab badge or convert kernels) and run cells sequentially.

5. Reproduce image generation
   - Notebook 1 contains the prompts and the code to sample images from each target model.
   - Ensure you have sufficient GPU resources. Sampling 5,000 images may require multiple hours depending on the model and hardware.

6. Evaluation
   - Automatic inference is performed in Notebook 3.
   - Aggregation and plotting are in Notebook 4.
   - Human evaluation steps and guidelines are in Notebook 5.

---

## Dataset & prompts

- Prompt set: 10 profession-related, demographically neutral prompts (e.g., "A portrait of a person working as a [profession]").
- Generation protocol:
  - Per-model: 1,000 images total
  - Per-profession: 100 images
  - Total images per experiment: 5,000 images (across models / prompts as used in the paper)
- Images, prompts, and annotation files are stored under data/ (or a similar folder). If any of these files are large, consider using Git LFS or a separate storage location and add download instructions.

---

## Models evaluated

This repository uses multiple open-source text-to-image generation models. Please edit the notebooks or the README to list the exact model checkpoints you used, for example:

- model-name-1 (checkpoint info or Hugging Face repo)
- model-name-2
- ...

Include model versions, commit hashes, or Hugging Face model IDs for reproducibility.

---

## Evaluation methodology

- Automatic demographic attribute inference:
  - Off-the-shelf classifiers or custom-trained models can be used to infer perceived attributes such as perceived gender presentation, perceived race/ethnicity, and age groups. See Notebook 3 for implementation details and classifier references.
- Human evaluation:
  - Manual labeling protocol (guidelines, instruction sheets, inter-rater agreement calculation) is described in Notebook 5.
- Metrics:
  - Distributional parity (per-profession demographic distributions)
  - Bias amplification metrics (difference between generated image distributions and expected/neutral baselines)
  - Statistical tests used are described in Notebook 4.

Be explicit in the notebooks about the classifiers and datasets used for attribute inference; those choices critically affect interpretation.

---

## Results (summary)

Key findings (high-level):
- Many open-source text-to-image models encode demographic biases.
- High-profile professions were more frequently depicted as white males.
- Caregiving roles were more often portrayed as female-presenting.
- Marginalized groups were underrepresented or stereotyped.

Refer to the figures and aggregated_metrics.csv in results/ for the full quantitative breakdown and visualizations.

---

## Responsible use & ethics

- These notebooks and analyses examine sensitive topics (race, gender, occupation). Exercise care when interpreting automated demographic inferences — these are imperfect and reflect societal perceptions rather than ground-truth identities.
- Do not use demographic inferences to make decisions about real people.
- Document all choices (
