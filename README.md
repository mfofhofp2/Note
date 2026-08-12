# Bond, Stock, Option — Cleaned-Up Derivation (Keith's ordering)

Uses the same reference-point ordering as the original note: $\Pi = O\,X(L)\,X(H)\,X(K)$.

## Setup

$$x = O + \rho + s\sigma + v\kappa \qquad X(\omega) = O + R\rho + \omega\sigma + \max(\omega-K,0)\kappa$$

With $L<K<H$:

$$X(L) = O+R\rho+L\sigma \qquad X(K)=O+R\rho+K\sigma \qquad X(H)=O+R\rho+H\sigma+(H-K)\kappa$$

We write $x$ as a combination of $O, X(L), X(H), X(K)$. Arbitrage-free requires the coefficients of $X(L), X(H), X(K)$ to be non-negative (coefficient on $O$ is unconstrained).

Convention: since every factor carries a copy of $O$ and $O\wedge O=0$, once the leading $O$ is factored out we only keep the non-$O$ (direction) part of each subsequent factor.

Reduction identities used throughout (all other 3-fold wedge combinations vanish because a vector repeats):
$$\rho\sigma\kappa=1, \quad \rho\kappa\sigma=-1, \quad \sigma\kappa\rho=+1, \quad \kappa\sigma\rho=-1, \quad \sigma\rho\kappa=-1, \quad \kappa\rho\sigma=+1 \qquad (\text{units of } \rho\sigma\kappa)$$

## Step 1 — Compute $\Pi = O\,X(L)\,X(H)\,X(K)$

$$(R\rho+L\sigma)\wedge(R\rho+H\sigma+(H-K)\kappa) = (RH-LR)\rho\sigma + R(H-K)\rho\kappa + L(H-K)\sigma\kappa$$

Wedge with $(R\rho+K\sigma)$ — only cross terms survive:

$$R(H-K)\rho\kappa\wedge K\sigma = R(H-K)K\,\rho\kappa\sigma = -R(H-K)K\,\rho\sigma\kappa$$
$$L(H-K)\sigma\kappa\wedge R\rho = L(H-K)R\,\sigma\kappa\rho = +L(H-K)R\,\rho\sigma\kappa$$

Sum:
$$\Pi = \big[-R(H-K)K + L(H-K)R\big]\,O\rho\sigma\kappa = R(H-K)(L-K)\,O\rho\sigma\kappa$$

**Note the sign**: since $L<K$, $(L-K)<0$, and $(H-K)>0$, $R>0$ — so $\Pi$ itself is **negative**. This matters below: dividing by a negative denominator flips the inequality direction.

## Step 2 — Compute $\Pi_1(x) = O\,x\,X(H)\,X(K)$ (coefficient of $X(L)$)

$$(\rho+s\sigma+v\kappa)\wedge(R\rho+H\sigma+(H-K)\kappa) = (H-sR)\rho\sigma + (H-K-vR)\rho\kappa + (s(H-K)-vH)\sigma\kappa$$

Wedge with $(R\rho+K\sigma)$:

$$(H-K-vR)\rho\kappa\wedge K\sigma = -(H-K-vR)K\,\rho\sigma\kappa$$
$$(s(H-K)-vH)\sigma\kappa\wedge R\rho = (s(H-K)-vH)R\,\rho\sigma\kappa$$

Sum, then simplify:
$$\Pi_1(x) = \big[-(H-K-vR)K + (s(H-K)-vH)R\big]\,O\rho\sigma\kappa = (H-K)\big[R(s-v)-K\big]\,O\rho\sigma\kappa$$

Divide by $\Pi = R(H-K)(L-K)\,O\rho\sigma\kappa$:

$$\text{coeff}(X(L)) = \frac{R(s-v)-K}{R(L-K)}$$

**Denominator is negative** ($L<K$). For coeff $\ge0$, numerator must be $\le0$:
$$R(s-v)-K\le0 \;\;\Longrightarrow\;\; v\ge s-\frac{K}{R}$$

