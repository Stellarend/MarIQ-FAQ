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
2. Mario Circuit 3
3. Ghost Valley 2
4. Donut Plains 2
5. Bowser Castle 2
6. Vanilla Lake 2
7. Rainbow Road
8. Koopa Beach 2
9. Mario Circuit 1
10. Ghost Valley 3
11. Bowser Castle 3
12. Choco Island 2
13. Donut Plains 3
14. Vanilla Lake 1
15. Koopa Beach 1
16. Mario Circuit 4
17. Mario Circuit 2
18. Ghost Valley 1
19. Bowser Castle 1
20. Choco Island 1
21. Donut Plains 1
22. Mario's Speed
23. Lakitu backwards warning
24. Item Box
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

### Why are only left, right and B being used?
To reduce complexity. Reduced complexity = More progress/time = Less training time

### What decides the Tryhard%?
Tryhard is a random value between 50% and 100% and changes when ever a training session occurs.

### How often do training sessions occur?
Every 10 seconds in game or 5 seconds IRL

### Why does it freeze so often?
The game freezes when a training session occurs (see above). Whenever training occurs, the program undergoes a massive calculation haul, and saves the data of the network, which is in the ballpark of 5MB in size (for reference, the entirety of the Super Mario Kart ROM is only around maybe 1MB).  

## Less Frequently Asked Questions
#### What activation function is used
Probably tanH

#### How does MarIQ get better
When the Tryhard% is high, it probably uses back propagation in order to refine values within the NN.
When the Tryhard% is low, it probably just assigns a random value somewhere in hopes of approaching a global min error.

#### When is it going to learn that driving on the dirt/grass is bad?
Simple Answer: Never. Long answer: MarIQ does not learn "environments" like being on grass or being in the air or any other scenario. MarIQ instead tries to generalize what it visualizes in its field of vision, and a few other tags (see "What are the NN inputs?"). What MarIQ learns is that some scenarios will give more rewards while others may give less or even punish MarIQ. Over time, the scenarios rewarded will generally be favored as following those result in higher rewards, while following others results in less rewards being payed out. Over even more time, MarIQ will have a tendency to follow the high-paying scenarios, meaning eventually, some day, MarIQ will find a grouping of scenarios where he will not even step on the grass/dirt in the first place, and chat will be happy... until Luigi knocks him back into a corner again.
