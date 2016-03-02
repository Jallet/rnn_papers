#Neural Machine Translation by Jointly Learning to Align and Translate - ICLR 2015

###Note wrote by Mingdong

##Task
Machine Translation from English to French

This is a pure generation approach, like [Sequence to Sequence Learning](https://github.com/KevinWangTHU/rnn_papers/blob/master/Sequence%20to%20Sequence%20Learning%20with%20Neural%20Networks/Sequence%20to%20Sequence%20Learning%20with%20Neural%20Networks.md).


##Method
###Overview
This model consists of two parts:

1. Encoder: Bi-directional RNN
2. Decoder: GRU + Attention

As shown in figure 1.

![Figure 1](https://github.com/KevinWangTHU/rnn_papers/raw/master/Neural%20Machine%20Translation%20by%20Jointly%20Learning%20to%20Align%20and%20Translate/fig1.png)

###Encoder
A vector concatenated by two vectors, which were produced by a forward and a backward RNN.

The author claimed that the RNN can better focus on the local input, thus better fits the whole model.

###Decoder
Basically it is a GRU. The flow is 

1. We have all input vector \{h\}, previous hidden state s\_i-1, previous output y\_i-1.
2. Use a score function to compute the score(h\_j, s\_i-1) = a\_ij
3. Use a\_ij to compute the weighted sum of all h\_j to get c\_i.
    * In one word, the aim of step 2 and 3 is to get a weighted sum of input vectors as the input of the RNN-Decoder
    * Step 2 get the weight
    * Step 3 get the sum
4. Use s\_i-1, y\_i-1, c\_i to compute next hidden state s\_i
5. Use s\_i, y\_i-1, c\_i to predict next output y\_i







##Contribution
Instead of previous Encode-Decode structure, this paper used the **attention** to dynamically focus on different vectors rather than single sentence representation vector. This makes it work better with long sequences, as the experiments shown.


##Drawback
There are many things that can be replaced, which makes me curious about their effects.

1. Bi-RNN
	  * Can it be replaced by LSTM, single RNN or just raw input vector?
2. GRU
	  * Can it be replaced by LSTM or other RNN?

##Cite
[Bibtex](https://scholar.google.hk/scholar.bib?q=info:7shpF8Tg3oIJ:scholar.google.com/&output=citation&scisig=AAGBfm0AAAAAVtakNirnmsHvYkFLQk9A7MZYbgHc8yu8&scisf=4&hl=en)
