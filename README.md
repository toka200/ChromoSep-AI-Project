# ChromoSep-AI

ChromoSep-AI is an attention-guided UNet++ framework for semantic segmentation of overlapping chromosomes.  
The model predicts four pixel-level classes: background, chromosome 1, chromosome 2, and overlap region.

## Repository structure

```text
ChromoSep-AI/
├── README.md
├── requirements.txt
├── LICENSE
├── .gitignore
├── configs/
│   └── chromosep_config.yaml
├── src/
│   ├── data.py
│   ├── model.py
│   ├── losses.py
│   ├── metrics.py
│   ├── train.py
│   ├── evaluate.py
│   └── inference.py
├── notebooks/
│   └── karyo-project3.ipynb
├── figures/
│   ├── dataset_sample.png
│   ├── class_distribution.png
│   ├── preprocessing_visualization.png
│   ├── methodology_pipeline.png
│   ├── confusion_matrix_testset.png
│   ├── per_class_metrics.png
│   └── final_results.png
└── saved_models/
    └── README.md
```

## Dataset

This work uses the public Overlapping Chromosomes / DeepFish dataset by Jean-Patrick Pommier on Kaggle.

Dataset link: https://www.kaggle.com/jeanpat/overlapping-chromosomes

Do not upload the dataset directly to this repository. After downloading it from Kaggle, place it locally in:

```text
data/
└── overlapping_chromosomes/
```

## Model

The final model is an Attention-Guided UNet++ architecture trained with a Triple Hybrid Loss:

```text
Total Loss = 0.3 Weighted Cross-Entropy + 0.3 Dice Loss + 0.4 Lovasz-Softmax Loss
```

## Reported performance

| Metric | Value |
|---|---:|
| Pixel Accuracy | 99.47% |
| Mean IoU | 89.14% |
| Mean Dice | 94.26% |
| Overlap IoU | 85.33% |
| Overlap Sensitivity | 97.00% |
| Specificity | 99.83% |
| Overlap F1-score | 92.00% |
| Inference Time | 70 ms/image |
| Parameters | 8.64M |

## Installation

```bash
git clone https://github.com/toka200/ChromoSep-AI-Project.git
cd ChromoSep-AI
pip install -r requirements.txt
```

## Training

```bash
python src/train.py --config configs/chromosep_config.yaml
```

## Evaluation

```bash
python src/evaluate.py --config configs/chromosep_config.yaml --checkpoint saved_models/best_model.pth
```

## Citation

```bibtex
@article{alzoubi2026chromosep,
  title={ChromoSep-AI: Shape-Aware Segmentation of Overlapping Chromosomes},
  author={Alzoubi, Tuqa and Sonbol, Riad and Alsohle, Wesam},
  journal={Manuscript submitted for publication},
  year={2026}
}
```

## License

Add a suitable license before public release. MIT is commonly used for code, but confirm with your supervisor before submission.
