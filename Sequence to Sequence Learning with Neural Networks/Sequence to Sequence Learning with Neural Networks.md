#Sequence to Sequence Learning with Neural Networks - NIPS 2014

##Note wrote by Mingdong

##Task
Machine translation from English to French.
 
##Method
###Overview
It is a statistical machine translation approach so it uses a **Stacked LSTM** (4 layer) to parameterized a **Conditioned Possibility**

![](https://github.com/KevinWangTHU/rnn_papers/raw/master/Sequence%20to%20Sequence%20Learning%20with%20Neural%20Networks/eq1.png)

###Stacked LSTM

![Figure 1](https://github.com/KevinWangTHU/rnn_papers/raw/master/Sequence%20to%20Sequence%20Learning%20with%20Neural%20Networks/fig1.png)

As shown in the figure 1, first the LSTM reads in the input, then \<EOS\>. Afterwards it begins to output translated sequence until another \<EOS\> is predicted.

The input words are embedding vectors and the output words are predicted by a *super huge softmax (1000\*80000\!!)*.


##Contribution
It is the first paper of recent Seq2Seq learning trend. Utilized LSTM to model possibility and output sequences.
###Tricks - Reverse input sequence 
Reduce the long term dependency problem.



##Drawback
Since this is the first paper about this topic, it did not use any more sophisticated techniques like *Attention*. Thus it have to use more parameters (stacked LSTM)

Stacked LSTM and large softmax make training very time consuming. 8 GPU * 10 days.

##Reference
[Author's Talk](research.microsoft.com/apps/video/?id=239083)



