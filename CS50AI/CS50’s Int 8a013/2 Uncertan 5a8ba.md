# 2. Uncertanity

given observations from start until now,
calculate distribution for past state

# Probability

### Possible Worlds

- $P(\omega)$: probability of possible world $\omega$

$$
0 \leq P(\omega) \leq 1 \\
\sum_{\omega \in \Omega} P(\omega) = 1
$$

- Unconditional Probability: 
degree of belief in a proposition in the absence of any other evidence
- Conditional Probability: 
degree of belief in a proposition given some evidence that has already been revealed
    - $P(a|b)$: The probability $a$ is true given that $b$ is true.
    - e.g. $P(rain \space today | rain \space yesterday)$
    - The calculation of $P(a|b)$
        
        $$
        P(a|b) = {{P(a\land b)} \over {P(b)}} \\ 
        P(a\land b) = P(b) P(a|b) = P(a) P(b|a)
        $$
        
- Random Variable: 
a variable in probability theory with a domain of possible values it can take on
    - e.g.) Roll → {1,2,3,4,5,6}
    - e.g.) Traffic → {none, light, heavy}
- Probability Distribution
    - $P(Flight = on time) = 0.6$
    - $P(Flight = delayed) = 0.3$
    - $P(Flight = cancelled) = 0.1$
    - $\bold{P}(Flight) = <0.6,0.3,0.1>$ expression using vector
- Independence:
the knowledge that one event occurs does not affect the probability of the other event.
    - $P(a\land b) = P(a) P(b|a) = P(a)P(b)$

## Bayes’ Rule

$$
P(b)P(a|b) = P(a)P(b|a) \\
P(b|a) = \frac{P(a|b)P(b)}{P(a)}
$$

- Example
    - Given clouds in the morning, what’s the probability of rain in the afternoon?
        - 80% of rainy afternoons start with cloudy mornings.
        - 40% of days have cloudy mornings.
        - 10% of days have rainy afternoons.
        - $P(rain|clouds) = \frac{P(clouds|rain)P(rain)}{P(clouds)} = 0.2$
- Knowing $P(Visible~effect~|~unknown~cause)$,
we can calculate $P(unknown~cause~|~visible~effect)$

## Joint Probability

- tells probability distributions of each possible combinations of values
- can get other informations like conditional probability from joint probability

$$
P(C|rain) = \frac{P(C,rain)}{P(rain)} = \alpha P(C,rain)
$$

## Probability Rules

- **Negation**

$$
P(\lnot a) = 1-P(a)
$$

- **Inclusion-Exclusion**

$$
P(a \lor b) = P(a) + P(b) - P(a\land b)
$$

- **Marglinalization**

$$
P(a) = P(a\land b) + P(a\land \lnot b) \\ P(X_i) = \sum_{j} P(X=X_i , Y=Y_j)
$$

- **Conditioning**

$$
P(a) = P(a|b)P(b) + P(a|\lnot b)P(\lnot b) \\
P(X_i) = \sum_j P(X=X_i| Y=Y_j)P(Y_j)
$$

## Bayesian Networks

- Bayesian Network:
data structure that represents the dependencies among random variables
- directed graph
- each node represents a random variable
- arrow from $X$ to $Y$ means $X$  is a parent of $Y$
- each node $X$ has probability distribution $P(X|Parents(X))$
- Example
    
    ![Untitled](2%20Uncertan%205a8ba/Untitled.png)
    
    - Computing Joint Probabilities
        
        $P(light, no, delayed, miss)$
        
        ⇒ $P(light) P(no|light)P(delayed|light, no)P(miss|delayed)$
        

## Inference

- Query $X$: variable for which to compute distribution
(something that I want information about)
- Evidence variables $E$: observed variables for event $e$
- Hidden variables $Y$: non-evidence, non-query variable.
- GOAL: Calculate $P(X|e)$
- $P(Appointment | light, no) \\ = \alpha P(Appointment, light, no) \\ = \alpha [P(Appointment, light, no, on time) + P(Appointment, light, no, delayed)]$

## Inference by Enumeration

$$
P(X|e) = \alpha P(X,e) = \alpha \sum_y P(X,e,y)
$$

- $X$ is the query variable.
- $e$ is the evidence.
- $y$ ranges over values of hidden variables.
- $\alpha$ normalizes the result.

**In Python ...**

use `pomegranate` library

## Approximate Inference

Sampling

Rejection Sampling

## Likelihood Weighting

sampling method

- Start by fixing the values for evidence variables.
- Sample the non-evidence variables using conditional prbabilities in the Bayesian Network.
- Weight each sample by its **likelihood**: the probability of all of the evidence.
- 

## Uncertanity over Time

$X_t$: Weather on time $t$

### Markov assumption

the assumption that the current state depends on only a finite fixed number of previous states

### Markov chain

a sequence of random variables where the distribution of each variable follows the Markov assumption

- Transition model: the description of transition from one state to the next state.

### Sensor Models

| Hidden State | Observation |
| --- | --- |
| robot’s position | robot’s sensor data |
| words spoken | audio waveforms |
| user engagement | website or app analytics |
| weather | umbrella |

### Hidden Markov Model

a Markov model for a system with hidden states that generate some observed event

### sensor Markov assumption

the assumption that the evidence variable depends only the corresponding state

| Task | Definition |
| --- | --- |
| filtering | given observations from start until now, calculate distribution for current state |
| prediction | given observations from start until now, calculate distribution for a future state |
| smoothing | given observations from start until now, calculate distribution for a past state |
| most likely explanation | given observations from start until now, calculate most likely sequence of states |