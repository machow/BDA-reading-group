Deriving poisson from binomial
===================
<div id="tags" style="display:none">BDA, distribution, probability</div>

Proof
-------------------
Imagine a binomial process, bin(x; n, $\pi$) that returns some event with a mean $\lambda$, regardless of the
number of times it's sampled (for example, if you expect 5 people to arrive a minute).
Then, $\lambda = n\pi \iff \frac{\lambda}{n} = \pi$. As samples, $n$, increase, converges to poisson.

1. $\lim\limits_{n \to \infty} \text{bin}(x; n, \pi) = \frac{n!}{x!(n-x)!}\frac{\lambda^x}{n^x}(1-\frac{lambda}{n})^{n - x}$
2. Last part split by both parts of exponent. $\lim\limits_{n \to \infty}(1 - \frac{\lambda}{n})^n = e^\lambda$, other is 1
3. $\lim\limits_{n \to \infty}\frac{(n)...(n - x + 1)}{n^x} = 1$, since $x$ terms with $n$ on top and bottom (can ignore constants).

Therefore, $\lim\limits_{n \to \infty}\text{bin}(x; n, \frac{\lambda}{n}) = \frac{\lambda^xe^\lambda}{x!}$

Derive exponential from poisson
===================
<div id="tags" style="display:none">BDA, probability, distribution</div>

Overview
-------------------
While the poisson distribution asks how many hits to expect in a unit of time,
the exponential distribution asks how much time until a hit. How can you go from poisson -> exp?

Proof
-------------------
Define the same event two ways:

$X_t$: time from $t$ until next hit

$N_t$: number of hits up to time $t$

1. $\Pr(X_t > x) \equiv \Pr(N_t = N_{t+x})$, i.e. no new event in $[t, t+x]$
2. $\Pr(N_{t+x} - N_t = 0) = \Pr(N_x = 0) = Poisson(0; \lambda x) = e^{-\lambda x }$
3. $\Pr(X < x) = 1 - e^{-\lambda x}$, which is the CDF of the exponential dist

By taking the derivative w.r.t. $x$, we get the pdf.

Deriving Gamma from Poisson
===================
<div id="tags" style="display:none">PDA, probability, distribution</div>

Overview
-------------------
While the exponential distribution is time until first hit, the gamma distribution, g($\beta$, $\alpha$), is time
until $\alpha^{\text{th}}$ hit.

Theorem
-------------------
Derive $g(t ; \beta, \alpha) = \frac{\beta^\alpha t^{\alpha-1} e^{-\beta t}}{\Gamma(\alpha)}$

Steps
-------------------
$S_\alpha$: time at $\alpha$ hits

$N_t$: number of hits at $t$

1. $\Pr(S_{\alpha} > t) = \Pr(N_t < \alpha) = \cup_{i=0}^{\alpha-1} \Pr(N_t = i)$
2. This is just sum of poissons
3. CDF: $\Pr(_{\alpha} \leq t)$ is just one minus RHS above
4. Take derivative, creates telescoping sum, only $\alpha-1$ component remaining
5. Remember that $\Gamma(\alpha) = (\alpha - 1)!$
