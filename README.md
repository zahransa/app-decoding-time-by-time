<h1 align="center">app-decoding-time-by-time</h1>

<p align="center">
  Decodes condition labels over time from MEG gradiometer epochs with MNE-Python SlidingEstimator (standardised logistic regression, 5-fold ROC AUC) and plots the decoding score time course.
</p>

<p align="center">
  <a href="https://github.com/brainlife/abcd-spec"><img src="https://img.shields.io/badge/ABCD_Spec-v1.1-green.svg" alt="ABCD Spec v1.1"></a>
  <a href="https://doi.org/10.25663/brainlife.app.655"><img src="https://img.shields.io/badge/Brainlife-brainlife.app.655-blue.svg" alt="Run on brainlife.io"></a>
</p>

## At a glance

<!-- brainlife-app:begin (generated from the App manifest; edit the manifest, not this block) -->

> **Decodes condition labels over time from MEG gradiometer epochs with MNE-Python SlidingEstimator (standardised logistic regression, 5-fold ROC AUC) and plots the decoding score time course.**

Selects the 'auditory' epochs, keeps the gradiometer channels and fits a scikit-learn pipeline (StandardScaler and LogisticRegression) independently at each time point with mne.decoding.SlidingEstimator, scoring with 5-fold cross-validated ROC AUC against event codes. Outputs a PNG of the mean score over time with the chance level. The condition name and channel type are hard-coded (MNE sample-dataset style 'auditory' left vs right), so it only runs on epochs that contain an 'auditory' condition with two event codes and gradiometers.

| | |
|---|---|
| **Inputs** | `neuro/meeg/mne/epochs` |
| **Outputs** | `generic/image/png` |
| **Container** | `brainlife/mne:1.0.2` |
| **Resources** | 1 CPUs |
| **Run it** | [doi.org/10.25663/brainlife.app.655](https://doi.org/10.25663/brainlife.app.655) |

#### Inputs

| Input | Datatype | Required | Description |
|---|---|---|---|
| `epo` | `neuro/meeg/mne/epochs` | yes | MEG epochs (MNE -epo.fif) with an 'auditory' condition. Must contain gradiometer channels and events tagged auditory with two classes. |

#### Outputs

| Output | Datatype | Description |
|---|---|---|
| `out_figs` | `generic/image/png` | Sensor-Space-Decoding.png: mean cross-validated ROC AUC over time with the chance level. |

<!-- brainlife-app:end -->

## Running the App

### On brainlife.io

Open the App at [doi.org/10.25663/brainlife.app.655](https://doi.org/10.25663/brainlife.app.655), choose `neuro/meeg/mne/epochs` from your project and press **Execute**. The results are saved to your project as `generic/image/png`.

### Locally

You need [Singularity/Apptainer](https://apptainer.org/) (the App runs in `brainlife/mne:1.0.2`), [`jq`](https://jqlang.github.io/jq/).

1. Clone this repository.
2. Create `config.json` with the paths to your inputs and the parameters:

   ```json
   {
       "epo": "/path/to/epo/epo"
   }
   ```

3. Run `./main`.

## Citing

If you use this App, please cite it, the software it builds on and brainlife.io:

- app-decoding-time-by-time. brainlife.io App. [doi:10.25663/brainlife.app.655](https://doi.org/10.25663/brainlife.app.655)
- Gramfort et al. MEG and EEG data analysis with MNE-Python. *Frontiers in Neuroscience* 7 (2013). [doi:10.3389/fnins.2013.00267](https://doi.org/10.3389/fnins.2013.00267)
- Hayashi S, Caron BA, Heinsfeld AS, et al. brainlife.io: a decentralized and open-source cloud platform to support neuroscience research. *Nature Methods* 21:809–813 (2024). [doi:10.1038/s41592-024-02237-2](https://doi.org/10.1038/s41592-024-02237-2)
- Avesani P, McPherson B, Hayashi S, et al. The open diffusion data derivatives, brain data upcycling via integrated publishing of derivatives and reproducible open cloud services. *Scientific Data* 6:69 (2019). [doi:10.1038/s41597-019-0073-y](https://doi.org/10.1038/s41597-019-0073-y)

## Authors

Maintained by [@zahransa](https://github.com/zahransa).
