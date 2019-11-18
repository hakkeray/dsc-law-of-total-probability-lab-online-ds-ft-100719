
# Partitioning and Law of Total Probability - Lab

## Introduction 
In this lab, you'll practice your knowledge of the law of total probability. In probability theory, the law (or formula) of total probability is a fundamental rule relating **marginal probabilities** to **conditional probabilities**.

## Objectives

You will be able to:

* Differentiate between independent and dependent events
* Perform partitioning based on known and unknown probabilities to solve a problem

## Exercise 1
Imagine you have two hats: one has 4 red balls and 6 green balls, the other has 6 red and 4 green. We toss a fair coin, if heads, you will pick a random ball from the first hat, if tails you will pick one from the second hat. 

What is the probability of getting a red ball?


```python
# Heads: 4 red, 6 green -> p(red) = 4/10
# Tails: 6 red, 4 green -> p(red) = 6/10
# Heads or Tails = 1/2 or 0.5
# p_Red = p_RgivH * p_H + p_RgivT * p_T

p_Red = (4/10 * 0.5) + (6/10 * 0.5)
print(p_Red)
```

    0.5


## Exercise 2
In games where at least one goal is made, a soccer team wins 60% of its games when it scores the first goal, and 10% of its games when the opposing team 
scores first. 

If the team scores the first goal about 30% of the time, what fraction of the games does it win?


```python
# P_win_giv_score_first = 0.6
# P_win_giv_score_second = 0.1
# P_score_first = 0.3
# therefore P_score_second = 1 - 0.3 = 0.7
# P_win = ?
p_w = (0.6 * 0.3) + (0.1 * 0.7)
p_w
```




    0.25



## Exercise 3

In Europe, except for regular gas, cars often run on diesel as well. At a gas station in Paris; 


* 40% of the customers fill up with diesel (event G1) 
* 35% with gas "Super 95" (event G2)
* 25% with gas "Super 98" (event G3). 


* 30% of the customers who buy diesel fill their tank completely (event F). 
* For "Super 95" and "Super 98", these numbers are  60% and 50%, respectively.


- Compute the probability that the next customer completely fills their tank and buys Super 95. 
- Compute the probability that the next customer completely fills their tank
- Given that the next customer fills their tank completely, compute the probability that they bought diesel. 

Hint: Consult the theorems for conditional probability, check for dependence or independence of events


```python
G1 = 0.4 # Diesel
G2 = 0.35 # Super95
G3 = 0.25 # Super98
F1 = 0.3 # Diesel, FullTank
F2 = 0.6 # 95 FullTank
F3 = 0.5 # 98 FullTank

# Full Tank and Super 95
P_G2_F2 = G2*F2
P_G2_F2
```




    0.21




```python
P_G1_F1 = G1*F1
P_G3_F3 = G3*F3

P_Full_Any = P_G1_F1+P_G2_F2+P_G3_F3
P_Full_Any
```




    0.45499999999999996




```python
P_G1_giv_F1 = (G1*F1)/P_Full_Any
P_G1_giv_F1
```




    0.26373626373626374



## Exercise 4

United Airlines operates flights from JFK to Amsterdam, to Brussels, and to Copenhagen. As you may know, flights are overbooked fairly often. Let's denote the probability of the flight to Amsterdam being overbooked equal to 40%, the probability of the flight to Brussels being overbooked equal to 25%, and the probability of the flight to Copenhagen being overbooked equal to 35%. You can assume that these events of overbooking are independent events.

- Compute the probability that all the flights are overbooked.
- Compute the probability of having at least one flight which is not overbooked.
- Compute the probability that exactly one flight is overbooked.


```python
p_Am = 0.40
p_Br = 0.25
p_Co = 0.35
p_all = p_Am*p_Br*p_Co
p_all
```




    0.034999999999999996




```python
p_1notOB = 1 - p_all
p_1notOB
```




    0.965




```python
p_Am1 = p_Am * (1-p_Br) * (1-p_Co)
p_Br1 = p_Br * (1-p_Am) * (1-p_Co)
p_Co1 = p_Co * (1-p_Am) * (1-p_Br)

p_1OB = p_Am1 + p_Br1 + p_Co1
p_1OB
```




    0.45000000000000007



## Exercise 5
You have three bags that each contain 100 marbles:

- Bag 1 has 75 red and 25 blue marbles;
- Bag 2 has 60 red and 40 blue marbles;
- Bag 3 has 45 red and 55 blue marbles.

You choose one of the bags at random and then pick a marble from the chosen bag, also at random. 

What is the probability that the chosen marble is red?



```python
B1 = .75
B2 = .60
B3 = .45
pBag = 1/3 
p_red = (B1*pBag)+(B2*pBag)+(B3*pBag)
p_red
```




    0.6



## Summary 

In this lab, you practiced conditional probability and its theorem with some simple problems. The key takeaway from this lab is to be able to identify random events as dependent or independent and calculating the probability of their occurrence using appropriate methods. Next, you'll take this knowledge a step further and run simulations with conditional and total probability. 
