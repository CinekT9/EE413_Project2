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