# SocialNteworkAnalysisAssignment


Context / Explanation for the Monte Carlo Influence Spread Code

### **1. Introduction**

In Social Network Analysis (SNA), many phenomena such as rumor spreading, information diffusion, viral marketing, and contagion processes cannot be predicted deterministically.
To study these uncertain processes, we use **Monte Carlo Simulation**, a repeated random sampling technique that estimates the expected behavior of a network under probabilistic conditions.

This assignment implements a **Monte Carlo simulation of influence spread** using the **Independent Cascade (IC) Model**, a widely used diffusion model in social networks.

---

## **2. Problem Definition**

Given a social network represented as a graph and a set of initially “influential” nodes (called **seed nodes**), we want to answer:

> *How much of the network can these seeds influence on average?*

However, influence spread is **random**:
Every node influences each of its neighbors **with a probability p**, so the process must be repeated many times to estimate the *expected* spread.

This is why Monte Carlo simulation is ideal.

---

## **3. Independent Cascade (IC) Model**

The IC model follows these rules:

1. A small set of seed nodes starts activated (influenced).
2. Each activated node gets **one chance** to activate each neighbor with probability *p*.
3. Newly activated nodes will try to influence their neighbors in the next round.
4. The diffusion stops when **no new nodes get activated**.

This makes the process evolve in multiple “waves,” similar to how information spreads in real social networks.

---

## **4. Why Monte Carlo?**

Since each activation attempt is random, a single simulation won’t reflect the true expected spread.

Therefore, the algorithm is repeated **N times** (e.g., 1000 simulations), and we compute:

* **Expected influence spread**
* **Maximum spread observed**
* **Minimum spread observed**

This gives a statistical, unbiased estimate of influence propagation.

---

## **5. How the Code Works**

### **(A) Graph Representation**



```python
graph = { 
    0:[1,4],
    1:[0,2,3],
    …
}
```

This shows understanding of fundamental SNA data structures.

---

### **(B) Independent Cascade model**

The function `independent_cascade()` performs one simulation:

* Maintains sets of **activated** and **newly activated** nodes
* Iteratively tries to activate neighbors
* Applies probability checks using `random.random()`
* Returns the total number of influenced nodes

This models the real spread of influence.

---

### **(C) Monte Carlo Loop**

The function `monte_carlo_influence()`:

* Runs the cascade model many times
* Stores the spread size from each run
* Computes summary statistics (mean, max, min)

This is the core Monte Carlo engine.

By Govind Bansal
229309254
IOT A 
