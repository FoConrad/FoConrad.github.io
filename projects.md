---
layout: page
title: Projects
subtitle: Coding projects I have written or contributed to
---

#### Contents
- <a href="#ppo-for-mxner">PPO for MXNet</a>
- <a href="#password-manager-pw_man">Password manager</a>
- <a href="#backpropagation-through-an-rnn-hash-function">Backpropagating through an RNN hash function</a>

### [PPO](https://openai.com/blog/openai-baselines-ppo/) for [MXNet](https://mxnet.apache.org)
[Proximal Policy Optimization](https://openai.com/blog/openai-baselines-ppo/), or PPO,
is a policy gradient method in the field of reinforcement learning. The main 
implementation for it is provided in the [OpenAI Baselines](https://github.com/openai/baselines) repository, which uses the [TensorFlow](https://www.tensorflow.org/) machine learning
library. Due to the need for this algorithm in a research project (actually, multiple) I was involved in, I rewrote this for
MXNet (the implementation of PPO in MXNet was primarily one of my contributions, but others mentioned in the repository helped as well).

Our code for PPO in MXNet can be found [here](https://github.com/FoConrad/PPO-MxNet). 
Additionally, I have added code to train the CartPole problem provided by
[OpenAI Gym](https://gym.openai.com/). This trains in an embarrassingly few number of
iterations, and the trained model is shown balancing the pole below (with some
random actions thrown in to make its job harder!).


<img src='/img/cartpole.gif' class='center-img' alt='CartPole'>


### Password manager: [`pw_man`](https://github.com/FoConrad/pw_man)
Due to the vast number of passwords I need for websites and an aversion
to storing them with the browser or a password manager I have not written, 
I created [pw_man](https://github.com/FoConrad/pw_man).

This is a password manager written in a single bash file. It works for Mac 
and Linux, with only `gpg`, and either `pbcopy` or `xclip` as dependencies. It 
allows you to store many passwords using a single one, and a quick retrieval process that stores it directly in your clipboard (for a limited amount of time, then it is erased from clipboard so no one else can paste it to see!).


### Backpropagation through an RNN hash function
This simple proof-of-concept repository [NN-Hashing](https://github.com/FoConrad/NN-hashing) shows that hash functions made from neural networks are susceptible to collisions due to the information exposed in the gradients.

[Some work](https://www.researchgate.net/publication/310624366_Hash_function_generation_by_neural_network) proposed using an RNN as a hash function, which likely was never intended to be cryptographically secure. This work proposes sending blocks of bits into an RNN until the entire file has been processed. It appeared to me that when processing the file, information from the gradient could be used to possibly find a hash collision.

So I wrote a python program that uses [adversarial example](https://medium.com/@ml.at.berkeley/tricking-neural-networks-create-your-own-adversarial-examples-a61eb7620fd8)  techniques to arrive at a collision given some target hash, and some random input file. The program achieves its goal nearly completely, with some work left on keeping the input bits discreet while maintaining the collision.

```
~$ /hashing.py --source test/source test/target
0x12ed2f3b00eed598d98f59fdc999351b - original source hash
0x97cd2b6f19b7d6ac113d789dc655213c - target hash
0x97cd2b6f19b7d6ac113d789dc655213c - step... 54 *
```
