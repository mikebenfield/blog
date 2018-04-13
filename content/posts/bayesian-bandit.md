---
title: "Two Bayesian Approaches to the Multi-Armed Bandit Problem"
date: 2018-04-12
---

# Background: The Multi-Armed Bandit

The multi-armed bandit is a classic problem in artificial intelligence that
illustrates the exploitation vs. exploration dilemma. Here's the idea: suppose
you're sitting in front of a special slot machine with M different levers. Each
lever i has a probability $p_i$ of giving you a payoff when you pull it. You
don't know the probabilities $p_i$. So you start pulling levers, and before long
you have some estimates of the probabilities based on the proportion of times
each lever has given you a reward.

So you could focus on the lever that has given you the highest proportion of
rewards so far, or you could pull other levers to further explore their reward
probability, on the chance that you haven't pulled them enough times yet to get
a good estimate of their probability. That is, exploitation vs. exploration.

For this post we're going to use a finite horizon, meaning we only get $N$ total
pulls and then we have to stop.

(The multi-armed bandit problem has many different setups, and may be more
general than this: it may be that the reward for each unknown is drawn from an
unknown probability distribution, instead of just from a Bernoulli distribution
with unknown mean. Also, an infinite horizon is often used. But this simple
setup is what I'll focus on here.)

# A Dynamic Programming Bayesian Approach

So yesterday I was thinking about this problem, and I thought: why not use a
simple Bayesian approach? Let the reward (0 or 1) of lever $i$ the $j$th time
(starting at $j=0$) it is pulled be the random variable $X^i_j$. Let the
distribution of $X^i_j$ be $\operatorname{Beta}(\alpha^k_j, \beta^i_j)$
[^beta_footnote],
where $\alpha_0$ and $\beta_0$ are chosen to make an appropriate prior and

$$\alpha^i_{j+1} = \alpha^i_j + X^i_j$$

and

$$\beta^i_{j+1} = \beta^i_j + 1 - X^i_j .$$


[^beta_footnote]: Recall that, roughly speaking, $\operatorname{Beta}(\alpha, \beta)$ is a distribution of the probability of success if you have observed $\alpha$ successes and $\beta$ failures so far.

Thus, each time we observe a success or failure on a given lever, we update our
prior probability for that lever to reflect the new information.

Then this becomes like a discrete time optimal control problem. Our states are
the current pairs $(\alpha^i_j, \beta^i_j)$ for each lever. Each time step the
control we choose is a lever $i$, and we get a random reward $X^i_j$, and the
state is updated. We can use dynamic programming to solve this. At time step
$N-1$, we can simply choose the lever whose Beta distribution has the highest
mean, and at each earlier time we choose the lever that gives the highest
expected reward (adding the current reward and future expected rewards).

It's kind of an odd optimal control problem though, and I guess technically it
doesn't really count as one. The problem is that our random variables $X^i_j$
don't reflect the "real" distributions. That is, the rewards for each lever arm
in reality are supposed to be fixed (but unknown) probabilities, and if we were
going to simulate the multi-armed bandit, we'd have to choose those fixed
probabilities. But in our model, the distributions for each reward simply
reflect our belief at each time step about those probabilites.

Now, a little reflection will reveal a glaring problem with this approach.
Typically with dynamic programming, for a problem with $N$ time steps, $n$
states, and $m$ control elements, our runtime is $O(nmN)$. The problem in this
case is that the number of possible states $n$ grows exponentially with the
number of time steps $N$. That's not good, and it means this is not going to be
a viable approach in many cases. Still, maybe it could work well when $N$ is
small, or when it's medium sized and the policy can be computed ahead of time.

I wanted to compare this method with a classical Bayesian approach.

# Thompson Sampling

In Thompson sampling, we similarly assign Beta priors to each lever and update
them after each success or failure. But rather than trying to calculate
everything ahead of time as in dynamic programming, we simply observe successes
and failures as they happen. Then, each step, we sample a probability $p_i$ for
each lever $i$ from its Beta distribution. We pull the lever of whichever $p_i$
is largest. This neatly handles the exploration vs. exploitation issue.

# The Comparison

I ran 100 iterations each of a few different two-armed bandit problems, with
different fixed probabilities $(p_1, p_2)$. I used values of $N$ from 3 to 30.
The dynamic programming approach seems to usually give total rewards from
between 4% and 10% greater than the Thompson sampling approach, with a smaller
standard deviation. That's good, and it makes sense: dynamic programming
calculates ahead of time the policy that will give the highest expected reward
(at least given the priors we have chosen). Thompson sampling is stochastic, and
while in the long run it's almost certain to make reasonable choices, there's no
guarantee at any given step it will choose the control element giving the
highest expected reward.

So that's nice, and I think for some specialized problems there may be some
value in this approach. But it's not going to work out for a long horizon.

# Future

At some point I'd like to try out an approximate dynamic programming solution.
One possibility is to use rolling horizon approach, in which dynamic programming
is use for the next $\ell$ steps, but some form of cost estimation is used
beyond that, thus avoiding the exponential runtime. It seems plausible to me
that this would give comparable results to the full dynamic programming solution.
