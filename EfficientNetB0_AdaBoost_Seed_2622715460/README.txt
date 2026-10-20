EfficientNetB0_AdaBoost_Seed_2622715460
=======================================

CONTENTS
--------
splits/split_indices.json
    Saved train/validation indices, image paths, seed and classes.

splits/split_images.csv
    Split, index, image name, image path and class name.

models/efficientnet_b0_final_weights.pth
    Trained EfficientNet-B0 weights and configuration.

models/adaboost_efficientnet_final.joblib
    Trained AdaBoost classifier.

models/best_efficientnet_b0_checkpoint.pkl
    Best validation checkpoint, if available.

config/model_config.json
    Model, preprocessing and training configuration.

metadata/environment.json
    Python, library, platform and CUDA information.

metadata/train_dataset_manifest.csv
metadata/test_dataset_manifest.csv
    Dataset paths, file sizes and SHA-256 hashes.

REPRODUCTION
------------
1. Obtain the same dataset version and labels.
2. Verify the dataset files using the SHA-256 manifests.
3. Restore the saved train/validation split.
4. Preserve ImageFolder class ordering and preprocessing.
5. Load the saved models for inference.
6. Use the original notebook and dataset to retrain the models.

IMPORTANT
---------
The dataset and complete training notebook are not included.
Absolute paths refer to the original Kaggle environment.
The notebook stores the evaluation results separately.
A matching seed alone does not guarantee identical results
across different hardware or software versions.
