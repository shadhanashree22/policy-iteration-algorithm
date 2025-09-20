# POLICY ITERATION ALGORITHM
## AIM
Implement policy iteration algorithm to find optimal policy by iteratively maximizing the value function. 

## PROBLEM STATEMENT
Finding the optimal policy to start from start state and reach goal state in the frozen lake environment using policy iteration.

## POLICY ITERATION ALGORITHM
# Step 1:
Import required libraries.
# Step 2:
Load the frozen lake environment.
# Step 3:
Define the value evaluation, value improvement and value iteration functions.
# Step 4: 
Run the functions and display the results.

## POLICY IMPROVEMENT FUNCTION
### Name: S V SHADHANASHREE
### Register Number: 212223230202
```python
def policy_improvement(V,P,gamma=1.0):
  Q=np.zeros((len(P),len(P[0])),dtype=np.float64)
  for s in range(len(P)):
    for a in range(len(P[s])):
      for prob, next_state, reward, done in P[s][a]:
        Q[s][a]+=prob*(reward+gamma*V[next_state]*(not done))
      new_pi=lambda s: {s:a for s,a in enumerate(np.argmax(Q, axis=1))}[s]
  return new_pi
```
## POLICY ITERATION FUNCTION
### Name: S V SHADHANASHREE
### Register Number: 212223230202
```python
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
<img width="781" height="386" alt="Screenshot 2025-09-20 104744" src="https://github.com/user-attachments/assets/f8d4c316-ebd7-48ab-80cb-9d8a84058e09" />



## RESULT:
Therefore, policy iteration algorithm to find optimal policy by iteratively maximizing the value function is successfully implemented.
