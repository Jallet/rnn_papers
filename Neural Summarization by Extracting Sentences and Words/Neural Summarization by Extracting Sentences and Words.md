#Neural Summarization by Extracting Sentences and Words

Submitted to ACL-16, University of Edinburgh

###Written by Mingdong

##Task
Extractive single document summarization by a data-driven approach based on RNN.


##Dataset
They retrieved hundreds of thousands of news articles and corresponding highlights from the DailyMail website. Using a number of transformation and scoring algorithms they __matched__ highlights to document content and construct two large scale training datasets, one for sentence extraction and the ohter for word extraction. 

They designed a rule-based system to determine whether a document sentece mateches a highlights and should be albeled with 1 (must be in the summary) or 0. The accuracy on the held-out data is 85%. (~ 30% of sentences are labeled as summary-worthy __Problem: is this too high? how to produce output?__) __The dataset is about 200K pairs.__

For word extraction. In cases where all highlight words come from the original document, the document-highlight pair constitutes a valid training example and is added to the word extraction dataset. For out-of-vocabulary words they tried to find a semantically equivalent replacement in the news article. Otherwise the pair is discarded. __The dataset is about 170 pairs.__

For more details see section 3 of this paper.

##Method

###Overview
Instead of human-engineered features, this paper proposed a data-driven approach to summarization based on neural networks and continuous sentence features.

They developed a general framework for single-document summarization, which includes a NN-based hierarchical document encoder and attention-based extractor. The extractor can extract sentences and words. 

Contrary to previous work, where attention is an __intermediate__ step uesd to blend hidden units of an encoder, this model applies attention __directly__ to select sentences or words of the input document as the output summary. 

###CNN Sentence Encoder and RNN Document Encoder
See figure. Pretty straight forward.

![Figure 2](toadd)

_Note that they use another task to pretrain the CNN encoder._

###Sentence Extractor
The extractor directly applies attention to extract salient sentences after reading them. The extractor is another RNN that labels sentences sequentially. The architecture is also in the figure. 

First get h'\_t = LSTM(p\_t-1s\_t-1, h'\_t-1), then use it and h\_t to calculate p(y_t=1|D). _Note that they adopt a curriculum learning strategy to solve the discrepancy between training phase and predict phase._

Here they do not use attention mechanism.


###Word Extractor
![Figure 3](toadd)

![Formulae](toadd)

The architecture is shown in Figure 3.

The word extractor produce one word at one time. It can be viewed as a conditional language model with a vocabulary constraint. 

##Contribution

1. The dataset. (Though Prof. Huang said that the labeling is too heavy, I think it is still a beneficial trial towards real document summarization.)
2. Presented a data-driven summa- rization framework based on an encoder-extractor architecture.

##Drawback

In the word extractor, each coding is used to produce one word, which is not intuitive. An autoencoder should be able to improve it. 

Another problem is that the output of SE consists of too many sentences (See the examples).

The writing is also of somewhat problems (softmax should be exp, for example).

##Cite
