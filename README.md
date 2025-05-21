# Fine-Tuned Models

## Classification Baselines
- resnet18_finetuned.pth
- mobilenet_v2_finetuned.pth

## Few-Shot Model
- protonet_trained.pth (MobileNetV2-based encoder)

## Performance Summary
- 5-way 1-shot Accuracy: 50.88% ± 11.16%
- 5-way 5-shot Accuracy: 67.40% ± 11.92%

## Notes
- All models trained on Mini-ImageNet
- Evaluation done over 100 episodes
- ResNet used 96×96 input, MobileNet used 64×64

# Wavelet-based Image Compression Results

## Standard Classification (ResNet18)
### Retaining 10.0% Coefficients
- Accuracy (Mean ± Std): 0.0123 ± 0.0527
- PSNR: 19.93 dB
- Compression Ratio: 9.98

### Retaining 25.0% Coefficients
- Accuracy (Mean ± Std): 0.0149 ± 0.0621
- PSNR: 26.93 dB
- Compression Ratio: 3.99

### Retaining 50.0% Coefficients
- Accuracy (Mean ± Std): 0.0144 ± 0.0588
- PSNR: 36.15 dB
- Compression Ratio: 2.00

## Standard Classification (MobileNetV2)
### Retaining 10.0% Coefficients
- Accuracy (Mean ± Std): 0.0223 ± 0.0921
- PSNR: 19.93 dB
- Compression Ratio: 9.98

### Retaining 25.0% Coefficients
- Accuracy (Mean ± Std): 0.0163 ± 0.0632
- PSNR: 26.93 dB

### Retaining 50.0% Coefficients
- Accuracy (Mean ± Std): 0.0139 ± 0.0543
- PSNR: 36.15 dB
- Compression Ratio: 2.00
#  Fine-Tuning MobileNetV2 on Compressed Data
## Overview
Fine-tunes MobileNetV2 on Mini-ImageNet using wavelet compression, evaluating performance on compressed and uncompressed data.
## Code Structure
- **Imports**: PyTorch, torchvision, wavelet compression libraries.
- **Wavelet Compression**: Applies 25% compression via `apply_wavelet_compression`.
- **Model**: Modifies MobileNetV2 classifier (1280 features).
- **Data**: Loads Mini-ImageNet (resize 96x96, normalize).
- **Training**: 10 epochs, SGD, CrossEntropyLoss on compressed data.
- **Evaluation**: Tests on uncompressed and compressed validation data.
- ## Usage
1. Set dataset path (`data_dir`).
2. Run:
   ```bash
   python script_name.py
   ```
3. Model saved as `compressed_trained.pth`.
4. Prints accuracy for uncompressed/compressed data.

## Results
- Uncompressed Accuracy: 0.37%
- Compressed Accuracy (25%): 1%

- # Compressed Sensing and Coherence Analysis
- ## Overview
This project implements compressed sensing (CS) on images using wavelet transforms and evaluates sensing matrix coherence. It applies Heuristic, IHT, and ISTA reconstruction methods at sampling rates of 25%, 50%, and 75%, and analyzes matrix coherence for Gaussian, Bernoulli, Fourier, and Structured matrices.
## Code Structure
- **Image Processing**: Loads and preprocesses a 128x128 grayscale image, applies Haar wavelet transform (level 3), and creates a sparse approximation (10% sparsity).
- **CS Reconstruction**:
  - **Heuristic**: Uses Gaussian filtering on random samples.
  - **IHT**: Iterative Hard Thresholding with 100 iterations.
  - **ISTA**: Iterative Soft Thresholding with dynamic lambda.
- **Metrics**: Computes Relative Error, PSNR, and SSIM for each method at different sampling rates.
- **Coherence Analysis**: Evaluates coherence and reconstruction error for Gaussian, Bernoulli, Fourier, and Structured matrices using Orthogonal Matching Pursuit (OMP).
- ## Results
- **Reconstruction (128x128 Image, k=1638)**:
  - **25% Sampling**: IHT (Rel Error: 0.2982, PSNR: 12.95 dB), ISTA (Rel Error: 0.4257, PSNR: 9.86 dB)
  - **50% Sampling**: IHT (Rel Error: 0.0672, PSNR: 25.90 dB), ISTA (Rel Error: 0.0634, PSNR: 26.39 dB)
  - **75% Sampling**: IHT (Rel Error: 0.0550, PSNR: 27.63 dB), ISTA (Rel Error: 0.0314, PSNR: 32.51 dB)
- **Coherence Analysis (N=200, M=100, k=10)**:
  - Gaussian: Coherence 0.4568, Error 0.0714
  - Bernoulli: Coherence 0.3800, Error 0.0544
  - Fourier: Coherence 0.2523, Error 0.0460
  - Structured: Error 0.3476
  - Welch Bound: 0.0709
