# RNN-Password-Generator

![](imgs/icon.jpg)

## Aim of the project:
The project shall generate password predictions based on a real-world password dataset. The output can be used to attack web accounts (Black hat). However, it can be also used to detect weak passwords (white hat).



## Dataset:
The dataset must contain a large set of passwords, favorably be relative to the required system. For instance, phone passwords tend to be shorter than social media passwords. In this project, we are using real WPA wifi passwords. The dataset is provided courtesy of  [berzerk0](https://github.com/berzerk0/Probable-Wordlists/tree/master/Real-Passwords/WPA-Length). It includes a twenty-four million passwords dataset that will be partially used in the project.



## Model:
The model used is mainly based on the RNN LSTM-based Text Predictor.

Long short-term memory (LSTM) is a recurrent neural network (RNN) architecture. LSTM has feedback connections. It can process single data points (such as images) and, more importantly, entire sequences of data (such as speech or video).

Utilizing the fact that LSTM can learn sequences, a text predictor is a major application of LSTM. Text prediction can be used to generate human-like text by training it using books and literature.

![](imgs/lstm.png)

### Text prediction defined by:
1. The main attribute for LSTM is the size of the hidden layers.
2. The LSTM takes a fixed size input of letters (sentence of size seq_length).
3. The output is the letter after the sentence.
4. The input sentence is taken from the text and shifted for (step) letters each time.
5. Letters are converted to index numbers for the training, and the prediction is converted back into letters.

Passwords dataset is converted into a text by concatenating them and using a space as a separator.

![](imgs/text_predict.png)



## Hyper-parameters:
1. Sentence Length: usually set to 10-30, in our implementation we fixed it at 25
2. Step size: usually set to 1-5, in our implementation we fixed it at 3
3. Hidden layers size: we tested 512 layers and 1,024 layers
4. Batch size: we tested 32, 128, 256, 512
5. Epoches: we tested it for upto 20 epoches

## Metrics:
The primary metrics for model training is the loss value and accuracy. However, to properly test the output of the model, we used a hit rate. The hit rate is the probability of generating a password that exists in the test set (number of generated passwords that exist in the test set/ total generated passwords).

## Results:
Using portion (5 million divided into train: 200k, validate 50k, test: 4.75M) of the WPA 24 million dataset, we did the following tests.
### 512 hidden layers:

#### Batch: 32
| [![](results/512_layers/data4999893_batch32_epochs20_model_loss-1.png)]() | [![](results/512_layers/data4999893_batch32_epochs20_model_accuracy-1.png)]() | [![](results/512_layers/data4999893_batch32_epochs20_model_hit_rate-1.png)]() |
|:---:|:---:|:---:|


#### Batch: 128
| [![](results/512_layers/data4999893_batch128_epochs20_model_loss-1.png)]() | [![](results/512_layers/data4999893_batch128_epochs20_model_accuracy-1.png)]() | [![](results/512_layers/data4999893_batch128_epochs20_model_hit_rate-1.png)]() |
|:---:|:---:|:---:|


#### Batch: 256
| [![](results/512_layers/data4999893_batch256_epochs20_model_loss-1.png)]() | [![](results/512_layers/data4999893_batch256_epochs20_model_accuracy-1.png)]() | [![](results/512_layers/data4999893_batch256_epochs20_model_hit_rate-1.png)]() |
|:---:|:---:|:---:|


#### Batch: 512
| [![](results/512_layers/data4999893_batch512_epochs20_model_loss-1.png)]() | [![](results/512_layers/data4999893_batch512_epochs20_model_accuracy-1.png)]() | [![](results/512_layers/data4999893_batch512_epochs20_model_hit_rate-1.png)]() |
|:---:|:---:|:---:|



### 1024 hidden layers:

#### Batch: 32
| [![](results/1024_layers/data4999893_batch32_epochs20_model_loss-1.png)]() | [![](results/1024_layers/data4999893_batch32_epochs20_model_accuracy-1.png)]() | [![](results/1024_layers/data4999893_batch32_epochs20_model_hit_rate-1.png)]() |
|:---:|:---:|:---:|


#### Batch: 128
| [![](results/1024_layers/data4999893_batch128_epochs20_model_loss-1.png)]() | [![](results/1024_layers/data4999893_batch128_epochs20_model_accuracy-1.png)]() | [![](results/1024_layers/data4999893_batch128_epochs20_model_hit_rate-1.png)]() |
|:---:|:---:|:---:|


#### Batch: 256
| [![](results/1024_layers/data4999893_batch256_epochs20_model_loss-1.png)]() | [![](results/1024_layers/data4999893_batch256_epochs20_model_accuracy-1.png)]() | [![](results/1024_layers/data4999893_batch256_epochs20_model_hit_rate-1.png)]() |
|:---:|:---:|:---:|


#### Batch: 512
| [![](results/1024_layers/data4999893_batch512_epochs20_model_loss-1.png)]() | [![](results/1024_layers/data4999893_batch512_epochs20_model_accuracy-1.png)]() | [![](results/1024_layers/data4999893_batch512_epochs20_model_hit_rate-1.png)]() |
|:---:|:---:|:---:|








## Analysis:
Viewing the results graph, we can notice multiple possible paprmeter combinations. But considering the training time as well, we chose the (512 hidden layers, batch of 512, and an epoch of 4) which achieved a hit rate of 16%.


## Acknowledgment:

* [Ajhalthor](https://github.com/ajhalthor/Keras_LSTM_Text_Generator) provided a starting point for the text predictor. 

* Passwords dataset was available thanks to [berzerk0](https://github.com/berzerk0/Probable-Wordlists/tree/master/Real-Passwords/WPA-Length).

*  The following [paper](https://www.mdpi.com/1424-8220/20/11/3106/pdf) proivdes a 
Generative Adversarial Network (GAN) based password generator.
* This project is part of the COSC-601 course taught by Dr.Zeyar Aung.
