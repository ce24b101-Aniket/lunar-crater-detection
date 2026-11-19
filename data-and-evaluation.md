# Data and evaluation notes

## Dataset

The training notebook identifies the dataset as `nasa-ibm-ai4science/Sombench-NAC-Crater-Detection`. It discovers the split annotation JSONs and source images at runtime, applies a single crater class, and converts COCO-style boxes to YOLO centre-width-height labels. Raw data and annotations are not committed here; obtain the dataset from its upstream repository and follow its license/terms.

The notebook's documented split procedure and outputs should be consulted for sample counts and any geographic/site grouping. Do not infer independent geographic generalization from the split name alone.

## Preprocessing and training

The documented controlled run starts from public `yolo11n.pt`, uses 640 px model input, AdamW, initial learning rate 0.001, weight decay 0.0005, and up to 100 epochs with patience 15. Training tiles are 256 px and are contrast-stretched per tile using valid pixels' 2nd and 98th percentiles. See `results/training_args.yaml` and `results/reproducibility.json` for the recorded configuration.

## Held-out evaluation

The selected confidence threshold (0.55) is stated to be selected on validation. A detection is matched one-to-one to a labelled crater when its centre is within half the labelled diameter and its relative diameter error is at most 50%. Ground-truth craters under 10 m are ignored; detections matching those ignored labels are not counted as false positives.

The archived test summary reports 46 images, TP=678, FP=58, FN=903, precision=0.9212, recall=0.4288, and F1=0.5852. This is a custom crater-specific metric, not YOLO mAP. The report should be cited with this protocol and threshold; do not compare it directly with studies that use different matching rules or datasets.

`baseline_vs_finetuned_validation.csv` reports a separate validation comparison. It is not the held-out test comparison and must be labelled accordingly.

## Reproducibility cautions

- The notebook includes exploratory/optional fine-tuning sections. Preserve the frozen primary test result when experimenting further.
- The submitted outputs archive includes numerous intermediate files and dataset-cache material; only selected compact run artifacts are tracked here.
- Record the exact dataset revision, code revision, environment, hardware, and checkpoint hash in future runs.
