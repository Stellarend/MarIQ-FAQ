# MarIQ-FAQ
Frequently Asked Questions about MarIQ

### What is MarIQ:
is a reinforcement learning program that teaches itself to play Super Mario Kart by a technique called Deep Q Learning. As it makes forward (or backward) progress through levels, it gets rewarded (or punished) accordingly, then learns which controller inputs will maximize its future reward in any given situation. 
The "Tryhard%" indicates how much it's trying to do well versus explore new strategies. The network is a recurrent neural network with layers of size 300, 300, 150, running using TensorFlow on SethBling's new 1080TI system. When it freezes momentarily, it's training the network on its recent experience, or saving a checkpoint.

### What is a Neural Network?
A neural network (NN) is composed of an input layer, a set of hidden layers and an output layer. These layers contain neurons which receive data, apply a function and pass it out to the next layer. This process is repeated until the output layer. The input layer has neurons that get specified data from the game.

### What does recurrent mean?
A recurrent neural network (RNN) not only uses current data, but it also uses data from other iterations. In the case of MarIQ, a regular neural network would only use data from each frame, but since MarIQ uses a RNN, it also uses data from previous frames. This helps the NN by potentially giving a sense of time, speed and causality.

### What are the possible outputs?
MarIQ has one hot output, meaning that only the largest number in the NN output is used as input for the game. The index-controller maps to 0:None, 1:A, 2:Right, 3:Right+A, 4:Left, 5:Left+A.

### What are the inputs?
![Alt text](/images/inputs.png?raw=true)
1.
2.
3.
4.
5.
6.
7.
8.
9.
10.
11.
12.
13.
14.
15.
16.
17.
18.
19.
20.
21.
22.
23.
24.
25.
26.
27.

### What does everything on the screen mean?
![Alt text](/images/uiindex.png?raw=true)
1.
2.
3.
4.
5.
6.
7.

### What decides the Tryhard%?
Tryhard is a random value between 50% and 100% and changes when ever a training session occurs.

### How often do training sessions occur?
Every 10 seconds in game or 5 seconds IRL

## Less Frequently Asked Questions
#### What activation function is used
Probbably tanH

#### How does MarIQ get better
When the Tryhard% is high, it probably uses back propagation in order to refine values within the NN.
When the Tryhard% is low, it probably just assigns a random value somewhere in hopes of approaching a global min error.
