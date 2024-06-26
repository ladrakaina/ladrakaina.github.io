---
layout: article
title: Gambler's Fallacy - A Problem Ill-defined
custom_css: article.css
include_mathjax: true
---
## Monte Carlo
The origins of the [Gambler's Fallacy](https://en.wikipedia.org/wiki/Gambler%27s_fallacy) comes from a famous story about a *[roulette](https://en.wikipedia.org/wiki/Roulette)* streak in the [Monte Carlo](https://en.wikipedia.org/wiki/Monte_Carlo_Casino) casino. Basically the streak was *sequential black* on 26 spins of the roulette wheel. As the streak continued, more people began betting. But what is *fallacious* about this behavior?

## The Problem
The mistake in the *Gambler's Fallacy* is simply a misunderstanding of the problem. Since every spin of the wheel is *independent* then the past states (read `R` or black `B`) do not affect the future. In mathematical terms:

$$
P\left(\bigcap_{i=1}^{n} p_i\right) = \prod_{i=1}^{n} P(p_i)
$$

Basically $P$ represents the *streak probability* and $p_i$ represents the probability of either `R` or `B` (which each have probability of $\frac{1}{2}$). So then the question of *predicting* the probability of the *27th* spin of the wheel is simply the same for either `R` or `B`:

$$
\begin{align}
\text{P(BBBBBBBBBBBBBBBBBBBBBBBBBBB)} &= \frac{1}{2^{27}} \\
\text{P(BBBBBBBBBBBBBBBBBBBBBBBBBBR)} &= \frac{1}{2^{27}}
\end{align}
$$

Instead what patrons of the *Monte Carlo Casino* were *intuitively* aware of is how **rare** getting a streak of pure `B` is in comparison to getting a *non-pure* combination (i.e. at least one `R` or one `B` in a streak of 27):

$$
\begin{align}
P(\neg (R_{27} \cup B_{27})) &= 1 - P(R_{27} \cup B_{27}) \\
&= 1 - \frac{2}{2^{27}} \\
&= 0.9999999850988388
\end{align}
$$

But still a *pure streak* (all `R` or all `B`) while rare, does not change the probability of the next spin being *either* `R` or `B`.

## Moral
When thinking about a problem it is extremely easy to misunderstand the *context* or *setup* of the problem, and instead frame the problem as a *different problem*. In this example, the patrons of the *Monte Carlo Casino* failed to grasp that the problem is **NOT** the probability of getting a *non-pure* streak (any combination other than all `B` or all `R`) but rather a simple *coin toss* (i.e. $P(\text{H}) = P(\text{T}) = \frac{1}{2}$).
