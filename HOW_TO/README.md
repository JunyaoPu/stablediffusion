# This is a quick guide to setup the SD V2

## clone the repo

```bash
git clone xxx
```

## creating the conda enviroment

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

## downloading the v2-1_768-ema-pruned.ckpt

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
