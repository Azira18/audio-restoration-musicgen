# Audio Restoration Pipeline for MusicGen

This repository contains a machine learning pipeline for **audio restoration**, designed to enhance the technical and perceptual quality of outputs from the MusicGen generative model.

## Pipeline Overview

The pipeline is structured as follows:

### 01_Generate_Audio
- Generates `n` audio files from randomly selected prompts from a list of 50.
- Uses the MusicGen model.

### 02_Source_Separation
- Applies the Demucs model to separate each audio file into six stems: drums, bass, other, vocals, guitar, and piano.

### 03_Stems_Denoising (`.py` only)
- Cleans each individual stem using the `noisereduce` model.
- Denoising can be performed by:
  1. Providing a `noise_clip` along with the stem (I used the vocals as the `noise_clip` because they contain the most noise), or  
  2. Providing only the stem.

### 03_Stems_Analysis
- Compares waveforms and spectrograms of each stem.
- Evaluates audio quality using DNSMOS.

### 04_Reconstruction_and_Analysis
- Reconstructs the audio by summing all cleaned stems (excluding vocals).
- Analyzes the results.

## Usage
- All files can be saved and run on **Google Colab** to listen to the processed audio tracks.

## References

- [MusicGen GitHub](https://github.com/facebookresearch/audiocraft)
- [Demucs: Source Separation](https://github.com/facebookresearch/demucs)
- [noisereduce Python library](https://github.com/timsainb/noisereduce)
- [DNSMOS: Deep Noise Suppression MOS](https://github.com/microsoft/DNS-Challenge)

