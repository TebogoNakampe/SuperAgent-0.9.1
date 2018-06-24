# SuperAgent-0.9.1
Q-Learning Algorithm

Q-Learning is an Off-Policy algorithm for Temporal Difference learning. It can be proven that given sufficient training under any  -soft policy, the algorithm converges with probability 1 to a close approximation of the action-value function for an arbitrary target policy.

<p align="center">
  <img width="460" height="300" src="https://github.com/TebogoNakampe/SuperAgent-0.9.1/blob/master/SA.ai.PNG">
</p>

Q-Learning learns the optimal policy even when actions are selected according to a more exploratory or even random policy.
The iterative algorithm for SARSA is as follows:

                                                # Q(st,at)←Q(st,at)+α[rt+γQ(st+1,at+1−Q(st,at)],
                                                where rr is the reward, γγ is the discount factor, ss is the state, aa is the action, tt                                                   is the time.

The SARSA algorithm is a stochastic approximation to the Bellman equations for Markov Decision Processes. One way of writing the Bellman equation for qπ(s,a)qπ(s,a) is:

                                # qπ(s,a)=∑s′,rp(s′,r|s,a)(r+γ∑a′π(a′|s′)qπ(s′,a′))
                                Where p(s′,r|s,a)p(s′,r|s,a) is the probability of transition to state s′s′ with reward rr given current                                 state ss and action aa
TD learning, including SARSA and Q-Learning, uses the ideas of Dynamic Programming in a sample-based environment where the equalities are true in expectation. But essentially you can see how the update qπ(s,a)=∑s′,rp(s′,r|s,a)(r+γ∑a′π(a′|s′)qπ(s′,a′))qπ(s,a)=∑s′,rp(s′,r|s,a)(r+γ∑a′π(a′|s′)qπ(s′,a′)) has turned into SARSA's update:

The weighted sum over state transition and reward probabilities happens in expectation as you take many samples. So Q(S,A)=E[Sampled(R)+γ∑a′π(a′|S′)qπ(S′,a′)]Q(S,A)=E[Sampled(R)+γ∑a′π(a′|S′)qπ(S′,a′)] (technically you have to sample R and S' together)
Likewise the weighting of the current policy happens in expectation. So Q(S,A)=E[Sampled(R+γQ(S′,A′))]Q(S,A)=E[Sampled(R+γQ(S′,A′))]
To change this expectation into an incremental update, allowing for non-stationarity as the policy improves over time, we add a learning rate and move each estimate towards the latest sampled value: Q(S,A)=Q(S,A)+α[R+γQ(S′,A′)−Q(S,A)

This Project was inspired by UNITY Technologies Q-GridWorld Project:
https://github.com/Unity-Technologies/Q-GridWorld

The goal when doing Reinforcement Learning is to train an agent which can learn to act in ways that maximizes future expected rewards within a given environment. In the last post in this series, that environment was relatively static. The state of the environment was simply which of the three possible rooms the agent was in, and the actions were choosing which chest within that room to open. Our algorithm learned the Q-function for each of these state-action pairs: Q(s, a). This Q-function corresponded to the expected future reward that would be acquired by taking that action within that state over time. 



To test on your local machine, please select the game scene and press play.

 -InternalAgent.cs contains all of the Q-learning logic.
 
 -GridEnvironment.cs contains all of the environment-specific logic.


