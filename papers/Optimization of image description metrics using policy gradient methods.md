# Optimization of image description metrics using policy gradient methods

via [arxiv](https://arxiv.org/pdf/1612.00370.pdf)

# work

image -> caption 

# idea

传统方法用 MLE 去最大化样例句子的概率。问题是 

1. exposure bias: rnn 训练时候每个新词都基于 ground truth, 用起来却基于自己，有 bias
2. 只考虑了正确句子，没考虑错误句子

想换个 metrics, 除了 P(正确句子 | 图，\theta) 以外的。我们有：

1. BLEU
2. CIDEr
3. METEOR
4. ROUGE

但是他们不可微分，没法搞 descent. 于是考虑搞成一个 reinforcement, 把一句话输出完以后的 metric score 作为 reward. 这个叫 policy gradient (PG). 一顿推导后给出一个算法。

这样就有方法可以用任何 M:句子 -> [0,1] 的 metric 做目标函数，而不用管可不可微。

于是他们很没节操地把所有 metrics 加权一起用了，包括一个 [SPICE](http://www.panderson.me/spice/) 是新提出的 image captioning 用 metric. 结果发现，所有 metric 混杂的 PG 效果最好。(废话)

