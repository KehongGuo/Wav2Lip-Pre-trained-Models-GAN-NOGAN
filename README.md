# Wav2Lip Pre-trained Models (GAN & NOGAN)

This repository provides pre-trained checkpoint files for the Wav2Lip model, specifically the GAN (Generative Adversarial Network) and NOGAN (Non-GAN) versions. These files are intended for easy cloning and use in projects that require high-quality, audio-driven lip synchronization.

## About Wav2Lip

Wav2Lip is a state-of-the-art deep learning model for generating accurate lip-sync videos from an audio track and a static face or video. It excels at producing realistic mouth movements that are tightly synchronized with the input audio, even for faces in unconstrained environments.

- **Original Paper**: [A Lip Sync Expert Is All You Need for Speech to Lip Generation In The Wild](https://arxiv.org/abs/2008.10010)
- **Original Repository**: [Rudrabha/Wav2Lip](https://github.com/Rudrabha/Wav2Lip)

## Models Included

This repository contains two key pre-trained models. Both are designed to work with the standard Wav2Lip inference code.

### 1. `Wav2Lip-SD-GAN.pt`

This is the **GAN (Generative Adversarial Network)** version of the model.

- **Characteristics**:
  - **Higher Quality & Detail**: Generally produces sharper, more realistic, and visually pleasing results. It is better at preserving fine details like beard stubble, skin texture, and reflections.
  - **Slightly Slower**: The adversarial training makes the model more complex, which can result in slightly longer inference times compared to the NOGAN version.
- **Recommended for**: Final productions, high-quality outputs, and scenarios where visual fidelity is the top priority.

### 2. `Wav2Lip-SD-NOGAN.pt`

This is the **NOGAN (Non-GAN)** version, which uses a simpler reconstruction loss.

- **Characteristics**:
  - **Faster Inference**: Simpler architecture leads to quicker video generation.
  - **Softer/Smoother Output**: The results can sometimes appear less sharp or slightly blurrier than the GAN version. It may struggle with preserving very fine facial details like beards, sometimes "painting over" them.
- **Recommended for**: Quick previews, rapid prototyping, or applications where speed is more critical than achieving the absolute highest visual quality.

## How to Use

You can integrate these models into your own project by cloning this repository or by directly downloading the required `.pt` files.

### Option 1: Clone the Repository

This is the recommended method if you want to keep the models organized.

```bash
# Clone this repository into your project directory
git clone https://github.com/KehongGuo/Wav2Lip-Pre-trained-Models-GAN-NOGAN.git
```

Then, in your Wav2Lip inference script, point the `--checkpoint_path` to the model file within the cloned directory.

**Example:**
```bash
python /path/to/Wav2Lip/inference.py \
  --checkpoint_path /path/to/your-repo-name/Wav2Lip-SD-GAN.pt \
  --face "input_video.mp4" \
  --audio "input_audio.wav" \
  --outfile "result_gan.mp4"
```

### Option 2: Direct Download with `wget`

You can also download the files directly into your project's `checkpoints` folder using `wget`.

1.  Navigate to the file you want in this GitHub repository (e.g., `Wav2Lip-SD-GAN.pt`).
2.  Click the "Download raw file" button.
3.  Copy the URL from your browser's address bar.

**Example command:**
```bash
# Create the checkpoints directory if it doesn't exist
mkdir -p /path/to/Wav2Lip/checkpoints

# Download the GAN model
wget "https://github.com/KehongGuo/Wav2Lip-Pre-trained-Models-GAN-NOGAN.git"

# Download the NOGAN model
wget "https://github.com/KehongGuo/Wav2Lip-Pre-trained-Models-GAN-NOGAN.git" -O /path/to/Wav2Lip/checkpoints/Wav2Lip-SD-NOGAN.pt
```

### Option 3: For Google Colab (Recommended for Notebooks)

This is the easiest and most reliable way to use the models in a Google Colab notebook. The `!git clone` command is fast and handles everything for you.

Place the following code block in a setup cell in your Colab notebook.

```python
# @title Download Wav2Lip and Pre-trained Models
# --- 1. Clone the official Wav2Lip repository ---
%cd /content/
!git clone https://github.com/Rudrabha/Wav2Lip.git

# --- 2. Clone this repository for the pre-trained models ---
!git clone https://github.com/KehongGuo/Wav2Lip-Pre-trained-Models-GAN-NOGAN.git wav2lip_models

# --- 3. Copy the models into Wav2Lip's checkpoint directory ---
!mkdir -p /content/Wav2Lip/checkpoints
!cp /content/wav2lip_models/Wav2Lip-SD-GAN.pt /content/Wav2Lip/checkpoints/
!cp /content/wav2lip_models/Wav2Lip-SD-NOGAN.pt /content/Wav2Lip/checkpoints/
```

After running this setup cell, you can run your Wav2Lip inference command using the standard path, as the models will be in the expected location.

## License

These model files are provided under the same license as the original Wav2Lip project. Please refer to their repository for detailed licensing information. Use of these models should comply with ethical AI guidelines and be for responsible purposes only.

## Acknowledgements

All credit for the training and architecture of these models goes to the original authors of the Wav2Lip paper and their public implementation. This repository is simply a convenient host for the pre-trained weights to facilitate easier access and project setup.

