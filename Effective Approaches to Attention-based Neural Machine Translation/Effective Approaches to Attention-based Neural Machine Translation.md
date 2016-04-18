#Effective Approaches to Attention-based Neural Machine Translation

###Written by Mingdong

##Task
MT from English to German (WMT'15)

##Dataset
Training data: WMT'14 training data consisting of 4.5M sentences pairs. Filtered out length > 50 pairs.

##Method
####Overview
This paper proposed a new local attention model and compared it with previous global model. Both models achieved good result on WMT'15 task.

####NMT
The attention-decode framework is same as other papers. You can refer to other papers in this repo to check the details.

####Attention-based Model
In common: 

1. Input is h_t at the top layer of the stacking LSTM.
2. Output is c\_t that captures relevant source-side information to help predict y\_t.
3. Given h\_t and c\_t, concatenate them and use a softmax to compute output distribution.

The basic framework is just like Ilya's seq2seq, but added an attention layer between the LSTM and the softmax-output.

Also, the score functions and their differences is discussed. For detail refer to the paper.

####Global
Use the top layer's h\_t to calculate the alignment weight and the weighted sum. Note that the difference is that the attention layer is just used to predict the output, rather than being used to calculate h\_t+1, as in Badaunau's paper.

####Local
Global attention's problem:

1. expensive
2. make important part more vague

Between soft and hard attention, they proposed local attention.
It is easier to train than hard attention while less expensive than soft.

First get p\_t, then calculate the weighted sum over [p\_t-d, p\_t+d].

1. p\_t = t 
2. p\_t is predicted by a non-linear function. Then, alighment is calculated with a gaussian distribution.

####Input-feeding Approach
To take into account past alignment information, they used an input-feeding technique, which concatenate the previous attention vectors with current input. Now, the network spans both horizontally and vertically.

##Contribution
Proposed two simple attentional mechanisms for NMT. The attention layer is much easier than previous ones. Also the local attention model is inspirational.

##Drawback
Would be better if they can visualize attention vectors.

##Cite
[Bibtex](https://scholar.google.com/scholar.bib?q=info:8iwlXnrxWqsJ:scholar.google.com/&output=citation&scisig=AAGBfm0AAAAAVwzT3IXk_yfEV1b570JBk-bga1x0Gh-Z&scisf=4&hl=en)