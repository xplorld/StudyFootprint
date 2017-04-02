# Language Models for Machine Translation: Original vs. Translated Texts

[aclweb](http://www.aclweb.org/anthology/D11-1034)

# intro

在机器翻译（MT）语料库里证明了一件事情：「中式英文」， or more generally 「A 式 B 文」是存在的。形式化一点就是，中文翻译成的英文，和 original 英文的语言模型是不一样的。

三个猜想：

1. 中文翻译成的英文和 original 英文的语言模型是不一样的。
2. A 语言翻译成的英文和 B 语言翻译成的英文的语言模型是不一样的。
3. MT 系统用翻译语料做的 LM，比用 original target language 的语料做的 LM，效果更好。

# Method

就找了一个 MT 库， 换里面的 LM.

LM 用的是 SRILM 搞的 4-gram, MT 用的是 Moses.

语料是 Europarl, 欧盟搞的一个 multi-language parallel corpus. 来源是欧洲议会的文件。每个文件会被翻译成 n 种语言。 语料还用了 Hansard, 是加拿大议会的英法互译记录。还有一个希伯来语的什么语料。

多语言政治组织的议事真的是为 MT 界提供了莫大的帮助呃。

# Experiment

1. 用 Any -> B 的 LM 去测试 A -> B 的 B 句子。然后发现 A -> B 比 Any other -> B 的 LM 的 ppl 都好。简直是废话。

2. 用 Any -> B 的 LM 装进 MT 里去翻译 A 语言到 B， 用 A -> B LM 的 BLEU 最好。还是废话。

# Conlustion

三个猜想成立。

噫。。。

















