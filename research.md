---
layout: page
title: Research
subtitle: Research projects I have led or been a part of
---

## Learning a concurrency control protocol for datatabses

Over the last year I have led a research team with the aim of using learning
methods (reinforcement learning and genetic algorithms) to learn an overly-specific
concurrency control protocol for some database setup. Protocols such as Optimistic
Concurrency Control (OCC) and Two Phase Locking (2PL) already operate on certain
assumptions (high vs low contention workloads). We are trying to take this a step
further, and learn a concurrency control protocol that is optimized for specific
database set up (workload, hardware, and software).

We are submitting this work in mid-July (2019), and I will be able to share more
information after that!

## TensorNinja


### Summary
Immediately when I started at NYU, I became involved in the following project which
was led by Chine-Chin Huang (as well with: Sean Welleck, Minje Wang, Zheng Zhang,
and Jinyang Li).

In this project we aimed to partition tensors in the dataflow graph of a deep
neural network (DNN) across GPU devices such that the training speed for the DNN was 
maximized. We used reinforcement learning to optimize for this metric, and wrote
our system to distribute computation for MxNet. Below shows the time needed per
training example for data parallelism (the default partitioning strategy) and
for the partitioning our model found for various DNN models.

![Results](./img/results.png)

### Additional details

Many modern deep learning systems 
(e.g. tensorflow, mxnet, torch, theano) need to parallelize
the training of deep neural networks across multiple GPU devices.
The  standard strategy is data parallelism, where each device processes a partition
of the input (i.e. the batch tensor is cut along the batch dimension).
and synchronizes weight updates after each iteration.  Currently,
data parallelism is used across machines (inter-machine
parallelism), as well as across multiple devices within a single machine
(intra-machine parallelism).  However, in the intra-machine setting, it is
often desirable to use another form of parallelization, model parallelism, or
to combine both data and model parallelism.

Model parallelism (or more precisely, model partitioning) partitions a weight tensor 
across devices (Another form of model parallelism, which we do not
consider in this paper, assigns different weight tensors to different
devices, or graph partitioning). It can outperform data parallelism when the mini-batch size used 
is relatively small or fixed.  This is desirable for two reasons;
first, training using large batch sizes is generally believed to reduce
accuracy.  Second,
while some recent work have achieved competitive accuracy 
using large batch training,
there is a limit to enlarging the batch size. By supporting small
batch training for intra-machine parallelism, one can scale to more machines
with the same overall batch size limit.

Our project seeks to determine the *best parallelization strategy* for training
a DNN, given a fixed batch size.
Problems we had to address were 1) there lacks an optimization
framework that unifies all parallelization strategies, including model and data parallelism as
well as different combinations of the two, 2) solving the underlying
optimization problem is NP-hard ([shown in spartan](https://www.usenix.org/conference/atc15/technical-session/presentation/huang-chien-chin)).
Our team created a  system (TensorNinja) which
addresses the first challenge by viewing each parallelization strategy as a
specific way of partitioning (or replicating) each tensor involved in the
underlying dataflow graph. Thus, to find the best parallization strategy, we
need to solve the optimization problem of finding the best way of partitioning
(or replicating) each tensor in a given dataflow graph.  TensorNinja addresses the second
challenge using reinforcement learning to smartly explore the space to discover
a good partition scheme without relying on any manually-designed heuristic.

The system was implemented in MxNet (both for partitioning, and training of our model).
Some preliminary results are shown below. Here we compare the partioning our system 
found with data parallelism for a few different models.
