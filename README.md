# audio-restoration-musicgen
This repository contains a machine learning pipeline for audio restoration, designed to enhance the technical and perceptual quality of outputs from the MusicGen generative model.

Here’s how I structured the pipeline:
- 01_Generate_Audio: I used the MusicGen model to generate n audio files from n prompts randomly selected from a list of 50.
- 02_Source_Separation: I applied the Demucs model to separate each audio file into six stems: drums, bass, other, vocals, guitar, and piano.
- 03_Stems_Denoising (available only in .py format): I used the noisereduce model to clean each individual stem. Denoising can be performed either by providing a noise_clip along with the stem to be cleaned (I used the vocals as the noise_clip, since they contain the most noise) or by providing only the stem to the model.
- 03_Stems_Analysis: I compared waveforms and spectrograms of each stem and used DNSMOS to evaluate audio quality.
- 04_Reconstruction_and_Analysis: I reconstructed the audio by summing all the cleaned stems (excluding vocals) and analyzed the results.

It is possible to save the files and run them on Google Colab to listen to all the audio tracks.
