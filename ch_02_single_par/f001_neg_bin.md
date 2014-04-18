Negative Binomial
===================
<div id="tags" style="display:none">BDA, probability, distribution</div>

Overview
-------------------
This distribution represents the probability of $s$ successes before $f$ failures, given a probability of sucess, $p$.

PMF
-------------------
$$
NB(s; f, p) = \binom{s + f - 1}{s} p^s(1 - p)^f
$$

We need to count how many times the event $s$ successes, $f$ failures occurs, times the prob of that event.
However, the last event has to be a failure (thus, $s + f - 1$)
