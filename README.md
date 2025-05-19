This is the README for the second project.

# Wavelet-based Image Compression Results

## Standard Classification (ResNet18)
### Retaining 10.0% Coefficients
- Accuracy (Mean � Std): 0.0123 � 0.0527
- PSNR: 19.93 dB
- Compression Ratio: 9.98

### Retaining 25.0% Coefficients
- Accuracy (Mean � Std): 0.0149 � 0.0621
- PSNR: 26.93 dB
- Compression Ratio: 3.99

### Retaining 50.0% Coefficients
- Accuracy (Mean � Std): 0.0144 � 0.0588
- PSNR: 36.15 dB
- Compression Ratio: 2.00

## Standard Classification (MobileNetV2)
### Retaining 10.0% Coefficients
- Accuracy (Mean � Std): 0.0223 � 0.0921
- PSNR: 19.93 dB
- Compression Ratio: 9.98

### Retaining 25.0% Coefficients
- Accuracy (Mean � Std): 0.0163 � 0.0632
- PSNR: 26.93 dB

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
- Compression Ratio: 3.99

### Retaining 50.0% Coefficients
- Accuracy (Mean � Std): 0.0139 � 0.0543
- PSNR: 36.15 dB
- Compression Ratio: 2.00
