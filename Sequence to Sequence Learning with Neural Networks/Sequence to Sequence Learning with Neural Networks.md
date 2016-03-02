#Sequence to Sequence Learning with Neural Networks - NIPS 2014

###Note wrote by Mingdong

##Task
Machine translation from English to French.
 
##Method
###Overview
It is a statistical machine translation approach so it uses a **Stacked LSTM** (4 layer) to parameterized a **Conditioned Possibility**

![](https://github.com/KevinWangTHU/rnn_papers/raw/master/Sequence%20to%20Sequence%20Learning%20with%20Neural%20Networks/eq1.png)

###Stacked LSTM

![Figure 1](https://github.com/KevinWangTHU/rnn_papers/raw/master/Sequence%20to%20Sequence%20Learning%20with%20Neural%20Networks/fig1.png)

As shown in the figure 1, first the LSTM reads in the input, then \<EOS\>. Afterwards it begins to output translated sequence until another \<EOS\> is predicted.

Note that here a unit is actually 4 vertically placed units (Refer to the [author's talk](research.microsoft.com/apps/video/?id=239083) for more details).

The input words are embedding vectors and the output words are predicted by _a super huge softmax \(1000\*80000\!\)_.


##Contribution
Improve the performance by using Stacked LSTM comparing to [Cho's](https://github.com/KevinWangTHU/rnn_papers/blob/master/Learning%20Phrase%20Representations%20using%20RNN%20Encoder-Decoder%20for%20Statistical%20Machine%20Translation/Learning%20Phrase%20Representations%20using%20RNN%20Encoder-Decoder%20for%20Statistical%20Machine%20Translation.md) and [Bahdanau's](https://github.com/KevinWangTHU/rnn_papers/blob/master/Neural%20Machine%20Translation%20by%20Jointly%20Learning%20to%20Align%20and%20Translate/Neural%20Machine%20Translation%20by%20Jointly%20Learning%20to%20Align%20and%20Translate.md) work.

###Tricks - Reverse input sequence 
Reduce the long term dependency problem.



##Drawback
It did not use any more sophisticated techniques like *Attention*. Thus it have to use more parameters (stacked LSTM)

Stacked LSTM and large softmax make training very time consuming. 8 GPU * 10 days.

##Reference

[Author's Talk](research.microsoft.com/apps/video/?id=239083) is very informative.

##Cite
[Bibtex](https://scholar.google.hk/scholar.bib?q=info:jVIu8OnqRLYJ:scholar.google.com/&output=citation&scisig=AAGBfm0AAAAAVtagbMd5lpdkS9BKtS6MdGr4_wsJDXPc&scisf=4&hl=en)


