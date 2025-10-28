<img width="737" height="165" alt="image" src="https://github.com/user-attachments/assets/4904f110-3be7-48d6-b8a2-ffdc4978a1e3" /># POLICY ITERATION ALGORITHM

## AIM
The aim of this experiment is to implement the Policy Iteration Algorithm in Reinforcement Learning to determine the optimal policy and corresponding value function for a given environment. Policy Iteration combines iterative policy evaluation and policy improvement steps to achieve convergence towards an optimal policy.

## PROBLEM STATEMENT
In Reinforcement Learning, the agent interacts with an environment modeled as a Markov Decision Process (MDP).
The challenge is to find an optimal policy that maximizes the long-term cumulative reward.
Policy Iteration addresses this by:

Evaluating the value of a given policy (Policy Evaluation).
Improving the policy based on the evaluated value function (Policy Improvement).
Repeating these steps until the policy converges to the optimal policy.

## POLICY ITERATION ALGORITHM
# STEP 1:
Initialization

Initialize an arbitrary policy π and value function V(s).
A
# STEP 2:
Policy Evaluation

For the current policy π, compute the value function V(s) for all states until convergence.

# STEP 3:
Policy Improvement

Update the policy by choosing actions that maximize the expected return using the current value function.
# STEP 4:
Check for Convergence

If the policy does not change (π′ = π), then the policy is optimal and the algorithm terminates.
Otherwise, repeat steps 2 and 3.

## POLICY IMPROVEMENT FUNCTION
### Name: MUKESH R
### Register Number: 212223240100
```
def policy_improvement(V, P, gamma=1.0):
    Q = np.zeros((len(P), len(P[0])), dtype=np.float64)

    for s in range(len(P)):
        for a in range(len(P[s])):
            for prob, next_state, reward, done in P[s][a]:
                Q[s][a] += prob * (reward + gamma * V[next_state] * (not done))

    new_pi = lambda s: {s: a for s, a in enumerate(np.argmax(Q, axis=1))}[s]

    return new_pi

```
## POLICY ITERATION FUNCTION
### Name: BALASURAMANIAM L
### Register Number: 21224240020
```
def policy_iteration(P,gamma=1.0,theta=1e-10):
  random_actions=np.random.choice(tuple(P[0].keys()),len(P))
  pi=lambda s: {s:a for s, a in enumerate(random_actions)}[s]
  while True:
    old_pi={s: pi(s) for s in range(len(P))}
    V=policy_evaluation(pi,P,gamma,theta)
    pi=policy_improvement(V,P,gamma)
    if old_pi=={s:pi(s) for s in range(len(P))}:
      break
  return V,pi

```

## OUTPUT:
### 1. Policy, Value function and success rate for the Adversarial Policy
<img width="737" height="165" alt="image" src="https://github.com/user-attachments/assets/d2df44e3-fae4-4ac5-908f-5ae9eeb699f0" />
<img width="737" height="165" alt="image" src="https://github.com/user-attachments/assets/460c17f8-00cc-40b6-b2d6-626dbb00ad78" />



### 2. Policy, Value function and success rate for the Improved Policy
<img width="737" height="165" alt="image" src="https://github.com/user-attachments/assets/a6ebaa9f-ff5d-4ec5-8d7e-8a7ae9d375b7" />
<img width="737" height="165" alt="image" src="https://github.com/user-attachments/assets/bb5cf39d-d515-4c16-a428-9e8d73fecf55" />



### 3. Policy, Value function and success rate after policy iteration
<img width="737" height="159" alt="image" src="https://github.com/user-attachments/assets/aae1dcdf-0e97-44ab-9df4-0aa239c60a5f" />

<img width="737" height="159" alt="image" src="https://github.com/user-attachments/assets/c856d0c5-e55f-4dee-a0c1-12e74fb95d00" />

## RESULT:
Therefore, policy iteration algorithm to find optimal policy by iteratively maximizing the value function is successfully implemented.




## RESULT:
Therefore, policy iteration algorithm to find optimal policy by iteratively maximizing the value function is successfully implemented.
