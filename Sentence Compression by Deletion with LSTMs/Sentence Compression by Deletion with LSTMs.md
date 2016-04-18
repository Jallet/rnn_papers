#Sentence Compression by Deletion with LSTMs

###Written by Mingdong

##Task
Sentence compression: Translate a sentence into a sequence of 0/1. 

##Dataset
They collected the dataset and [made it public](http://storage.googleapis.com/sentencecomp/compression-data.json). 

Training data is ~ 2M parallel sentence-compression pairs from the news. Test data = 10k pairs.

##Method
This is basically a classification work. The network is shown in figure 1.

First the input is reversed then put in unchanged again. Pretty straight forward. The representation of input consists of two parts: the embedding of current word and last label. Last label contain a one hot sport representation of the previous word's label (为什么是3维的one-hot向量来表示？没懂).

They also gave two variants of the basic version. First is LSTM+PAR, in which model we provide not only the embedding of the current word but also its parent word. The other one is LSTM+PAR+PRES, which adds three more bit of feature. 

The result shows that for automatic evaluation, more feature means more better performance. But for human evaluation, the basic LSTM model gives best readability and informativeness.

The paper also discusses some difficult samples. 
> Sentences which pose difficulty to the model are the ones with quotes, intervening commas, or other uncommon punctuation patterns.
> 
> Our understanding of why the extended model (LSTM+PAR+PRES) performed worse in the human evlauation than the base model is that, in the absence of syntactic features, the basic LSTM learned a model of syntax useful for compression, while LSTM++, which was given syntactic information, learned to optimize for the particular way
the ”golden” set was created (tree pruning). While the automatic evaluation penalized all deviations from the single golden variant, in human evals there was no penalty for readable alternatives.

##Contribution
Built a sentence compression system without linguistic features by LSTM and performed well. They also collected a huge dataset.

This work shows that the sentence compression can be done by LSTM network, which means the _pattern_ of compression is easy to capture. In fact, the harder abstractive sentence summarization problem is also easy for LSTM network. 

In all, these works showed that sentence level feature can be captured by LSTM.

##Drawback
Task is not exciting. Not generative but only labelling work. Also attention and memory should be able to improve the result.

##Cite
[Bibtex](https://scholar.google.com/scholar.bib?q=info:wo0n4gbkomgJ:scholar.google.com/&output=citation&scisig=AAGBfm0AAAAAVwyTJfKeZ1F20lZ68dEng53sOhm2B6aO&scisf=4&hl=en)