#A Neural Attention Model for Abstractive Sentence Summarization

###Written by Mingdong

##Task
_Abstractive_ sentence summarization: Not just compression or extractive.

##Dataset
####For Training:
Gigaword dataset (~9.5 million news articles), which is already tokenized. They filtered out many articles and at last the training set consists of roughly 4M articles. The detailed statistics can be found in the paper.

The task is: First sentence -> Headline.


####For Testing:
DUC-2003, 2004 shared tasks. Consists of 500 news articles, each paired with 4 different human-generated reference summaries, < 75 bytes ~ 14 words. Summarizations are based on the text of the whole articles (but in this paper they just used the first sentences).

They also used a randomly held out subset of Gigaword (same as the training data).


##Method
###Overview
This is also a sequence to sequence problem, but they used a different framework. They seems to use the standard framework in their next paper (NAACL, not camera-ready yet).

The general loss function is the same: log p(y | x). The output is also produced by beam search. But they used a context window for input sequence modeling rather than RNN-Encoder. The did not use a LSTM decoder.
 
The overall framework is shown as figure 3.


###Encoder
The encoder incorporate the input sequence and the attempted output to produce a meaningful context for the generation of next output word.

In this paper the writers tried three different encoders: Bag-of-Words, Convolutional and Attention-Based. The bag-of-words and conv are not good. We just discuss the attention-based encoder here.

They tried to train an alignment matrix _P_ between the input and the summary. Then, exp(xPy) is a distribution that can be used to calculate the weighted-sum.

*Note here the dimention described in the paper is not consistent. The y_c is actually a vector, not a matrix.*

###Language Model
In principle the encoder itself should be able to produce the output. However by adding the Language model the output should be more readable.

###Beam search decoding
Just like other sequence output model.


##Contribution
提出了一个纯生成式的句子摘要方法，效果不错。同时，其中还利用了attention，对别的需要alignment的模型有启发。

##Drawback
注意力权值矩阵的解释还是比较弱，尤其是在不是最终步，而是其中一步的时候会不太漂亮。没有seq2seq的一致性高。

##Cite
[Bibtex](https://scholar.google.com/scholar.bib?q=info:BWpSOvvhdckJ:scholar.google.com/&output=citation&scisig=AAGBfm0AAAAAVwtbjFubxYKcDjyQTk8OwVvI2rDDlU1o&scisf=4&hl=en)
