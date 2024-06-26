---
layout: article
title: Options Advantage - Why More Options IS Better
custom_css: article.css
include_mathjax: true
---
## Modeling Options
One way to think about *options* is simply to model them as a *binary* game where there are two *players*, and only
*two outcomes*, winning (`W`) or losing (`L`):

$$
P(\text{losing}) + P(\text{winning}) = p_l + p_w = 1
$$

Or to put it another way, which will be useful shortly, we can write:

$$
P(\text{winning}) = 1 - P(\text{losing})
$$

## Games of Constant Probability
Now let us consider a *series of games*, where the outcome is denoted by a `W` for a *win* and a `L` for a *loss*, and for simplicity's sake let us consider a *fair coin toss* as the game, and for now only do *1 trial* (i.e. $n = 1$). We can then easily calculate the $2^n = 2^1 = 2$ outcomes and visualize them as *strings*:

$$
\{W, L\}
$$

We can easily see there is only *1* outcome where we win out of the $2^n = 2^1 = 2$ total outcomes, and hence the *probability* of *"winning at least one game"* is:

$$
P(\text{winning at least once}) = \frac{1}{2}
$$

Now let us repeat the game for *2 trials* (i.e $n = 2$), which creates $2^n = 2^2 = 4$ outcomes:

$$
\{WW, WL, LW, LL\}
$$

We can see that, in the scenario where we are only concerned with *"winning at least one game"* then we have *3 different ways* to *"win"* out of the $2^n = 2^2 = 4$ total outcomes:

$$
\{WW, WL, LW\}
$$

The *probability* of *"winning at least one game"* is then:

$$
P(\text{winning at least once}) = \frac{3}{4}
$$

If we repeat the same *series of games* but use *3 trials* (i.e. $n = 3$), we now have $2^n = 2^3 = 8$ outcomes:

$$
\{WWW, WWL, WLW, WLL, LWW, LWL, LLW, LLL\}
$$

We can see that, in the scenario where we are only concerned with *"winning at least one game"* then we have *7 different ways* to *"win"* out of $2^n = 2^3 = 8$ total outcomes:

$$
\{WWW, WWL, WLW, WLL, LWW, LWL, LLW\}
$$

And the *probability* of *"winning at least one game"* is then:

$$
P(\text{winning at least once}) = \frac{7}{8}
$$

So in general, for this *fair toss game* the ways in which we can *"win at least one game"* in a series of games (i.e. 
multiple trials) follows this pattern:

$$
P(\text{winning at least once}) = \frac{2^n - 1}{2^n}
$$

which simplifies further:

$$
\begin{align*}
    P(\text{winning at least once}) &= \frac{2^n - 1}{2^n} \\
    &= \frac{2^n}{2^n} - \frac{1}{2^n} \\
    &= 1 - \left(\frac{1}{2}\right)^n
\end{align*}
$$

This formula can the be further *abstracted* for the *probability of the fair coin toss game* (i.e. $p_l = \frac{1}{2} $) and
we are back to our starting formulation:

$$
\begin{align*}
    P(\text{winning at least once}) &= 1 - \left(\frac{1}{2}\right)^n \\
    &= 1 - p_l^n \\
    &= 1 - P(\text{losing})^n
\end{align*}
$$

and we can now see that the starting formula is just a special case of $n = 1$:

$$
\begin{align*}
    P(\text{winning}) &= 1 - P(\text{losing})^n \\
    &= 1 - P(\text{losing})^1 \\
    &= 1 - P(\text{losing})
\end{align*}
$$


## Games of Variable Probability
But what about games where each *game in the series* (i.e. trial) has a different probability:

$$
p_i \neq p_{i+1} \neq \ldots \neq p_n
$$

We can generalize the formula to work with *variable probabilities* as follows:

$$
\begin{align*}
    P(\text{winning}) &= 1 - \prod_{i=1}^{n} P(\text{losing}) _ i \\
    &= 1 - \prod_{i=1}^{n} p_i
\end{align*}
$$

Where:
+ $p_i$ is the *probability* of your **opponent winning** (i.e. $P(\text{losing}) $) the `i-th` game out of `n` total games
+ $0 < p_i < 1$
+ all $p_i$ are independent:

$$
P\left(\bigcap_{i=1}^{n} p_i\right) = \prod_{i=1}^{n} P(p_i)
$$


## Advantage at Infinity
As the number of games `n` approaches a greater and greater number, the *player's advantage* (i.e. the player's *probability* of winning *at least* one game) approaches $1$ or 100% (i.e. they are guaranteed to win *at least* one game):

$$
\lim_{n \to \infty} \left(1 - \prod_{i=1}^{n} p_i\right) = 1
$$


## Moral
What we can see from the above formulas is that the more *options* your or your *oponent* possess, the greater
their advantage (i.e. the *higher probability* they will *win at least one game*). Even if the $p_l$ is high (meaning a high probability of losing), the more *options* added, the more the $p_w$ (probability of *winning at least once*) will approach unity (i.e. 100%).
