# Interpretable Lung and Colon Cancer Diagnosis using Vision Models, Grad-CAM and LLMs

## About the Project

This MSc Computer Science project explores interpretable multi-class classification of lung and colon histopathology images. The aim was not only to classify tissue images, but also to make model outputs easier to understand by combining visual explanations from Grad-CAM with short language-based explanations.

The workflow compares multiple deep-learning approaches under a common experimental pipeline, including DenseNet121, a Vision Transformer (ViT-Base), and a hybrid DenseFormer-Histo model.

> **Important:** This is an academic decision-support project and is not intended to provide medical diagnoses or replace qualified medical professionals.

## Dataset

The project uses the **Lung and Colon Cancer Histopathological Images (LC25000)** dataset. It contains 25,000 augmented histopathology images across five balanced classes representing benign and malignant lung and colon tissue.

Dataset source: Kaggle — *Lung and Colon Cancer Histopathological Images* by Andrew MVD.

The dataset is not included in this repository. The notebook currently uses Kaggle-style dataset paths, so those paths may need to be updated when running in another environment.

## Project Workflow

The notebook covers:

- dataset exploration and preparation
- image preprocessing, including resizing and image enhancement/normalisation steps
- training and evaluation of DenseNet121
- training and evaluation of ViT-Base
- development and evaluation of the DenseFormer-Histo model
- classification metrics and visual evaluation
- Grad-CAM visual explanations
- conversion of Grad-CAM statistics into interpretable descriptors
- LLM-generated explanations based on the predicted class, confidence score and Grad-CAM descriptors

## Models and Reported Results

The final notebook reports the following classification accuracies:

| Model | Accuracy |
| --- | ---: |
| DenseFormer-Histo | 98.64% |
| DenseNet121 | 96.80% |
| ViT-Base | 95.60% |

These results are from the experimental setup recorded in the notebook and should be interpreted in the context of the augmented LC25000 dataset rather than as evidence of clinical performance.

## Explainability Pipeline

For the selected DenseFormer-Histo model, Grad-CAM is used to generate a heatmap showing image regions that influenced a prediction. The notebook then analyses the heatmap and converts simple attention statistics into descriptors. These structured outputs are passed to an LLM to generate a short, conservative explanation.

The LLM prompt is explicitly instructed not to provide a medical diagnosis and to frame the output as decision support.

## Technologies

- Python
- TensorFlow / Keras
- PyTorch
- Torchvision
- Hugging Face Transformers
- OpenCV
- Scikit-learn
- NumPy and Pandas
- Matplotlib and Seaborn
- Grad-CAM
- OpenAI API

## Running the Notebook

Install the dependencies:

```bash
pip install -r requirements.txt
```

The notebook was developed with Kaggle-style input paths. Download the LC25000 dataset separately and update the paths if you run the notebook locally.

For the optional LLM explanation stage, provide the API key through an environment variable rather than writing a key into the notebook:

```bash
export OPENAI_API_KEY="your-key"
```

On Windows PowerShell:

```powershell
$env:OPENAI_API_KEY="your-key"
```

Do not commit API keys to GitHub.

## Repository Files

- `cancer_diagnosis_analysis.ipynb` — cleaned project notebook
- `requirements.txt` — Python dependencies
- `.gitignore` — excludes datasets, model weights, secrets and temporary files

## Limitations

The dataset consists of augmented histopathology images, so high experimental accuracy should not be interpreted as clinical validation. The Grad-CAM descriptors and LLM explanations are intended to improve transparency of model outputs, not to establish a diagnosis.

## Project Context

This project was completed as part of an MSc Computer Science research project focused on interpretable AI for histopathological image classification.
