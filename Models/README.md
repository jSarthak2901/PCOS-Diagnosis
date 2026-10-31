# Models

This folder contains all model experiments for PCOS ultrasound image classification (classes: **Appears abnormal** / **Appears normal**). The experiments are split into two folders according to whether their results can be reproduced.

```
Models/
├── Reproducible/        # 3-seed experiments (fixed seeds, saved splits/weights, mean ± SD reported)
├── Non-Reproducible/    # single-run exploratory experiments
└── README.md
```

## Dataset

This project uses the PCOSGen ultrasound image datasets available on Zenodo.

- **Training Dataset:** PCOSGen-train dataset — 3,200 ultrasound images. https://zenodo.org/records/14592001
- **Testing Dataset:** PCOSGen-test dataset — 1,468 ultrasound images. https://zenodo.org/records/14591782

Both datasets provide ultrasound images with normal/abnormal classifications. Please download the **updated dataset versions** from the links above.

The test set contains 1,052 *Appears abnormal* and 416 *Appears normal* images. The 3,200 training images are split 85/15 into 2,720 training and 480 validation images; the test set is used only for the final evaluation.

## Reproducible

Experiments run with a fixed, documented protocol on **three seeds: 2622715460, 512 and 2**. The architecture and training settings are identical across seeds. Results are reported per seed and as mean ± SD (sample SD, n = 3). The seed-fixed runs were re-obtained with identical numbers in separate single-seed runs (MobileNetV2 and EfficientNet-B0 with seed 2622715460, EfficientNet-B3 with seed 512), and the split, weights and classifier are saved per seed for re-use.

| Model | Classifier | Seed 2622715460 | Seed 512 | Seed 2 | Mean ± SD |
|---|---|---|---|---|---|
| MobileNetV2 | AdaBoost | **94.01** | 89.99 | 91.14 | 91.71 ± 2.07 |
| MobileNetV2 | Direct (fine-tuned CNN) | **92.44** | 85.83 | 88.62 | 88.96 ± 3.32 |
| EfficientNet-B3 | AdaBoost | 91.35 | **92.71** | 91.08 | 91.71 ± 0.88 |
| EfficientNet-B3 | Direct (fine-tuned CNN) | **90.05** | 87.60 | 89.71 | 89.12 ± 1.33 |
| EfficientNet-B0 | AdaBoost | **92.64** | 91.83 | 91.76 | 92.08 ± 0.49 |
| EfficientNet-B0 | Direct (fine-tuned CNN) | 89.03 | **89.58** | 88.42 | 89.01 ± 0.58 |

Values are test accuracy (%). Bold = best seed.

**Protocol**

- Backbone: ImageNet-pretrained CNN fine-tuned end to end.
- Loss: 0.5 × Cross-Entropy + 0.5 × Dice loss; optimizer Adam (lr = 0.001); WeightedRandomSampler for class balance.
- Training: up to 50 epochs, early stopping on validation accuracy (patience 8).
- AdaBoost: trained on the global-average-pooled features of the fine-tuned network.
- Seeding: Python `random`, NumPy, PyTorch (CPU and CUDA) and `cudnn.deterministic = True`; scikit-learn `random_state` set to the seed.
- Validation images use the training augmentations, so validation accuracy is lower and noisier than test accuracy.

## Non-Reproducible

Single-run **exploratory** experiments, kept for comparison. They were run once, without a fixed seed controlling network training (only scikit-learn `random_state = 42` is set), or, for the MiT-B2 notebooks, with seed 42 but no repeat run or saved artefacts. Their exact numbers should not be expected to reproduce.

They cover:

- Networks: AlexNet, VGG16, ResNet18, MobileNetV2, InceptionV3, EfficientNet-B3 and MiT-B2 (with FPN or MobileNetV2 features).
- Classifiers on extracted features: Random Forest, KNN, Gaussian Naive Bayes, AdaBoost, XGBoost and SVM.
- Direct classification with the fine-tuned CNN, with Dice-loss baselines and 5-fold cross-validation runs.

## Related Resources & Work

- **Anagha Kaggle Dataset:** PCOS Detection Using Ultrasound Images https://www.kaggle.com/datasets/anaghachoudhari/pcos-detection-using-ultrasound-images
- **Kaggle Notebook — Anagha Dataset:** https://www.kaggle.com/code/jshanky/anagha-dataset
- **Kaggle Notebook — PCOS-Zenodo:** https://www.kaggle.com/code/jshanky/pcos-zenodo
