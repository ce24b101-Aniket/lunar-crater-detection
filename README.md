# Lunar Crater Detection — Model01

This repository is limited to the lunar crater detection materials in the supplied `Model01` folder.

## Contents

- `notebooks/train-and-evaluate.ipynb` — training and evaluation
- `notebooks/image-inference.ipynb` — crater detection on uploaded images
- `notebooks/geotiff-inference.ipynb` — raster and GeoTIFF inference workflow
- `docs/pipeline-guide.docx` — supplied step-by-step guide
- `figures/architecture/` — supplied crater pipeline diagrams
- `figures/results/` and `results/` — selected plots, tables, and run configuration extracted from the supplied training outputs
- `weights/best.pt` — crater detection checkpoint from the supplied outputs

The training notebook identifies the Kaggle/Hugging Face dataset used for crater labels. Dataset imagery and the complete output archives are not included in this repository; see the notebooks and selected result files for the project details.

Some dataset tile names contain “Apollo17” as a lunar image-site label. They are part of the crater detection dataset; this repository contains no Apollo seismography materials.

This is a research project. Review the notebook settings, evaluation protocol, and applicable dataset/model terms before reusing the checkpoint or reporting results.
