# MarIQ-FAQ
### What is MarIQ:
is a reinforcement learning program that teaches itself to play Super Mario Kart by a technique called Deep Q Learning. As it makes forward (or backward) progress through levels, it gets rewarded (or punished) accordingly, then learns which controller inputs will maximize its future reward in any given situation. 
The "Tryhard%" indicates how much it's trying to do well versus explore new strategies. The network is a recurrent neural network with layers of size 300, 300, 150, running using TensorFlow on SethBling's new 1080TI system. When it freezes momentarily, it's training the network on its recent experience, or saving a checkpoint.

### What is a Neural Network?
A neural network (NN) is composed of an input layer, a set of hidden layers and an output layer. These layers contain neurons which receive data, apply a function and pass it out to the next layer. This process is repeated until the output layer. The input layer has neurons that get specified data from the game.

### What does recurrent mean?
A recurrent neural network (RNN) not only uses current data, but it also uses data from other iterations. In the case of MarIQ, a regular neural network would only use data from each frame, but since MarIQ uses a RNN, it also uses data from previous frames. This helps the NN by potentially giving a sense of time, speed and causality.

### What are the possible NN outputs?
MarIQ has one hot output, meaning that only the largest number in the NN output is used as input for the game. The index-controller maps to 0:None, 1:B, 2:Right, 3:Right+B, 4:Left, 5:Left+B.

### What are the NN inputs?
![Alt text](/images/inputs.png?raw=true)
1. Map with mode 7 tilt
2. placeholder
3. placeholder
4. placeholder
5. placeholder
6. placeholder
7. placeholder
8. placeholder
9. Mario Circuit 3?
10. placeholder
11. placeholder
12. placeholder
13. placeholder
14. placeholder
15. placeholder
16. placeholder
17. Mario Circuit 2
18. Ghost Valley 1
19. Bowser Castle 1
20. placeholder
21. Donut Plains 1
22. Mario's Speed
23. Lakitu backwards warning
24. placeholder
25. Pressing Left
26. Pressing Right
27. Pressing B

### What does everything on the screen mean?
![Alt text](/images/uiindex.png?raw=true)
1. Tryhard% indicator
2. Controler visualization
3. Inputs
4. Recurrent neural network
5. Network output values
6. Average reward per step output
7. Simulated game input

### How are you getting the map as an input.
The map is in 2 dimensions and mode 7 is used to apply a matrix transformation that makes it appear tilted

### Why are only left, right and A being used?
To reduce complexity. Reduced complexity = More progress/time = Less training time

### What decides the Tryhard%?
Tryhard is a random value between 50% and 100% and changes when ever a training session occurs.

### How often do training sessions occur?
Every 10 seconds in game or 5 seconds IRL

## Less Frequently Asked Questions
#### What activation function is used
Probably tanH

#### How does MarIQ get better
When the Tryhard% is high, it probably uses back propagation in order to refine values within the NN.
When the Tryhard% is low, it probably just assigns a random value somewhere in hopes of approaching a global min error.
