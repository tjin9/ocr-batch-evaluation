# OCR Batch Evaluation with Tesseract

A learning project exploring how Optical Character Recognition (OCR) performs 
on real-world images, and how basic image preprocessing techniques affect accuracy.

This project is part of my self-learning journey into OCR technology.

## Overview

This project evaluates Tesseract OCR's accuracy on a batch of 30 real-world 
images, each paired with a ground truth (correct) text label. It compares 
three different strategies:

1. **No preprocessing** — running Tesseract directly on the raw images
2. **Global thresholding (OTSU)** applied to all images
3. **Adaptive thresholding** applied to all images
4. **Selective preprocessing** — only applying preprocessing to images that 
   fail on the first attempt



## Results

| Strategy | Accuracy |
|---|---|
| Baseline (no preprocessing) | 60.0% |
| Global thresholding (OTSU) — all images | 46.7% |
| Adaptive thresholding — all images | 36.7% |
| **Selective preprocessing (final)** | **63.3%** |

## Key Findings

- Preprocessing is **not universally helpful**. Applying adaptive thresholding 
  to every image actually *lowered* accuracy (60% → 36.7%), because images 
  that already worked well with raw OCR were negatively affected.
- A **selective approach** — only preprocessing images that initially fail — 
  gave the best overall result (63.3%).
- Some images remain unsolved even after preprocessing. See 
  `exploration_hard_case.ipynb` for a detailed case study on one such image 
  (`4_test.jpg`), which shows text on a crumpled paper against a visually 
  complex wooden background with decorative arrows — a genuine hard case 
  for traditional OCR tools.


 ## Project Structure

```text
├── ocr_batch_evaluation.ipynb      # Main pipeline: baseline, preprocessing, comparison
├── exploration_hard_case.ipynb     # Deep dive into a single hard-to-read image
├── Test_images/                    # Directory containing 30 test images
├── Image name and annotation.csv   # Ground truth labels
├── requirements.txt
└── README.md
```
## Tech Stack

- **Tesseract OCR** (via `pytesseract`) — text extraction
- **OpenCV** — image preprocessing (thresholding)
- **Pandas** — data handling and evaluation
- **Matplotlib** — visualizing preprocessing results

## How to Run

1. Install [Tesseract OCR](https://github.com/UB-Mannheim/tesseract/wiki) on your machine
2. Update the `tesseract_cmd` path in the notebook to match your installation
3. Install Python dependencies: pip install -r requirements.txt
4. Run `ocr_batch_evaluation.ipynb`

## Dataset

[Textual images for OCR performance evaluation (TIOCR)](https://www.kaggle.com/datasets/shreyaspj/tiocr) from Kaggle.

## Author

Tasneem (tjin9) — built as part of my self-learning journey into OCR and 
Computer Vision, alongside my broader path in Data Science & AI.
