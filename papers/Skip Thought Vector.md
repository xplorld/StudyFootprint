# Skip Thought Vector

[arxiv](https://arxiv.org/pdf/1506.06726.pdf)

a method to do sequence representation

[Word] -> Vector

# method

魔改了 LSTM Encoder-Decoder 的模式。

## Encoder

for a sentence s_i, 整个句子走过 LSTM，取最后的 hidden state h_i.

## Decoder

本来是一个 LSTM, 输入 s_i^j = 第 i 个句子第 j 个词，输出预测的下一个词 s_i^(j+1). 魔改在于对于 reset gate, output value 在过 nonlinearity 之前都加一个 系数矩阵*上一个句子的 encoded vector. 

## Train

Decoder decode 出来一个 value, 认为这个是一个 word2vec 的形式，

P(this word at this point| ctx) = exp(word2vec[ground-truth this word] * prediectd hidden value by LSTM)

minimize sum of log P(word) for all words in sentence in corpus


# Comment

是一个 generative 的 model，可以 generate 句子。
也给了一个 sentence vector, 可以做句子相似性比较。这个意义上两个句子越接近指的是他们预测下一个句子越类似。很想 word2vec. 
本身给的方法是用上句的 vector 预测下句，单方向的。也可以搞成用 i-1, i+1 句预测 i 句，就更像 word2vec.

