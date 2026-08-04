# Note

# Bond, Stock, Option — Cleaned-Up Derivation

## Setup

Three instruments: bond (return $R$), stock (price $s$), call option with strike $K$ (price $v$).

$$x = O + \rho + s\sigma + v\kappa$$
$$X(\omega) = O + R\rho + \omega\sigma + \max\{\omega-K,0\}\,\kappa$$

We take three reference outcomes $L < K < H$. Since $\max\{\omega-K,0\}=0$ for $\omega\le K$:

$$X(L) = O + R\rho + L\sigma \qquad (\text{no } \kappa \text{ term, since } L\le K)$$
$$X(K) = O + R\rho + K\sigma \qquad (\text{no } \kappa \text{ term, since } K\le K)$$
$$X(H) = O + R\rho + H\sigma + (H-K)\kappa$$

We want to write $x = a\,O + b\,X(L) + c\,X(K) + d\,X(H)$ and determine when $b,c,d\ge0$ (arbitrage-free requires the coefficients of $X(L), X(K), X(H)$ to be non-negative — the coefficient on $O$ is unconstrained).

## The mechanical tool

Let $\Pi = O\,X(L)\,X(K)\,X(H)$, and let $\Pi_j(x)$ denote $\Pi$ with the $j$-th factor replaced by $x$. Then each coefficient is

$$b = \frac{\Pi_1(x)}{\Pi}, \qquad c = \frac{\Pi_2(x)}{\Pi}, \qquad d = \frac{\Pi_3(x)}{\Pi}$$

**Key simplification**: every factor being multiplied contains a copy of $O$. Since $O\wedge O = 0$, any term that draws the $O$-part from more than one factor vanishes. So in every product below, we can replace $X(L),X(K),X(H),x$ by their **non-$O$ parts** once the leading $O$ has been factored out:

$$X(L) \to R\rho+L\sigma, \quad X(K)\to R\rho+K\sigma, \quad X(H)\to R\rho+H\sigma+(H-K)\kappa, \quad x\to \rho+s\sigma+v\kappa$$

Throughout, only the $\rho\sigma\kappa$ term survives (all other wedge combinations involve a repeated vector and vanish). Useful reduction identities:

$$\rho\sigma\kappa = 1,\quad \rho\kappa\sigma=-1,\quad \sigma\kappa\rho=+1,\quad \kappa\sigma\rho=-1,\quad \sigma\rho\kappa=-1,\quad \kappa\rho\sigma=+1 \quad (\text{units of } \rho\sigma\kappa)$$

## Step 1 — Compute $\Pi$

$$(R\rho+L\sigma)\wedge(R\rho+K\sigma) = (RK-LR)\,\rho\sigma = R(K-L)\,\rho\sigma$$

Wedge with $(R\rho+H\sigma+(H-K)\kappa)$: only the $\kappa$ term survives ($\rho\sigma\rho=\rho\sigma\sigma=0$):

$$R(K-L)\,\rho\sigma \wedge (H-K)\kappa = R(K-L)(H-K)\,\rho\sigma\kappa$$

$$\boxed{\Pi = R(K-L)(H-K)\; O\rho\sigma\kappa}$$

## Step 2 — Compute $\Pi_1(x) = O\,x\,X(K)\,X(H)$

$$(\rho+s\sigma+v\kappa)\wedge(R\rho+K\sigma) = (K-sR)\,\rho\sigma - vR\,\rho\kappa + vK\,\kappa\sigma$$

Wedge each term with $(R\rho+H\sigma+(H-K)\kappa)$:

- $(K-sR)\rho\sigma \wedge (\cdots) = (K-sR)(H-K)\,\rho\sigma\kappa$
- $-vR\,\rho\kappa \wedge (\cdots) = -vR\cdot H\cdot\rho\kappa\sigma = -vRH\cdot(-\rho\sigma\kappa) = vRH\,\rho\sigma\kappa$
- $vK\,\kappa\sigma\wedge(\cdots) = vK\cdot R\cdot\kappa\sigma\rho = vKR\cdot(-\rho\sigma\kappa) = -vKR\,\rho\sigma\kappa$

Sum:
$$\Pi_1(x) = \big[(K-sR)(H-K) + vR(H-K)\big]\,O\rho\sigma\kappa = (H-K)(K-sR+vR)\;O\rho\sigma\kappa$$

