# VALUE ITERATION ALGORITHM

## AIM
To develop a Python program to find the optimal policy for the given MDP using the value iteration algorithm.

## PROBLEM STATEMENT
To find the optimal policy for the mdp using value iteration algorithm instead of policy iteration which is slower than value iteration.

## POLICY ITERATION ALGORITHM
Firstly the state value function and action value function for all the states of mdp are initialized to zero then while iterating through actions of each state the value function and action value function is caluculated for each state then the maximum action value function of each state is taken to find the best ploicy.

## VALUE ITERATION FUNCTION
### Name: Koti Sai Sankar
### Register Number: 212222240111
### Include the value iteration function
```
def value_iteration(P, gamma=1.0, theta=1e-10):
    
    V=np.zeros(len(P), dtype=np.float64)
    while True:
      Q=np.zeros((len(P),len(P[0])), dtype=np.float64)
      for s in range(len(P)):
        for a in range(len(P[s])):
          for prob,next_state,reward,done in P[s][a]:
            Q[s][a]+=prob*(reward+gamma*V[next_state]*(not done))
      if np.max(np.abs(V-np.max(Q,axis=1)))<theta:
        break

      V=np.max(Q,axis=1)
      pi=lambda s: {s:a for s, a in enumerate(
          np.argmax(Q,axis=1))
     }[s]

    return V, pi
```

## OUTPUT:

![image](https://github.com/user-attachments/assets/19d90ca6-ea5d-4f9f-83f9-5b4b741e4c28)

![image](https://github.com/user-attachments/assets/f18a6960-a8aa-4f62-8118-89aa5559622c)

![image](https://github.com/user-attachments/assets/1878ea04-da4c-44d1-8b57-15ded41c8953)

## RESULT:
Thus, The Python program to find the Value Iteration for the given MDP using the Value Iteration Function is successfully executed.
