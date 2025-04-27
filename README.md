# final_project_description

The final project is open-ended. The task is to program a SuperTuxKart ice-hockey player. You have two options: An image-based agent and a state-based agent. You need to pick one route and cannot compete in both.

Both agent types have the same objective, score as many goals as possible and win the match. However, they have different inputs and performance requirements. For each we play 2 vs 2 tournaments against agents the TAs and I coded up.

Image based agents
An image-based agent gets access to the state of the players karts. The agent also sees an image for each player, from which it can infer where the puck is and where the other teams players are. However, it does not get access to the state of the puck or opponents during the gameplay.

We anticipate to see some vision-heavy solutions here. Choose this path if you prefer to work on the vision component of your agent and use a hand-tuned controller. This option may require more compute to develop and test.

Implement image_agent/player.py.

Special rules
You need to use a deep network to process the images
You may use any controller you want (hand-designed or even some of the agents the TAs and I coded up)
Time limit 50ms per step (call to the Team.act function) on a reasonable fast GPU
State based agents
A state-based agent gets access to the state of the players karts, the opponents' kart, and the location of the ball. There is no vision required here.

We anticipate to see some learning-based solution here. Choose this path if you prefer to work on the control component of your agent.

Implement state_agent/player.py.

Special rules
Your agent needs to be a single deep network, no hand-designed components are allowed.
Your agent should be a torch.jit.script. This is required and no exceptions.
Time limit 10ms per step (call to the Team.act function) on a reasonable fast GPU
You are not allowed to use parts of the test agent models in your model for submission. Note that image_jurgen_agent is also a state based agent.
Examples of acceptable usage of test agents:
Using test agents to play against each other to generate training dataset for imitation learning
Using test agents as opponents for reinforcement training
Looking at the model structure of our test agents and training a new model with a similar structure
Examples of violations of the rules:
Using the pre-trained parameters from the test agents we provided
Building a wrapper model that uses the test agents we provided/importing our model.th file with minor changes to data preprocessing
Fine tuning our pre-trained test agent models with a new dataset and submit it as your model
Getting started
In both bases you will implement Team object in player.py. This class provides an act function, which takes inputs as described above and produces a list of actions (one per player). The current agents will simply drive straight as an example.

You can test your agents against each other or the build-in AI

python -m tournament.runner image_agent AI
The tournament runner has quite a few arguments you can explore using the -h flag. The most important include recording a video -r my_video.mp4 or saving data -s my_data.pkl.

General rules
This project is completely open-ended, however, there are a few ground rules:

You may work in a team of up to 4 students.
Teams may share data, but not code.
We will provide some test agents to compete against towards the end of the project.
In our grader, your agent will run in complete isolation from the rest of the system. Any attempt to circumvent this will result in your team failing.
You may use pystk and all its state during training, but not during gameplay in the tournament.
Your code must be efficient. If you violate the time-limit your forfeit the match.
The tournament (extra credit)
We will play two ice hockey tournaments, one for each type of agent, for those teams that complete the appropriate google form linked in the Final Proejct Instructions found on Canvas. Two of your agents will play two opponents. Each game will play up to 3 goals, or a maximum of 1200 steps (2 minutes). The team with more goals wins. Should one of the teams violate the above rules, it will lose the game. Should both teams violate the rules, the game is tied.

The submission with the most victories wins the tournament. The goal difference breaks ties. Additional, matches further break ties.

Sanity checks
You may run the local grader on your solution similar to previous assignments. Feel free to upload to canvas once your submission passes the local grader.

Grading
The coding portion of the assignment is worth a total 30pts, and the report is worth 70 pts. For the coding portion,

30pts average number of goals scored per game. Linearly from 0 to 1. We will compute the average against the TAs agents.
15 pts extra credit for the top 3 teams per agent type in the competition (15pts winner, 10pts second, 5pts third).
For the report, please see the rubric and instructions on Canvas. Links to both documents can be found on the assignment page for the Final Project Report and additionally under Files-->Final Project Documents.

The canvas grader will report your final grade for the coding portion of this assignment.

You have a soft limit of 5 submissions for the canvas grader. The grader will likely be very, very busy (20+min per submission), and there may be delays of up to 24h to get a reply during peak submission times. Please plan ahead and make sure your code runs fast.

Similar to all of the previous assignments, only the score of your final submission will count.

Hints
Test your code on a Linux machine (either CS lab or colab).
Start early.
Submission
Once you finished the project, create a submission bundle using

python bundle.py agent [YOUR UT ID]
and submit it under the 'Final Project' assignment. Submit your writeup as a pdf under the 'Final Project report' assignment.
