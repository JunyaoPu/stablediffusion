# This is a quick guide to setup the SD V2

## Hardware used in this test

RTX3090 with 24GB VRAM, this test require 15 / 24 VRAM

## Clone the repo

```bash
git clone xxx
```

## Creating the conda enviroment

```bash
cd stablediffusion
conda env create -f environment.yaml
```

```bash
source activate ldm
```

OR

```bash
conda activate ldm
```

## Downloading the v2-1_768-ema-pruned.ckpt

```bash
mkdir models
cd models
wget --content-disposition "https://huggingface.co/stabilityai/stable-diffusion-2-1/resolve/main/v2-1_768-ema-pruned.ckpt"
```

## Run the scripts/txt2img.py

```bash
cd ~
cd stablediffusion
conda activate ldm
python scripts/txt2img.py --prompt "Elon Musk is standing in the white house with Donald Trump" --ckpt models/v2-1_768-ema-pruned.ckpt --config configs/stable-diffusion/v2-inference-v.yaml --H 768 --W 768  --device "cuda" --n_samples 1
```

# Speed up with xformers

This will reduce the inference time by almost 50%

This will reduce the usage of VRAM from 15GB to 11GB

## Installing xformers

```bash
cd ~
cd stablediffusion
conda activate ldm
pip3 install xformers
```

## Run the scripts/txt2img.py with more efficient model inference.
```bash
cd ~
cd stablediffusion
conda activate ldm
python scripts/txt2img.py --prompt "Elon Musk is standing in the white house with Donald Trump" --ckpt models/v2-1_768-ema-pruned.ckpt --config configs/stable-diffusion/v2-inference-v.yaml --H 768 --W 768  --device "cuda" --n_samples 1
```
