MobileNetV2_AdaBoost_Seed_2
===========================

CONTENTS
--------
splits/split_indices.json
    Exact train/validation indices, image paths, seed and class mapping.
splits/split_images.csv
    Train/validation image manifest with class names.
models/mobilenetv2_final_weights_seed2.pth
    Final trained MobileNetV2 weights + inference settings.
models/adaboost_final_seed2.joblib
    Trained AdaBoost classifier (on MobileNetV2 features).
models/Mobilenet_seed2.pkl
    Best-validation training checkpoint.
config/model_config.json
    Architecture, preprocessing and training configuration.
metadata/environment.json
    Python, library, platform and CUDA information.
metadata/train_dataset_manifest.csv, metadata/test_dataset_manifest.csv
    Dataset file paths, sizes and SHA-256 hashes.
metadata/artifact_sha256.json
    SHA-256 hashes of every file in this seed folder.

REPRODUCTION NOTES
------------------
1. Use the same dataset version, image files and labels (verify with the manifests).
2. Restore the saved train/validation split; do not create a new split.
3. Preserve ImageFolder class ordering and preprocessing.
4. Load the saved models for inference, or re-run the training notebook with this seed.
5. A matching seed alone does not guarantee bit-identical results across hardware
   or software versions.

IMPORTANT
---------
The dataset images and the training notebook are not included.
Absolute paths refer to the original Kaggle environment.
Metrics/result files are NOT included in this package.
