# w251_hw11
## Evan Fjeld

The intitial training took about 250 steps before the model started to make more consistent improvement. The duration hovered at around 0 for the first 100 episodes and then jumped to about 25 for the next 150 before making very consistent improvements from 250 to about 550 with a maximum performance of about 200. Then the model's performance falls a little bit before ending about around 150. 

### Initial Training:

<img width="388" alt="initial_training" src="https://user-images.githubusercontent.com/10189327/226795417-a5ee3dd8-a73a-4ede-821b-be63de9b99b9.png">

### First Change
The first change I made to the model was to add a layer to the DQN class. layer3(128, 64). This made a significant improvement to performance. The duration hovers around 0 until it gets to 100 sessions but then jumps up from there with the training loop doing significantly better. But then the model goes down the wrong path and stuggles for a bit and performance follows. It gets back on track at about 450 episodes but never really regains it's footing and finishes at about 100, but starting to move in the right direction. 

<img width="391" alt="first_change" src="https://user-images.githubusercontent.com/10189327/226797965-298eafee-bcca-4043-9ae9-b62acdee179c.png">

The model definitely trained more slowly with an additional layer. 

### Second Change
Next, I tried to change the optimizer from AdamW to SGD. This trains much faster but does significantly worse than Adam. The model starts with much worse performance and then really gets stuck and never improves past about 10. 

<img width="382" alt="second_change" src="https://user-images.githubusercontent.com/10189327/226799587-9311a693-0c57-49a9-80ae-57c20f21cd94.png">


### Third Change
What was the third change you made to the model, and how did it affect the outcome?

### Epsilon Value
How is the Epsilon value used in the training? Why does it "decay"?

The epsolon value starts at 0.9 and ends at 0.05 with a decay of 1000. It starts with a very high epsilon meaning the model is going to take very large steps at the beginning of training to try new strategies. As the model learn, the epsilon value decays to take smaller and smaller steps as the model gets better at the game, it's beginning to learn. By the end of training, epsilon is pretty low so it's relying more on what it already knows to fine tune it's startegy of keeping the stick traight. 

### Gamma
Explain the purpose of the Gamma (𝛾) value.

Gamma determins the the weight given to the future rewards. By discounting future rewards, the agent is more interested in the payout from the next step, but if the future rewards are more valuable than the reward right in front of it, it may discount the next step for the greatest total payout down the line. In a game where keeping the stick up is an immediate thing, with little delayed gratification, you probably don't want to think too far down the line, as the stick probably won't be balanced at that point. Unless you keep it up with your next move. 
