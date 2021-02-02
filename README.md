# Haiku_generator

In this project I design an LSTM model that generates haiku - short poems that are usually 3-lines long. 

#Data
The dataset is taken from https://www.kaggle.com/hjhalani30/haiku-dataset, but for training I only use the subset of haikus that are exactly 13 words long (for the purpose of simplicity). I create a tokenizer and 1-hot-encode the haikus. My x's are the haikus, whereas y's are the haikus shifted one word ahead so that the LSTM cell can learn to predict the next word based on the last word. 

#Model
The model is an LSTM cell trained to predict the next word in a sequence. The hidden state and cell state pass information from previous words thanks to which predictions are based not just on the last word but also the words that appeared before. I use the Adam optimizer and categorical crossentropy loss. 


#Sampling and prediction
In order to generate new haikus I define an inference model which takes as input the encoding of an initial word (an array of 0s by default) and generates subsequent characters by repeatedly calling the LSTM cell. This time each time we obtain a prediction y, it represents probabilities of the next word corresponding to particular index in the sequence. Then we draw a sample according to these probabilities. Changing the temperature allows us to make the probability distribution rather biased (for low values of temperature) or to be more 'random' by having more entropy (higher values). The obtained sample gets fed to the next iteration of the LSTM cell to obtain the next word based on that prediction.

Below are some examples of generated haikus:

effort right
/
upset
day
about
their
woman
such
He'd
account
/

#Issues

#Work in progress
I intend to create an LSTM with word embeddings to compare the results with that of LSTM with one-hot-encodings.
