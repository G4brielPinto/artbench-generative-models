# ArtBench Generative Models

An academic comparison of four generative-model families for 32×32 artwork images from the
ArtBench-10 benchmark:

- autoencoders;
- conditional GAN (cGAN);
- DCGAN;
- denoising diffusion model.

The notebooks contain model definitions, training flows, sample generation and image-quality
evaluation using FID/KID-oriented metrics.

## Included and excluded material

This portfolio edition includes only source notebooks and a small local dataset loader. It excludes
the ArtBench files, a coursework-specific training subset, generated images, checkpoints, logs and
the internal report.

The loader in scripts/artbench_local_dataset.py was reconstructed from the equivalent loader
already present in the cGAN/DCGAN notebooks. It makes the autoencoder and diffusion notebooks
self-contained without changing their expected dataset format.

## Repository layout

~~~text
.
├── notebooks/
│   ├── Autoencoders.ipynb
│   ├── CGAN.ipynb
│   ├── DCGAN.ipynb
│   └── Diffusion_Model_.ipynb
├── scripts/
│   └── artbench_local_dataset.py
└── requirements.txt
~~~

## Setup

Use Python 3.10 or newer in an isolated virtual environment.

~~~bash
python -m venv .venv
python -m pip install --upgrade pip
python -m pip install -r requirements.txt
jupyter lab
~~~

Launch Jupyter from the repository root and open a notebook from notebooks/.

## Local data contract

The original project expects a local ArtBench-10 download and a CSV that identifies the
coursework subset. These files are intentionally not versioned. Create the following local layout:

~~~text
.
├── ArtBench-10/
│   ├── ArtBench-10.csv
│   └── artbench-10-python/
│       └── artbench-10-batches-py/
│           ├── meta
│           ├── data_batch_1 … data_batch_5
│           └── test_batch
└── student_start_pack/
    └── training_20_percent.csv
~~~

The subset CSV must contain a train_id_original column. The local loader validates the expected
CSV columns and ArtBench batch layout before constructing dataset splits.

## Reproducibility notes

- Training is computationally expensive; a CUDA-capable GPU is recommended.
- Notebook outputs and execution counts were removed before this edition was prepared.
- Historical results are not included and are not presented as newly reproduced benchmarks.
- Run each notebook independently in an environment that contains the local data contract above.

## Privacy and sharing

No data, generated artwork, checkpoints, institutional documents, personal contact details or
secrets are present. The repository is initially private while it is reviewed for a future public
portfolio release.
