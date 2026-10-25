PCOS EfficientNet-B3 + AdaBoost — Seed 512
=============================================

CONTENTS
--------
models/efficientnet_b3_best_seed512.pth
    Best EfficientNet-B3 model state and associated configuration.

models/adaboost_efficientnet_b3_seed512.joblib
    Trained AdaBoost classifier.

splits/split_indices.json
    Train/validation indices and class mapping.

splits/split_images.csv
    Image paths, names, classes, and split membership.

config/model_config.json
    Model and training configuration.

metadata/environment.json
    Python, library, and hardware information.

IMPORTANT
---------
1. The dataset and complete training notebook are not included.
2. Dataset paths refer to the original Kaggle environment.
3. Split indices require the same dataset contents and file ordering.
4. A seed alone does not guarantee identical results across hardware
   or software environments.
5. The metrics describe this run; they do not independently establish
   clinical validity or generalization.