> **Correction vs. the original note**: the original draft concludes $v\le s(H-K)/H$ here. Re-deriving carefully (matching every intermediate expression against the original) gives $v \ge s-K/R$ instead — this is the standard discounted-intrinsic-value lower bound on a call, independent of $L,H$.

## Step 3 — Compute $\Pi_2(x) = O\,X(L)\,x\,X(K)$ (coefficient of $X(H)$)

$$(R\rho+L\sigma)\wedge(\rho+s\sigma+v\kappa) = (Rs-L)\rho\sigma + Rv\,\rho\kappa + Lv\,\sigma\kappa$$

Wedge with $(R\rho+K\sigma)$:

$$Rv\,\rho\kappa\wedge K\sigma = -RvK\,\rho\sigma\kappa \qquad Lv\,\sigma\kappa\wedge R\rho = LvR\,\rho\sigma\kappa$$

Sum:
$$\Pi_2(x) = (LvR-RvK)\,O\rho\sigma\kappa = vR(L-K)\,O\rho\sigma\kappa$$

Divide by $\Pi = R(H-K)(L-K)\,O\rho\sigma\kappa$ — the $(L-K)$ factor cancels directly (no sign flip needed):

$$\text{coeff}(X(H)) = \frac{v}{H-K} \;\;\ge0 \;\;\Longrightarrow\;\; v\ge0$$

This matches the original note's conclusion ($v\ge0$) — correct.

## Step 4 — Compute $\Pi_3(x) = O\,X(L)\,X(H)\,x$ (coefficient of $X(K)$ — this is the step flagged `TODO: check sign` in the original)

Reuse the intermediate result from Step 1:
$$(R\rho+L\sigma)\wedge(R\rho+H\sigma+(H-K)\kappa) = (RH-LR)\rho\sigma + R(H-K)\rho\kappa + L(H-K)\sigma\kappa$$

Wedge with $(\rho+s\sigma+v\kappa)$:

$$(RH-LR)\rho\sigma\wedge v\kappa = (RH-LR)v\,\rho\sigma\kappa$$
$$R(H-K)\rho\kappa\wedge s\sigma = -R(H-K)s\,\rho\sigma\kappa$$
$$L(H-K)\sigma\kappa\wedge\rho = L(H-K)\,\rho\sigma\kappa$$

Sum:
$$\Pi_3(x) = \big[R(H-L)v - (H-K)(Rs-L)\big]\,O\rho\sigma\kappa$$

Divide by $\Pi = R(H-K)(L-K)\,O\rho\sigma\kappa$ (**negative denominator**):

$$\text{coeff}(X(K)) = \frac{R(H-L)v-(H-K)(Rs-L)}{R(H-K)(L-K)}$$

For coeff $\ge0$, since denominator is negative, numerator must be $\le0$:
$$R(H-L)v \le (H-K)(Rs-L) \;\;\Longrightarrow\;\; v \le \frac{(H-K)(Rs-L)}{R(H-L)}$$

> **Correction vs. the original note**: the original draft concludes $v\ge(H-K)(Rs-L)/[R(H-L)]$ — this is the step Keith himself flagged with `TODO: check sign`. The intermediate expression is correct, but dividing by the negative $\Pi$ flips the inequality: the correct direction is $v \le \ldots$, not $v \ge \ldots$. Numerically, with $L=90,K=100,H=110,R=1,s=100$: $(H-K)(Rs-L)/[R(H-L)] = 10\cdot10/20=5$ — matching the original note's arithmetic, but as an **upper** bound, not a lower one.

## Combined result

$$\boxed{\max(0,\ s-K/R) \;\le\; v \;\le\; \frac{(H-K)(Rs-L)}{R(H-L)}}$$

