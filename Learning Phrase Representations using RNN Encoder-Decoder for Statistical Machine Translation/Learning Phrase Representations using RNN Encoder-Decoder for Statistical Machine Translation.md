#Learning Phrase Representations using RNN Encoder-Decoder for Statistical Machine Translation - EMNLP 2014

###Note wrote by Mingdong

##Task
Machine translation from English to French

However the task differs from [Sequence to Sequence Learning](https://github.com/KevinWangTHU/rnn_papers/blob/master/Sequence%20to%20Sequence%20Learning%20with%20Neural%20Networks/Sequence%20to%20Sequence%20Learning%20with%20Neural%20Networks.md), since

1. It only trys to translate phrases in the phrase-table
2. It is not a generation method but just uses the log-likelihood as an additional feature. 

Thus, this paper is more related to standard MT method.

##Method
It uses a RNN-Encoder-Decoder structure , as shown in figure 1. It uses **GRU** instead of standard RNN or LSTM.

![](https://github.com/KevinWangTHU/rnn_papers/raw/master/Learning%20Phrase%20Representations%20using%20RNN%20Encoder-Decoder%20for%20Statistical%20Machine%20Translation/fig1.png)

Note that in this paper, the flow is

1. Input phrase x
2. Get c from x
3. Use y\_t-1, h\_t-1 and c together to get h\_t
4. Use h\_t, y\_t-1 and c together to get possibility of y_t
5. Use the possibility as feature

##Contribution
This is the first (as I know) paper that used RNN to do translation task and achieved good result.

It proposed GRU.

##Drawback
It was still designed for standard phrase-based method. 

It can just get phrase representation.

It is not a pure generation method.


##Cite
[Bibtex](http://aclweb.org/anthology/D/D14/D14-1179.bib)