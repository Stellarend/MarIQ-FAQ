# MarIQ-FAQ
Frequently Asked Questions about MarIQ

### What is MarIQ:
MarIQ is a reinforcement learning program that teaches itself to play Super Mario Kart by a technique called Deep Q Learning. As it makes forward (or backward) progres through levels, it gets rewarded (or punished) accordingly, then learns which controller inputs will maximize its future reward in any given situateion. 
The "Tryhard%" indicates how much it's trying to do well versus explore new strategies. The network is a recurrent neural network with layers of size 300, 300, 150, running using TensorFlow on SethBling's new 1080TI system. When it freezes momentarily, it's training the network on its recent experience, or saving a checkpoint.

### What is a Neural Network?
A neural network (NN) is compsed of a input layer, a set of hidden layers and an output layer. These layers contain neurons which recieve data, apply a function and pass it out to the next layer. This process is repeated untill the output layer. The input layer has neurons that get specifed data from the game.

### What does recurrent mean?
A recurrent neural network (RNN) not only uses current data but it also uses data from other itterations. In the case of MarIQ, a regular neural network would only use data from each frame but since MarIQ uses a RNN, it also uses data from previous frames. This helps the NN by poentially giving a sense of time, speed and causality.

### What are the possible outputs?
MarIQ has one hot output meaning that only the largest number in the NN output is used as input for the game. The index-controler maps to 0:None, 1:A, 2:Right, 3:Right+A, 4:Left, 5:Left+A.

### What are the inputs?












## Less Frequently Asked Questions
#### What activation function is used
Probbably tanH

#### How does MarIQ get better
When the tryhard% is high, it probabbly uses back proppogation in order to refine values within the NN.
When the tryhard% is low, it probbably just assigns a random value somewhere in hopes of approaching a global min error.