Same conclusion as the independently-derived version using the $O\,X(L)\,X(K)\,X(H)$ ordering (that version's $\Pi$ is the negative of this one's, since it swaps the last two factors — a single transposition, one sign flip — but the final inequalities work out identically once each sign is tracked through consistently).

## Sanity check against known theory

- **Lower bound** $v\ge\max(0,s-K/R)$: the standard model-free no-arbitrage lower bound on a call (discounted intrinsic value). Independent of $L,H$ — a good consistency check, since it must hold in *any* arbitrage-free model, not just this trinomial one.
- **Upper bound** $v\le(H-K)(Rs-L)/[R(H-L)]$: comes from the specific trinomial structure; reduces to the earlier bond+stock cone-boundary logic at the endpoints.
- **$v\ge0$**: trivial (a call's payoff is never negative).













# Bond, Stock, Option — Cleaned-Up Derivation

## Setup

Three instruments: bond (return $R$), stock (price $s$), call option with strike $K$ (price $v$).

$$x = O + \rho + s\sigma + v\kappa$$
$$X(\omega) = O + R\rho + \omega\sigma + \max(\omega-K,0) \kappa$$

We take three reference outcomes $L < K < H$. Since $\max(\omega-K,0)=0$ for $\omega\le K$:

$$X(L) = O + R\rho + L\sigma       (\text{no } \kappa \text{ term, since } L\le K)$$
$$X(K) = O + R\rho + K\sigma       (\text{no } \kappa \text{ term, since } K\le K)$$
$$X(H) = O + R\rho + H\sigma + (H-K)\kappa$$

We want to write $x = a O + b X(L) + c X(K) + d X(H)$ and determine when $b,c,d\ge0$ (arbitrage-free requires the coefficients of $X(L), X(K), X(H)$ to be non-negative — the coefficient on $O$ is unconstrained).

## The mechanical tool

Let $\Pi = O X(L) X(K) X(H)$, and let $\Pi_j(x)$ denote $\Pi$ with the $j$-th factor replaced by $x$. Then each coefficient is

$$b = \frac{\Pi_1(x)}{\Pi},       c = \frac{\Pi_2(x)}{\Pi},       d = \frac{\Pi_3(x)}{\Pi}$$

**Key simplification**: every factor being multiplied contains a copy of $O$. Since $O\wedge O = 0$, any term that draws the $O$-part from more than one factor vanishes. So in every product below, we can replace $X(L),X(K),X(H),x$ by their **non-$O$ parts** once the leading $O$ has been factored out:

$$X(L) \to R\rho+L\sigma,     X(K)\to R\rho+K\sigma,     X(H)\to R\rho+H\sigma+(H-K)\kappa,     x\to \rho+s\sigma+v\kappa$$

Throughout, only the $\rho\sigma\kappa$ term survives (all other wedge combinations involve a repeated vector and vanish). Useful reduction identities:

$$\rho\sigma\kappa = 1,    \rho\kappa\sigma=-1,    \sigma\kappa\rho=+1,    \kappa\sigma\rho=-1,    \sigma\rho\kappa=-1,    \kappa\rho\sigma=+1     (\text{units of } \rho\sigma\kappa)$$

## Step 1 — Compute $\Pi$

$$(R\rho+L\sigma)\wedge(R\rho+K\sigma) = (RK-LR) \rho\sigma = R(K-L) \rho\sigma$$

Wedge with $(R\rho+H\sigma+(H-K)\kappa)$: only the $\kappa$ term survives ($\rho\sigma\rho=\rho\sigma\sigma=0$):

$$R(K-L) \rho\sigma \wedge (H-K)\kappa = R(K-L)(H-K) \rho\sigma\kappa$$

$$\boxed{\Pi = R(K-L)(H-K)  O\rho\sigma\kappa}$$

## Step 2 — Compute $\Pi_1(x) = O x X(K) X(H)$

$$(\rho+s\sigma+v\kappa)\wedge(R\rho+K\sigma) = (K-sR) \rho\sigma - vR \rho\kappa + vK \kappa\sigma$$

Wedge each term with $(R\rho+H\sigma+(H-K)\kappa)$:

- $(K-sR)\rho\sigma \wedge (\cdots) = (K-sR)(H-K) \rho\sigma\kappa$
- $-vR \rho\kappa \wedge (\cdots) = -vR\cdot H\cdot\rho\kappa\sigma = -vRH\cdot(-\rho\sigma\kappa) = vRH \rho\sigma\kappa$
- $vK \kappa\sigma\wedge(\cdots) = vK\cdot R\cdot\kappa\sigma\rho = vKR\cdot(-\rho\sigma\kappa) = -vKR \rho\sigma\kappa$

Sum:
$$\Pi_1(x) = [(K-sR)(H-K) + vR(H-K)] O\rho\sigma\kappa = (H-K)(K-sR+vR) O\rho\sigma\kappa$$

$$b = \frac{\Pi_1(x)}{\Pi} = \frac{K-sR+vR}{R(K-L)} = \frac{K-R(s-v)}{R(K-L)}$$

**$b\ge0$** (denominator positive since $R>0,K>L$):
$$K-R(s-v)\ge0  =>  v \ge s-\frac{K}{R}$$

## Step 3 — Compute $\Pi_2(x) = O X(L) x X(H)$

$$(R\rho+L\sigma)\wedge(\rho+s\sigma+v\kappa) = (Rs-L) \rho\sigma + Rv \rho\kappa + Lv \sigma\kappa$$

Wedge each term with $(R\rho+H\sigma+(H-K)\kappa)$:

- $(Rs-L)\rho\sigma\wedge(\cdots) = (Rs-L)(H-K) \rho\sigma\kappa$
- $Rv \rho\kappa\wedge(\cdots) = Rv\cdot H\cdot\rho\kappa\sigma = -RvH \rho\sigma\kappa$
- $Lv \sigma\kappa\wedge(\cdots) = Lv\cdot R\cdot\sigma\kappa\rho = LvR \rho\sigma\kappa$

Sum:
$$\Pi_2(x) = [(Rs-L)(H-K) - Rv(H-L)] O\rho\sigma\kappa$$

$$c = \frac{\Pi_2(x)}{\Pi} = \frac{(Rs-L)(H-K) - Rv(H-L)}{R(K-L)(H-K)}$$

**$c\ge0$**:
$$(Rs-L)(H-K) \ge Rv(H-L)  =>  v \le \frac{(Rs-L)(H-K)}{R(H-L)}$$

## Step 4 — Compute $\Pi_3(x) = O X(L) X(K) x$

From Step 1, $(R\rho+L\sigma)\wedge(R\rho+K\sigma) = R(K-L) \rho\sigma$. Wedge with $(\rho+s\sigma+v\kappa)$: only the $\kappa$ term survives:

$$\Pi_3(x) = R(K-L)v O\rho\sigma\kappa$$

$$d = \frac{\Pi_3(x)}{\Pi} = \frac{v}{H-K}$$

**$d\ge0$** (since $H>K$): $    v\ge0$

## Combined result

$$\boxed{\max(0,  s-\frac{K}{R})  \le  v  \le  \frac{(Rs-L)(H-K)}{R(H-L)}}$$

(This assumes $R>0$ and $L<K<H$, which are needed for the denominators to be positive and the ordering to make sense.)

## Sanity check against known theory

- **Lower bound** $v\ge\max(0,s-K/R)$ is exactly the standard model-free no-arbitrage lower bound on a call option: the discounted intrinsic value. This doesn't even depend on $L$ or $H$ — a good consistency check, since it should hold in *any* arbitrage-free model, not just this specific trinomial one.
- **Upper bound** depends on the full trinomial structure ($L,H,K$) and reduces exactly to the earlier bond+stock cone-boundary logic when you substitute in the endpoints.
- **$v \ge 0$** is the trivial bound (option payoff is never negative, so its price shouldn't be either).

## Note on the original draft

The original note's arithmetic (the "$100(10)/100=10$" and "$10(10)/20=5$" fragments) doesn't cleanly match this derivation — likely because of the transcription/sign issues already flagged with a `TODO: check sign` in the source. With this cleaned-up version, plugging in the classic **90/100/110** example ($L=90, K=100, H=110, R=1$) gives:

- Lower bound: $\max(0, s-100)$
- Upper bound: $\frac{(s-90)(10)}{20} = \frac{s-90}{2}$

At $s=100$: lower bound $=0$, upper bound $=5$ — matching the "$5$" that appears in the original fragment, but not the "$10$." This suggests the "$10$" in the original draft may have come from an intermediate (possibly mis-simplified) expression rather than a final bound. Worth confirming directly with Keith what $s$ value the original 90-100-110 example assumed, since the source note doesn't state it explicitly.

# Bond, Stock, Two Options — Extending to a Second Strike

## Setup

Four instruments: bond (return $R$), stock (price $s$), call option with strike $K_1$ (price $v_1$), call option with strike $K_2$ (price $v_2$), with $K_1<K_2$.

$$x = O + \rho + s\sigma + v_1\kappa_1 + v_2\kappa_2$$
$$X(\omega) = O + R\rho + \omega\sigma + \max(\omega-K_1,0)\kappa_1 + \max(\omega-K_2,0)\kappa_2$$

We take four reference outcomes $L<K_1<K_2<H$:

$$X(L) = O+R\rho+L\sigma \qquad (\text{neither option ITM})$$
$$X(K_1) = O+R\rho+K_1\sigma \qquad (\text{neither option ITM})$$
$$X(K_2) = O+R\rho+K_2\sigma+(K_2-K_1)\kappa_1 \qquad (\text{only the } K_1\text{ call is ITM})$$
$$X(H) = O+R\rho+H\sigma+(H-K_1)\kappa_1+(H-K_2)\kappa_2$$

We write $x = a\,O + b\,X(L) + c\,X(K_1) + d\,X(K_2) + e\,X(H)$. Arbitrage-free requires $b,c,d,e\ge0$ (coefficient on $O$ unconstrained). Four instruments, four reference outcomes — this is exactly the "complete market" count from the single-option case, now one dimension up.

## The mechanical tool, extended

With five points ($O$ plus four references), $\Pi = O\,X(L)\,X(K_1)\,X(K_2)\,X(H)$ is a 4-fold wedge in the direction space $(\rho,\sigma,\kappa_1,\kappa_2)$. As before, factor out $O$ (using $O\wedge O=0$) and work with direction parts only. The only surviving top-form is $\rho\sigma\kappa_1\kappa_2$ (any repeated vector kills a term), with sign given by permutation parity — same rule as before, just one more slot to track.

A convenient shortcut for a 4-fold wedge of vectors, each given by its coordinates in $(\rho,\sigma,\kappa_1,\kappa_2)$: the wedge product equals the determinant of the matrix whose rows are those coordinates, times $\rho\sigma\kappa_1\kappa_2$. This is the natural extension of the $\rho\sigma\kappa$ reduction identities used for three vectors, and keeps the bookkeeping manageable as the dimension grows.

Coordinates (in the basis $\rho,\sigma,\kappa_1,\kappa_2$):

$$X(L)\to(R,L,0,0) \quad X(K_1)\to(R,K_1,0,0) \quad X(K_2)\to(R,K_2,K_2-K_1,0) \quad X(H)\to(R,H,H-K_1,H-K_2) \quad x\to(1,s,v_1,v_2)$$

## Step 1 — Compute $\Pi \leftrightarrow \det\big(X(L),X(K_1),X(K_2),X(H)\big)$

$$\begin{vmatrix} R&L&0&0\\ R&K_1&0&0\\ R&K_2&K_2-K_1&0\\ R&H&H-K_1&H-K_2 \end{vmatrix}$$

Subtract row 1 from rows 2, 3, 4 (determinant unchanged):

$$\begin{vmatrix} R&L&0&0\\ 0&K_1-L&0&0\\ 0&K_2-L&K_2-K_1&0\\ 0&H-L&H-K_1&H-K_2 \end{vmatrix}$$

This is block lower-triangular after expanding along column 1 — the determinant is the product of the diagonal entries:

$$\boxed{\Pi = R(K_1-L)(K_2-K_1)(H-K_2)\; O\rho\sigma\kappa_1\kappa_2}$$

Unlike the single-option case (where $\Pi$ came out negative), here every factor is positive since $L<K_1<K_2<H$ and $R>0$ — so $\Pi>0$, and no sign-flip bookkeeping is needed below.

## Step 2 — Compute $\Pi_1(x) \leftrightarrow \det\big(x,X(K_1),X(K_2),X(H)\big)$ (coefficient $b$ of $X(L)$)

$$\begin{vmatrix} 1&s&v_1&v_2\\ R&K_1&0&0\\ R&K_2&K_2-K_1&0\\ R&H&H-K_1&H-K_2 \end{vmatrix}$$

Eliminate column 1 using row 1 (subtract $R\times$row 1 from rows 2–4):

$$\begin{vmatrix} 1&s&v_1&v_2\\ 0&K_1-Rs&-Rv_1&-Rv_2\\ 0&K_2-Rs&K_2-K_1-Rv_1&-Rv_2\\ 0&H-Rs&H-K_1-Rv_1&H-K_2-Rv_2 \end{vmatrix}$$

Expand along column 1 — reduces to the $3\times3$ minor. Subtract row 2 from rows 3, 4 of that minor:

$$\begin{vmatrix} K_1-Rs&-Rv_1&-Rv_2\\ K_2-K_1&K_2-K_1&0\\ H-K_1&H-K_1&H-K_2-Rv_2+Rv_2 \end{vmatrix} = \begin{vmatrix} K_1-Rs&-Rv_1&-Rv_2\\ K_2-K_1&K_2-K_1&0\\ H-K_1&H-K_1&H-K_2 \end{vmatrix}$$

Expand along the third column (only two nonzero entries):

$$-(-Rv_2)\cdot\big[(K_2-K_1)^2-(K_2-K_1)(H-K_1)\big]\cdots$$

This is getting heavy to track by hand across every term — collecting all contributions (row/column expansion of the $3\times3$, then simplifying) gives:

$$\det\big(x,X(K_1),X(K_2),X(H)\big) = (K_2-K_1)(H-K_2)\big[K_1-R(s-v_1)\big]$$

Dividing by $\Pi$:

$$b = \frac{K_1-R(s-v_1)}{R(K_1-L)}$$

**$b\ge0$** (denominator positive):
$$K_1-R(s-v_1)\ge0 \;\Longrightarrow\; v_1 \ge s-\frac{K_1}{R}$$

This is exactly the single-option discounted-intrinsic-value lower bound, reappearing unchanged with a second option in the picture — a strong consistency check.

## Step 3 — Compute $\Pi_2(x) \leftrightarrow \det\big(X(L),x,X(K_2),X(H)\big)$ (coefficient $c$ of $X(K_1)$)

Same style of row reduction (details omitted for brevity — same mechanics as Step 2, with $x$ now in the second slot):

$$c = \frac{(K_2-K_1)(s-L/R) - \big[(K_2-L)v_1-(K_1-L)v_2\big]}{(K_1-L)(K_2-K_1)}$$

**$c\ge0$**:
$$(K_2-L)v_1-(K_1-L)v_2 \;\le\; (K_2-K_1)\left(s-\frac{L}{R}\right)$$

A joint bound linking $v_1$ and $v_2$ together — this one doesn't reduce to either option's standalone bound; it only appears once both strikes are in the picture.

## Step 4 — Compute $\Pi_3(x) \leftrightarrow \det\big(X(L),X(K_1),x,X(H)\big)$ (coefficient $d$ of $X(K_2)$)

$$\begin{vmatrix} R&L&0&0\\ R&K_1&0&0\\ 1&s&v_1&v_2\\ R&H&H-K_1&H-K_2 \end{vmatrix}$$

Rows 1 and 2 agree in columns 3–4 (both zero) — subtracting row 1 from row 2 leaves a row of the form $(0,K_1-L,0,0)$, which simplifies the expansion considerably. Carrying this through:

$$\det\big(X(L),X(K_1),x,X(H)\big) = (K_1-L)\big[v_1(H-K_2)-v_2(H-K_1)\big]$$

Dividing by $\Pi$:

$$d = \frac{v_1(H-K_2)-v_2(H-K_1)}{(K_2-K_1)(H-K_2)}$$

**$d\ge0$**:
$$\boxed{v_1 \ge v_2\cdot\frac{H-K_1}{H-K_2}}$$

This is the cross-strike relationship, falling straight out of the coefficient calculation with no separate argument required. Since $H-K_1>H-K_2>0$, the ratio $(H-K_1)/(H-K_2)>1$, so this condition is strictly stronger than the intuitive "$v_1\ge v_2$" (the lower-strike call must be worth more) — it pins down exactly how much more.

## Step 5 — Compute $\Pi_4(x) \leftrightarrow \det\big(X(L),X(K_1),X(K_2),x\big)$ (coefficient $e$ of $X(H)$)

Rows 1 and 2 again agree in columns 3–4. Same simplification as Step 4:

$$\det\big(X(L),X(K_1),X(K_2),x\big) = (K_1-L)(K_2-K_1)\,v_2$$

Dividing by $\Pi$:

$$e = \frac{v_2}{H-K_2} \ge 0 \;\Longrightarrow\; v_2\ge0$$

The trivial bound — a call's payoff is never negative.

## Combined result

$$v_2\ge0 \qquad v_1 \ge v_2\cdot\frac{H-K_1}{H-K_2} \qquad v_1\ge s-\frac{K_1}{R} \qquad (K_2-L)v_1-(K_1-L)v_2\le(K_2-K_1)\left(s-\frac{L}{R}\right)$$

Together these four inequalities carve out the no-arbitrage region for $(v_1,v_2)$ jointly, given $s$.

## Worked numeric example

Take $L=80,\ K_1=100,\ K_2=110,\ H=130,\ R=1,\ s=105$.

$$v_2\ge0$$
$$v_1 \ge v_2\cdot\frac{130-100}{130-110} = 1.5\,v_2$$
$$v_1 \ge 105-100 = 5$$
$$30\,v_1-20\,v_2 \le 10\times(105-80)=250$$

**Consistency check**: try $(v_1,v_2)=(10,0)$. The first three bounds pass ($0\ge0$, $10\ge0$, $10\ge5$), but the fourth gives $30(10)-20(0)=300 > 250$ — **violated**. Solving the original linear system directly for $(b,c,d,e)$ at these values confirms $c=-0.25<0$, matching the violated inequality exactly.

Try instead $(v_1,v_2)=(8,3)$: $v_2=3\ge0$ ✓; $v_1=8\ge1.5(3)=4.5$ ✓; $v_1=8\ge5$ ✓; $30(8)-20(3)=240\le250$ ✓ — all four pass, so this pair is arbitrage-free.

## Why this matters for extending further

The same recipe — one more reference outcome, one more direction vector, one more determinant to evaluate — extends to any number of strikes $K_1<\cdots<K_n$. The row-reduction shortcuts seen in Steps 4–5 (reference points sharing zero entries in the option columns collapse the determinant quickly) suggest the coefficient calculations stay tractable even as $n$ grows, though the joint bound analogous to Step 3's condition (linking multiple option prices at once) will involve more cross-terms with each additional strike.
