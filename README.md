## Overview

This repository provides an end-to-end MATLAB pipeline for classifying neuronal cell types in mouse primary visual cortex (V1) based on their responses to visual stimuli. The workflow is designed to operate within the **Scanbox** imaging environment and integrates multiple stages of calcium imaging data processing, stimulus alignment, feature extraction, and classification. Both population-level summaries and single-cell analyses are supported.

![plot](https://github.com/ryan-gorzek/celltype-tuning-V1/blob/main/plots/celltype.png)
## Features

* Automated loading of calcium imaging, stimulus, quadrature, and eye-tracking data.
* Construction of MATLAB structure arrays linking neural activity to stimulus presentation.
* Cell filtering based on responsiveness (ON/OFF domain criteria, SNR thresholds).
* Population-level visualization:
  * Orientation, spatial frequency, direction selectivity, temporal frequency, contrast, and size tuning histograms.
  * Contextual modulation (center/surround, cross/iso).
  * Stationary vs. running tuning curves.
* Single-cell characterization:
  * ON/OFF receptive field kernels.
  * Multi-stimulus tuning surfaces (orientation, spatial frequency, contrast, size).
  * Context-modulated PSTHs.
* Dimensionality reduction (PCA, t-SNE) on response features.
* Cell type classification (e.g., pyramidal vs. SST interneurons) using discriminant analysis with cross-validation.
* Performance evaluation against shuffled baselines.

## Repository Structure

* `stimuli/` – Scripts that run visual stimuli on a Neurolabware microscope utilizing Scanbox and Processing.
* `tools/` – Helper functions for loading data, visualization, and classification.
* `population_singlecell.m` – Pipeline for generating population- and single cell-level summaries for individual or pooled sessions.
* `celltype.m` – Pipeline for comparing response properties of cell types (e.g., Cre-driver lines) recorded in separate sessions.

## Requirements

* MATLAB (tested on R2022b or newer).
* [Scanbox](https://scanbox.org) environment for raw imaging data acquisition.
* Required MATLAB toolboxes:
  * Statistics and Machine Learning Toolbox
  * Image Processing Toolbox
* Experimental data in Scanbox-compatible format.

## Input Data

The pipeline requires:

* **Calcium imaging data** (`.sbx` files processed with suite2p and extracted signals).
* **Stimulus timing and parameters**.
* **Quadrature signals** for running state.
* **Eye-tracking video data**.

## Output

* Figures summarizing population statistics across visual features.
* Single-cell response kernels and tuning curves.
* Dimensionality reduction plots (PCA, t-SNE).
* Cross-validated classifier performance metrics (observed vs. shuffled distributions).
