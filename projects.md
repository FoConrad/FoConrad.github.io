---
layout: page
title: Projects
subtitle: Coding projects I have written or contributed to
---

<script>
// TODO(Conrad): Find a clean way to just read this
var pre_data = ["~$ /hashing.py --source test/source test/target",
"0x12ed2f3b00eed598d98f59fdc999351b - original source hash",
"0x97cd2b6f19b7d6ac113d789dc655213c - target hash"]

var data = [
    "0x12ed2f3b00eed598d98f59fdc999351b - step... 0",
    "0xdcc721265f35066e712d60059644aeac - step... 1",
    "0x87c1216e37b596ac117d7c85d655a82c - step... 2",
    "0x83c123ee31a79eac111f7c95d675212e - step... 3",
    "0x93a5234f01afdeac183d39d9c679317a - step... 4",
    "0x13ada35b08eedfb8182d19f9cc79717b - step... 5",
    "0x172daf5b08eedfb8592d59f9cc49353f - step... 6",
    "0x172daf6b08ee56ba592d59b9ce493d39 - step... 7",
    "0x16ef2f6b083e16b2592f7995df453c39 - step... 8",
    "0x12cf2f6f09371ea4593f7c85dfd42c39 - step... 9",
    "0x92cb2f6f11370ea4d13f7c8dded42c39 - step... 10",
    "0xd3c9296f113506ac913f7c05d6d42c2c - step... 11",
    "0xd3cd2b6e11b516acb13f7c05c654282c - step... 12",
    "0x93c52b6e11b5d6acb11f7985c654202c - step... 13",
    "0x9a852b6f11b5d68c311f7995c655303c - step... 14",
    "0x9aa52b6f19b5d68c192d799dc65d303e - step... 15",
    "0x1aa52b6b09afd6ac192d7899c649313c - step... 16",
    "0x1fed2b0b09afdeac192d79b9c6413538 - step... 17",
    "0x17cd2b2b08af5ebc193d7989c6402539 - step... 18",
    "0x17cdaf2f08af1ebc113d7885d6502539 - step... 19",
    "0x17cd2f6f18bf1eac113d7c85d6552539 - step... 20",
    "0x97892f6f18b71eac113d7c95c6452539 - step... 21",
    "0x93812b6f1db596ac513d7c95c645293c - step... 22",
    "0x93c12b6f15b596ac513d781dc645393c - step... 23",
    "0xdbc12b6f11b5d6ac111d791dc644383c - step... 24",
    "0x9ac52b6f11b7d6ac110d7999c654383c - step... 25",
    "0x1bcd2b6f19bfd6ac113d7999de54203c - step... 26",
    "0x1bcd2f6e19bfdeac113f799dde54202e - step... 27",
    "0x1fcd2bef19b7deac113d788dde55252f - step... 28",
    "0x17cd2b2f18b7d6ac113d7885ce55253b - step... 29",
    "0x97cd2b6f18b756ac113d7885c6552d38 - step... 30",
    "0x97cd2b6f11b756ac113d7885c6453d3c - step... 31",
    "0x978d2b6f19b756ac113d7885c645393c - step... 32",
    "0x978d2b6f19bf9eac113f789dc645203c - step... 33",
    "0x978d2f6f19bf9eac113f789dde45203c - step... 34",
    "0x1fcd2b6f19bfdeac113f789dde54243c - step... 35",
    "0x1fcd2b6f18b7deac513d789dce54243c - step... 36",
    "0x13c52b6f18b7deac513d789dc654253c - step... 37",
    "0x93c52b6f18b7d6ac113d789dc655213c - step... 38",
    "0x93c52b6f19b7d6ac113d7995c655213c - step... 39",
    "0x9bcd2b6f19b7d6ac113d799dc655213c - step... 40",
    "0x9bcd2b6f19b7d6ac113d799dc645203c - step... 41",
    "0x93cd2b6f19bfd6ac113d789dce45243c - step... 42",
    "0x13cd2b6f19bfd6ac513d789dce45243c - step... 43",
    "0x17cd2b6f19b7deac513d789dc655203c - step... 44",
    "0x17cd2b6f19b7deac113d789dc655213c - step... 45",
    "0x97cd2b6f19b7deac113d789dc655213c - step... 46",
    "0x97cd2b6f19b7deac113d7895c655213c - step... 47",
    "0x97cd2b6f19b7deac113d7895c655243c - step... 48",
    "0x93cd2b6f19b7deac113f789dc655243c - step... 49",
    "0x93cd2b6f19b7deac113f789dc645243c - step... 50",
    "0x93cd2b6f19b7deac113f789dc645243c - step... 51",
    "0x97cd2b6f19b7d6ac113d7895c655213c - step... 52",
    "0x97cd2b6f19b7d6ac113d7895c655213c - step... 53",
    "0x97cd2b6f19b7d6ac113d789dc655213c - step... 54 * ...success"
];
var wait = function(func) {
    if (window.jQuery)
        func();
    else
        setTimeout(function() { wait(func) }, 10);
};
wait(function(){
    $("a.scroll").click(function(ev) {
        ev.preventDefault();
        var navbar_height = $('.navbar').height() + 3;
        $("html, body").animate({
            scrollTop: $($(this).attr("href")).offset().top - navbar_height,
        }, 500);
    });
});
// "Now," said Virgil, "we are enter the second layer of Callback Hell! Here
// you will find those guilty of abusing poor setTimeout."
wait(function() {
    var index = 0;
    var iterate = function(func) {
        if (func()) {
            setTimeout(function(){iterate(func);}, 2500)
        } else {
            setTimeout(function(){iterate(func);}, 60);
        }
    };
    iterate(function() {
        var text_array = pre_data.concat([data[index]]);
        $('div.highlighter-rouge code').html(text_array.join("\n"));
        index = (index+1) % data.length;
        return index == 0;
    });
});
</script>

#### Contents
- <a class="scroll" href="#ppo-for-mxnet">PPO for MXNet</a>
- <a class="scroll" href="#password-manager-pw_man">Password manager</a>
- <a class="scroll" href="#backpropagation-through-an-rnn-hash-function">Backpropagating through an RNN hash function</a>

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

[Some work](https://www.researchgate.net/publication/310624366_Hash_function_generation_by_neural_network) (which I found cited [in this paper](https://ai.google/research/pubs/pub46518)) proposed using an RNN as a hash function, which likely was never intended to be cryptographically secure. This work proposes sending blocks of bits into an RNN until the entire file has been processed. It appeared to me that when processing the file, information from the gradient could be used to possibly find a hash collision.

So I wrote a python program that uses [adversarial example](https://medium.com/@ml.at.berkeley/tricking-neural-networks-create-your-own-adversarial-examples-a61eb7620fd8)  techniques to arrive at a collision given some target hash, and some random input file. The program achieves its goal nearly completely, with some work left on keeping the input bits discreet while maintaining the collision.

```
~$ /hashing.py --source test/source test/target
0x12ed2f3b00eed598d98f59fdc999351b - original source hash
0x97cd2b6f19b7d6ac113d789dc655213c - target hash
0x97cd2b6f19b7d6ac113d789dc655213c - step... 54 *
```
