
This is the code for the LiBERTy Model. If you use this code, please cite our paper:

@inproceedings {susladkar2023LiBERTy,

 title            = {{LiBERTy: A Novel Model for Natural Language Understanding}},
	
 year             = "2023",
	
 author           = "Onkar Susladkar and Gayatri Deshmukh and R Sai Chandra Teja and Sparsh Mittal and Rekha Singhal",
	
 booktitle        = "International Conference on AI-ML Systems (AIMLSystems) ",
	
 address          = "Bengaluru, India",
	
 publisher        = "ACM",
 
 }

Basically speaking, BERT and BiLSTM are the two approaches to solving the task. The final result shows that Double Layer BiLSTM is 
our best choice.

> Datasets are provided in the data folder for reproduction

Use `pip install -r requirements.txt` to install the packages needed. We've tested this repository under Python 3.6 and Ubuntu 22.04

## 0. Some non-functional codes:

`evaluate.py` : Sample code provided for evaluating the output and results.


## 1. BERT Classification 
By fine-tuning the pretrained BERT model from `HuggingFace`, I embedded all the words and
use the provided BERT classification model to do the named entity recognition on the test set. Details can be found at: https://huggingface.co/transformers/model_doc/bert.html

The models are saved at the `./models/` and the results are saved at `./results/`

**The best results achieved is 89.3% on the validation set.** This is probably because there are some domain knowledge and BERT can't treat them well.

Codes related are provided below, to reproduce, please follow this sequence:


`BERT_finetuning.py` **(This code is deprecated by `BERT_revised.py`)**: code for fine-tuning the BERT model with the old version of `BertTokenizer`, which `tokenize` and `convert_token_to_id` is used, followed by classification.

`BERT_revised.py` : code for fine-tuning the BERT model with `transformer 3.4.0`, where`BertTokenizer.encode` is used, followed by a classification.

`BERT_find_best_model.py` : code for finding the best model according to the validation accuracy.

`BERT_loss_visualization.py` : visualizing the training/validation loss/accuracy for all the models.

`BERT_predict_verify.py`: code for generating result on the test data and verify the result by checking the generation's length.


### 3. Glove Update
---
We've added the Glove downloading part into the LSTM_NER.py code and now the code can automatically download all the glove pretrained model.

User can pass a parameter of how many billion words is the glove pretrained on to decide which glove model to use.



