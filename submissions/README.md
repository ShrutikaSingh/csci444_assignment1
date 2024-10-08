
# Sentiment Analysis with Naive Bayes

## Overview
This project implements a Naive Bayes classifier for sentiment analysis using a custom tokenizer and binary vector representation of text for IMDB Dataset. 

## Folder structure with Description
The following is the folder structure of the project along with descriptions for each file:

(venv) 206819985@OTS-FVFHK1DWQ05Q-MAC submissions % tree

- **K1000_main.py**  
  This is Naive Bayes Code with vocab size = 1000

- **README.md**  
  Contains details for the main assignment

- **Shrutika_CSCI444_1_MAIN_REPORT (1).pdf**  
  This is the report for main assignment of Naive Bayes Contatining Answers for Section: Tokenizer, Results, and Naive Bayes

- **main.py**  
  This is the main code for Naive Bayes with vocab size = 10000

- **requirements.txt**  
  This file lists the libraries required for the main homework. (Bonus requirement file is separate in the Bonus Folder)

- **test_paths.csv**  
  Contains paths to test files.

- **test_predictions.csv**  
  Generated `test_predictions.csv` with headers as `review,sentiment`. Rows look like this: `./test/354863.txt,0`

- **train_labels.csv**  
  Contains training labels.

- **val_labels.csv**  
  Contains validation labels.

- **val_predictions.csv**  
  Generated `val_predictions.csv` with headers as `review,sentiment`. Rows look like this: `./val/597852.txt,1`


## RUNNING THE CODE

###  Step 1
cd into sumbmission folder

> (venv) 206819985@OTS-FVFHK1DWQ05Q-MAC submissions % pwd
      /Users/206819985/Documents/csci_444_assign/hw1-imdb/submissions

### Step 2
Copy the name of folder where your test, train and val data is located

In my case it is located at : 
> /Users/206819985/Documents/csci_444_assign/hw1-imdb


## For Vocab Size = 10000

### Step 3
Run the following command
> python main.py --data_src <PATH_OF_DATA_FOLDER>

IN MY Case
>python3 main.py --data_src /Users/206819985/Documents/csci_444_assign/hw1-imdb


### Step 4
OUTPUT

<img width="968" alt="image" src="https://github.com/user-attachments/assets/b07a4e65-80d0-4b7e-8dd0-9107b8fbc769">


## For Vocal Size = 1000
> python K1000_main.py --data_src <PATH_OF_DATA_FOLDER>

In My Case, the command was like this :
> python3 K1000_main.py --data_src /Users/206819985/Documents/csci_444_assign/hw1-imdb

<img width="1012" alt="image" src="https://github.com/user-attachments/assets/623fd155-b310-4f9c-b5c6-f52c7b73dd40">


### FORMULAE USED FOR RESULTS

    accuracy = (true_positives + true_negatives) / (true_positives+false_negatives+false_positives+true_negatives)
    precision = true_positives / (true_positives + false_positives)
    recall = true_positives / (true_positives + false_negatives)
    f1 = 2 * (precision * recall) / (precision + recall)
    

## Other Accuracy

### Evaluarion Metrices After Removing Stop Words (vocab length = 10000)

> (venv) 206819985@OTS-FVFHK1DWQ05Q-MAC hw1-imdb % python3 main.py --data_src /Users/206819985/Documents/csci_444_assign/hw1-imdb

Validation Accuracy: 0.8552

Validation Precision: 0.8636

Validation Recall: 0.8435

Validation F1: 0.8534


### Evaluation Metrices when Important words like Not, Nor ETC Have not been Removed (vocab length = 10000)

Validation Accuracy: 0.8570

Validation Precision: 0.8653

Validation Recall: 0.8455

Validation F1: 0.8553

My Observations for Evaluation Metrices:
<img width="1476" alt="image" src="https://github.com/user-attachments/assets/6a8ef228-10ef-4a53-9c0b-fc120e6bc55b">


## Implementation

### 1. Tokenizer Class
- **Function:** Converts text to lowercase, tokenizes it into words, and removes common stop words to retain only meaningful terms.

### 2. Vocabulary Building
- **Approach:** Constructs a vocabulary of the most frequent words from the training texts, limited by a specified size (`vocab_size`) to balance detail and manageability.

### 3. Binary Vector Representation
- **Purpose:** Transforms text into binary vectors where each element indicates the presence or absence of a word from the vocabulary, simplifying the input for the Naive Bayes model.

### 4. Naive Bayes Classifier
- **Training:** Computes prior probabilities for each sentiment class and estimates conditional word probabilities, applying Laplace smoothing to handle unseen words and prevent zero probabilities.

### 5. Model Evaluation
- **Metrics:** Evaluates model performance using accuracy, precision, recall, and F1-score on the validation dataset to measure its effectiveness in sentiment classification.

### 6. Implementation Choices
- **Stop Words Removal:** Filters out common stop words to reduce noise and focus on more meaningful terms in the texts.
- **Vocabulary Size:** Limits vocabulary to manage computational complexity and retain only the most relevant terms for classification.

## Usage
1. **Prepare Data:** Ensure your data is organized into `train`, `val`, and `test` splits with text and labels.
2. **Run the Model:**
   ```bash python main.py --data_src <PATH_to_DATA_FOLDER> ```

## Steps Followed:

Loads the training, validation, and test data.

Trains a Naive Bayes model on the training data.

Evaluates the model on the validation set and prints the accuracy, precision, recall, and F1 score.

Saves the validation and test predictions to CSV files.
