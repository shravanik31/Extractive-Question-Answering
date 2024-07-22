# Extractive Question Answering

## Project Overview
This project develops a model that ingests a text paragraph and a related question, then extracts the answer directly from the text. The main goal is to create a robust system capable of understanding and processing natural language queries accurately.

## Dataset
The Spoken Question Answering Dataset (SQuAD) is employed here, which includes 37,111 records. Each record features a context paragraph from which questions are derived and the corresponding answers are located. The dataset can be found in the Dataset folder of this repository.

## Model
The model used is the `distilbert-base-uncased` from Hugging Face, a compact and efficient version of BERT designed for faster processing with substantial accuracy. DistilBERT leverages a transformer-based architecture pre-trained on a vast corpus via a self-supervised learning method, specifically Masked Language Modeling (MLM).

## Data Preprocessing
Data preprocessing involves tokenization using the `DistilBertTokenizerFast`, converting text into manageable tokens for model processing. This stage ensures proper alignment of answers within the context by marking start and end positions, crucial for effective training. Additionally, normalization standardizes answers for consistent model evaluation.

## Training Details
- **Epochs**: 6
- **Learning Rate**: 2e-5
- **Optimizer**: Adam
- **Loss Function**: Focal Loss

The training process involves monitoring loss and accuracy, concluding with the computation of average metrics across batches and saving the optimized model and tokenizer.

## Testing
Model performance is evaluated using F1 and Word Error Rate (WER) scores on a test dataset. For testing:
- Train the model using scripts provided in the repository.
- Download pre-trained model components from [this link](https://drive.google.com/drive/folders/1sUOgLMbHMRywD9z7zNbwUufMfnBTSZWt?usp=sharing) and evaluate by specifying paths to your dataset.

## Results
The base model and its enhancements have been tested under various noise conditions:
- **Base Model Performance (No Noise)**: F1 Score of 0.6306, WER of 1.2447
- **Improved Model with Doc Stride and Learning Rate Decay**: Enhanced F1 scores across noise scenarios, highlighting the effective fine-tuning of the model.

## Improvements
- **Doc Stride**: Set to 128 to manage overlap in long documents, enhancing answer detection accuracy.
- **Learning Rate Decay**: Implemented using ExponentialLR (rate: 2e-2), allowing finer parameter adjustments and improving model response under noisy conditions.

## Observations
Significant enhancements were observed with the `deepset/bert-base-cased-squad2` model, showing the highest F1 score and the lowest WER in noise-free tests, demonstrating the potential for advanced pre-trained models in this application.

For more detailed visual results and training plots, refer to the report.
