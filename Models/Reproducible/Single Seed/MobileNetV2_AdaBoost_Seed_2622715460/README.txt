MobileNetV2_AdaBoost_Seed_2622715460
====================================

CONTENTS
--------
splits/split_indices.json
    Saved train/validation indices, paths, seed and class mapping.

splits/split_images.csv
    Split name, dataset index, image name, full path and class.

models/mobilenetv2_final_weights.pth
    Trained MobileNetV2 weights and configuration.

models/adaboost_final.joblib
    Trained AdaBoost classifier.

models/best_mobilenet_checkpoint.pkl
    Best validation checkpoint, if available.

config/model_config.json
    Model architecture, preprocessing and training configuration.

metadata/environment.json
    Software and hardware information.

metadata/train_dataset_manifest.csv
metadata/test_dataset_manifest.csv
    Dataset file names, sizes and SHA-256 hashes.

REPRODUCTION
------------
1. Obtain the same dataset version and labels.
2. Verify dataset files using the SHA-256 manifests.
3. Restore the exact saved train/validation indices.
4. Preserve ImageFolder class ordering and preprocessing.
5. Load the saved models for inference.
6. Use the original training notebook to retrain the models.

IMPORTANT
---------
The dataset and notebook are not included in this ZIP.
Image paths refer to the original Kaggle runtime.
The notebook contains the experiment results separately.
Matching seeds alone do not guarantee bit-for-bit identical
results across different hardware and software versions.
