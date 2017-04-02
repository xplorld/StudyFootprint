# SeqGAN: Sequence Generative Adversarial Nets with Policy Gradient

via [arxiv](https://arxiv.org/abs/1609.05473)

# 问题

- exposure bias
	- scheduled sampling (bad probably)
	- seq-based scores, e.g. BLEU (bad for specific task like poem or chatbot. maybe good for generic purpose?)
	- GAN
		- problems:
			- discrete
			- loss D only for whole sequence

# SeqGAN

as a reinforcement problem

- G: model
- Y_1:T = y_i ..., y_T
- state = T_1:t
- policy is stochastic, P_t(y_t) = G(y_t | Y_1:t-1)
- state transtion (based on action of word choice) is deterministic
- D: adverse model
- D(T_1:T) = P(T_1:T is a real sequence)
- reward of sequence for G: likelihood of D get wrong

train by monte carlo & policy Gradient

