# Results as reported in the paper
Values are copied from the final run and rounded as in the paper. Full-precision CSV files are written by the notebook to `MyDrive/dacl10k_project/tables/`.

**table01_classes.csv** (Table 1). The 19 dacl10k classes: dataset label, name used in this paper, group, number of official training and test images containing the class, number of polygons in both splits and approximate share of image area in the training split.

**table02_models.csv** (Table 2). Model configurations. Trainable parameters exclude frozen backbone weights.

**table03_accuracy.csv** (Table 3). Segmentation accuracy (mIoU; mean ± standard deviation over 3 seeds). Per-class thresholds were tuned on the internal validation split. The leakage-free test set excludes test images with a near-duplicate in the training data.

**table04_per_class_iou.csv** (Table 4). Per-class test IoU (mean over 3 seeds). The best value in each row is shown in bold.

**table05_bootstrap.csv** (Table 5). Paired bootstrap comparisons of test mIoU: each model against the replicated baseline FPN (EfficientNet-B4), and the best model on validation (DINOv2-B + LoRA) against each other model (5,000 resamples of test images, percentile 95% confidence intervals; mean over 3 seeds). ΔmIoU is the first model minus the second. P-values are Holm-adjusted within each test subset. The resampling covers test-image variability only, not training randomness.

**table06_calibration.csv** (Table 6). Calibration of the uncertainty methods on the test set, DINOv2-B + LoRA (seed 0; the deep ensemble combines seeds 0, 1 and 2). ECE = expected calibration error (15 bins); ECE (active) is restricted to pixels that are labelled positive or predicted with p ≥ 0.05; NLL = negative log-likelihood. Lower is better for all calibration metrics.

**table07_error_review.csv** (Table 7). Uncertainty-guided error review, DINOv2-B + LoRA (seed 0; the deep ensemble combines seeds 0, 1 and 2). AURC = area under the risk–coverage curve (lower is better); the other columns give the share of pixel errors found when reviewing the most uncertain 5%, 10% or 20% of pixels.

**table08_explanation_faithfulness.csv** (Table 8). Faithfulness of the explanation methods over 40 test images, DINOv2-B + LoRA (seed 0). Values are mean ± standard deviation. Deletion AUC: lower is better; insertion AUC: higher is better; rank correlation with a randomised model: lower is better. P-values: one-sided Wilcoxon signed-rank test against the random baseline.

**table09_robustness.csv** (Table 9). Test mIoU and mean uncertainty (MC dropout) under image corruption, DINOv2-B + LoRA (seed 0), on 300 test images.

**tableS1_splits.csv** (Table S1). Data splits used in this study. The near-duplicate audit found 6 image pairs with a perceptual-hash Hamming distance of at most 8 between the official training and validation splits.

**tableS2_temperatures.csv** (Table S2). Fitted per-class temperatures, DINOv2-B + LoRA (seed 0; the deep ensemble combines seeds 0, 1 and 2). T > 1 means that the method was over-confident for the class and T < 1 that it was under-confident. The fallback of T = 1 for classes with fewer than 20 positive pixels was not needed for any class.

**tableS3_xai_leakage_by_class.csv** (Table S3). Off-target attribution leakage by target class (share of positive attribution outside the explained region), DINOv2-B + LoRA (seed 0).

**tableS4_training_length.csv** (Table S4). Effect of training length, DINOv2-B (full fine-tuning), seed 2: the 30-epoch protocol used for all models against a 60-epoch schedule without early stopping. The last row gives the paired bootstrap difference (5,000 resamples of test images) with its 95% confidence interval. For comparison, the seed-to-seed standard deviation of test mIoU is 0.041 (3 seeds).