$$b = \frac{\Pi_1(x)}{\Pi} = \frac{K-sR+vR}{R(K-L)} = \frac{K-R(s-v)}{R(K-L)}$$

**$b\ge0$** (denominator positive since $R>0,K>L$):
$$K-R(s-v)\ge0 \;\Longrightarrow\; v \ge s-\frac{K}{R}$$

## Step 3 — Compute $\Pi_2(x) = O\,X(L)\,x\,X(H)$

$$(R\rho+L\sigma)\wedge(\rho+s\sigma+v\kappa) = (Rs-L)\,\rho\sigma + Rv\,\rho\kappa + Lv\,\sigma\kappa$$

Wedge each term with $(R\rho+H\sigma+(H-K)\kappa)$:

- $(Rs-L)\rho\sigma\wedge(\cdots) = (Rs-L)(H-K)\,\rho\sigma\kappa$
- $Rv\,\rho\kappa\wedge(\cdots) = Rv\cdot H\cdot\rho\kappa\sigma = -RvH\,\rho\sigma\kappa$
- $Lv\,\sigma\kappa\wedge(\cdots) = Lv\cdot R\cdot\sigma\kappa\rho = LvR\,\rho\sigma\kappa$

Sum:
$$\Pi_2(x) = \big[(Rs-L)(H-K) - Rv(H-L)\big]\;O\rho\sigma\kappa$$

$$c = \frac{\Pi_2(x)}{\Pi} = \frac{(Rs-L)(H-K) - Rv(H-L)}{R(K-L)(H-K)}$$

**$c\ge0$**:
$$(Rs-L)(H-K) \ge Rv(H-L) \;\Longrightarrow\; v \le \frac{(Rs-L)(H-K)}{R(H-L)}$$

## Step 4 — Compute $\Pi_3(x) = O\,X(L)\,X(K)\,x$

From Step 1, $(R\rho+L\sigma)\wedge(R\rho+K\sigma) = R(K-L)\,\rho\sigma$. Wedge with $(\rho+s\sigma+v\kappa)$: only the $\kappa$ term survives:

$$\Pi_3(x) = R(K-L)v\;O\rho\sigma\kappa$$

$$d = \frac{\Pi_3(x)}{\Pi} = \frac{v}{H-K}$$

**$d\ge0$** (since $H>K$): $\quad v\ge0$

## Combined result

$$\boxed{\max\left\{0,\, s-\frac{K}{R}\right\} \;\le\; v \;\le\; \frac{(Rs-L)(H-K)}{R(H-L)}}$$

(This assumes $R>0$ and $L<K<H$, which are needed for the denominators to be positive and the ordering to make sense.)

## Sanity check against known theory

- **Lower bound** $v\ge\max\{0,s-K/R\}$ is exactly the standard model-free no-arbitrage lower bound on a call option: the discounted intrinsic value. This doesn't even depend on $L$ or $H$ — a good consistency check, since it should hold in *any* arbitrage-free model, not just this specific trinomial one.
- **Upper bound** depends on the full trinomial structure ($L,H,K$) and reduces exactly to the earlier bond+stock cone-boundary logic when you substitute in the endpoints.
- **$v \ge 0$** is the trivial bound (option payoff is never negative, so its price shouldn't be either).

## Note on the original draft

The original note's arithmetic (the "$100(10)/100=10$" and "$10(10)/20=5$" fragments) doesn't cleanly match this derivation — likely because of the transcription/sign issues already flagged with a `TODO: check sign` in the source. With this cleaned-up version, plugging in the classic **90/100/110** example ($L=90, K=100, H=110, R=1$) gives:

- Lower bound: $\max(0, s-100)$
- Upper bound: $\dfrac{(s-90)(10)}{20} = \dfrac{s-90}{2}$

At $s=100$: lower bound $=0$, upper bound $=5$ — matching the "$5$" that appears in the original fragment, but not the "$10$." This suggests the "$10$" in the original draft may have come from an intermediate (possibly mis-simplified) expression rather than a final bound. Worth confirming directly with Keith what $s$ value the original 90-100-110 example assumed, since the source note doesn't state it explicitly.
