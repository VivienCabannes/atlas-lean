# Uniform deviation for a finite class

Let $\mathcal{F}$ be a finite nonempty set of predictors, let $\ell$ be a measurable loss with
values in $[0, \ell_\infty]$ for some $\ell_\infty > 0$, and let $z_1 = (x_1, y_1), \dots,
z_n = (x_n, y_n)$, with $n \ge 1$, be independent and identically distributed examples. For
$f \in \mathcal{F}$ write $R(f) = \mathbb{E}\,\ell(y, f(x))$ for the expected risk and
$\hat R(f) = \frac{1}{n}\sum_{i=1}^{n} \ell(y_i, f(x_i))$ for the empirical risk. Then for every
$t > 0$,

$$
\mathbb{P}\Big(\max_{f \in \mathcal{F}} \lvert \hat R(f) - R(f) \rvert > t\Big)
\le 2\,\lvert \mathcal{F} \rvert \exp\Big(-\frac{2 n t^2}{\ell_\infty^2}\Big),
$$

and so, for every $\delta \in (0, 1]$, with probability at least $1 - \delta$,

$$
\max_{f \in \mathcal{F}} \lvert \hat R(f) - R(f) \rvert
\le \ell_\infty \sqrt{\frac{\log(2 \lvert \mathcal{F} \rvert / \delta)}{2n}}.
$$

Derivation: for a fixed $f$, the variables $\ell(y_i, f(x_i)) / \ell_\infty$ are independent, take
values in $[0, 1]$ and have mean $R(f) / \ell_\infty$, so the two-sided Hoeffding inequality bounds
the probability that $\lvert \hat R(f) - R(f) \rvert$ exceeds $t$ by
$2 \exp(-2 n t^2 / \ell_\infty^2)$. The event on the left is the union of these $\lvert \mathcal{F}
\rvert$ events, and the probability of a finite union is at most the sum of the probabilities. The
second statement takes $t = \ell_\infty \sqrt{\log(2 \lvert \mathcal{F} \rvert / \delta) / (2n)}$,
for which the right-hand side equals $\delta$, and passes to the complementary event. The maximum
over a finite class is measurable because each $\hat R(f)$ is.

A uniform bound of this kind controls empirical risk minimization (derived): if
$\hat f \in \mathcal{F}$ minimizes $\hat R$ and $s = \max_{f} \lvert \hat R(f) - R(f) \rvert$, then
for every $f \in \mathcal{F}$, $R(\hat f) \le \hat R(\hat f) + s \le \hat R(f) + s \le R(f) + 2s$.

The source states this bound for a loss with values in $[0, \ell_\infty]$ and i.i.d. examples,
with the per-predictor Hoeffding step for independent variables in $[0, 1]$; the exact forms above
(the strict event, the measurability remark and the constants) are derived here. Only the case of a $\{0, 1\}$-valued loss with
$\ell_\infty = 1$, such as the classification error, matches a statement formalized in this
library; for other bounded losses the Hoeffding step is the classical inequality for bounded
variables, which this library does not formalize.

This page is an AI-authored exposition; it has no Lean formalization in this library.

## Informally uses

- [Two-sided Hoeffding inequality for Bernoulli sums](../../../Probability/concentration-inequalities/hoeffding-s-inequality/hoeffding-bernoulli-sum-abs-tail.md):
  mathematical prerequisite in a restricted case, the per-predictor bound when the loss takes only
  the values $0$ and $1$ ($\ell_\infty = 1$): with $X_i = \ell(y_i, f(x_i))$ and
  $p = R(f)$ it is exactly the bound $2 \exp(-2 n t^2)$ on the event
  $\lvert \hat R(f) - R(f) \rvert > t$.

## Sources

- F. Bach, *Learning Theory from First Principles*, MIT Press (2024); author PDF dated 26 May 2025 at <https://www.di.ens.fr/~fbach/ltfp_book.pdf>, Section 4.4.3 (finite number of models), printed page 88 (the union bound and the high-probability bound), and Section 1.2.1, Proposition 1.2 and Corollary 1.1, printed pages 10–11 (Hoeffding's inequality for independent variables in $[0, 1]$).
