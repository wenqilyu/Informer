# Informer: Beyond Efficient Transformer for Long Sequence Time-Series Forecasting

## Overview

### Why we need long sequence
1. Sequence prediction is a problem that involves using historical sequence information to predict the next value or vlues in the sequence. It is a basic but important research problem.
![This is an image](img/img1.png)


### Problems in long sequence prediction
2. As the length of the data sequence increases, the inference speed of LSTM decreases repaidly and result in the inability to predict long sequences with limited computing power and time successfully. Meanwhile, the continuous accumulation of error causes the MSE score to increase rapidly, making the rusult unusable.
![This is an image](img/img2.png)


### The challenges when we use transfromers in long sequence prediction

1. The quadratic computation of self-attention.(Complexity)

   The atom operation of self-attention mechanism, namely conoimcal dot-product, causes the time complexity and memory usage per layer to be O(L^2)


2. the memory bottleneck in stacking layers.(Long Iutput)

   The stack of J encoder/decoder layer makes total memory usage to be O(j·L^2), which limits the model scalability on receiving long sequence inputs.
   

3. the spped plunge in prediction long outputs.(Long Output)

   The dynamic decoding of vanilla Transformer makes the inference spped as slow as RNN-based model.


![This is an image](img/img3.png)


### Improve in Informer（solve the challenges metioned before）

1. Self-attention mechanism

![This is an image](img/img4.png)

![This is an image](img/img5.png)

2. Self-attention Distilling Operation

![This is an image](img/img6.png)

3. Generative-style Decoder

   1)Start token is an efficient technique in NLP "dynamic decoding", especially for per-training model, and we extend it into a generative way.
   
   2)Insted of choosing a specific flag as the token, we sample a "shorter" long sequence in input sequence, which is an earlier slice before output sequence.
   
   3)For example, if we could like to predict 480 pionts(5-day predict in the ETT dataset), we will take the known 5 days before this time sequence as "start-token" and feed the generative-style inference decode with them.
   
  

## Critical Thinking


## Discussion
1. Why we use transformers in LSTF?
2. What is the next step for informer?
3. 


## Resource Links

https://github.com/zhouhaoyi/Informer2020


## Video Recording


## Code Demo

https://colab.research.google.com/drive/1_X7O2BkFLvqyCdZzDZvV2MB0aAvYALLC

