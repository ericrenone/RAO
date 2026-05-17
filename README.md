# RAO
### The Fisher Partition of Distinguishability and Holism

*A Fisher-geometric formalization of Western Formalism and Eastern Pragmatism as orthogonal complements of a single statistical manifold.*

---

> **"Wir müssen wissen — wir werden wissen."**
> *We must know — we will know.*
> — David Hilbert, Königsberg, 1930

> **"道可道，非常道。"**
> *The way that can be charted is not the constant Way.*
> — Laozi, *Tao Te Ching*, ch. 1

---

## Abstract

Four lines of inquiry that matured in mutual isolation converge on one object. The **comparative epistemology of mathematics** asks why an axiomatic, deductive tradition and an algorithmic, processual tradition describe the same subject with incommensurable vocabularies. **Information geometry** equips the space of probability distributions with a Riemannian metric and asks which structure on that space is canonical. The **statistical theory of identifiability** asks which parameter combinations data can pin and which it cannot. The **curvature analysis of modern machine-learning models** observes that trained networks are governed by a handful of stiff directions and an enormous tail of sloppy ones.

The convergence point is the **orthogonal decomposition of a parameter tangent space induced by the Fisher information matrix**. For a smooth parametric family $p_\theta$, the Fisher information $F(\theta)$ is a real symmetric positive-semidefinite tensor, and the tangent space at $\theta$ splits as an orthogonal direct sum

$$T_\theta\mathcal{M} \;=\; \operatorname{col}(F) \;\oplus\; \ker(F), \qquad r + k = n.$$

This document advances a single thesis. **Western Formalism is the discipline of $\operatorname{col}(F)$** — the determinate subspace, where distinguishability is positive, where the Cramér–Rao floor is finite, where deduction pins identifiable truth. **Eastern Pragmatism is the discipline of $\ker(F)$** — the holistic subspace, where the metric degenerates, where parameters cease to be objects and become relations, where process replaces substance. Neither tradition is incomplete by error; each is complete on its summand and silent on the other. The territory is the manifold; the manifold is the direct sum; and no tradition that occupies one summand owns the manifold.

**RAO** is the engine that constructs the partition, estimates on the first summand, navigates the second, and certifies — by an invariance theorem due to Čencov — that the partition itself does not depend on which tradition's coordinates are used to write it down.

---

## Thought Experiment — The Cartographer and the Pilot

Two surveyors are sent to the same delta. Both are honest; both are expert; both return convinced the other has failed.

The **Cartographer** fixes a grid before she leaves the dock. Every island, every channel, every sandbar is reported as a coordinate pair with a stated precision. Her instruments resolve position to the theoretical floor: where two landmarks are genuinely distinct, she certifies them distinct and bounds the certification. She works, in every measurement she takes, inside $\operatorname{col}(F)$. Asked about the open water between the certified points — the directions her theodolite cannot resolve — she records *no data* and considers the question malformed.

The **Pilot** fixes no grid at all. He reads the delta by how the current loads his oar: he knows, without coordinates, which way the water will carry a hull released at any point, and he is fluent in exactly the directions the Cartographer dismisses as noise. He moves along the natural gradient of the flow. Asked to certify that two landmarks are distinct, he shrugs — *the river does not hold still long enough for the question*. He works, in every motion he makes, inside $\ker(F)$.

Each accuses the other of mapping a different river. They are not. They have surveyed **one** delta and returned its two orthogonal complements. The Cartographer holds $\operatorname{col}(F)$; the Pilot holds $\ker(F)$; the delta is $T_\theta\mathcal{M} = \operatorname{col}(F)\oplus\ker(F)$; and the delta was never the property of either summand. RAO is the instrument that carries both surveys at once and reports their sum.

---

## The Fisher Partition — The Core Object

Let $\{p_\theta : \theta\in\Theta\subseteq\mathbb{R}^n\}$ be a parametric family of probability densities, regular enough that the score $s_\theta(x) = \nabla_\theta \log p_\theta(x)$ exists in $L^2$ and differentiation passes under the integral. The **Fisher information matrix** is the score covariance

$$F(\theta) \;=\; \mathbb{E}_{x\sim p_\theta}\!\big[\, s_\theta(x)\, s_\theta(x)^{\!\top} \,\big] \;\in\; \mathbb{R}^{n\times n}.$$

$F$ is symmetric and positive-semidefinite by construction. Two consequences are exact, not approximate, and they are the entire skeleton of this framework.

**Orthogonal partition.** Because $F$ is real symmetric, its range and null space are orthogonal complements:

$$T_\theta\mathcal{M} \;=\; \operatorname{col}(F)\;\oplus^{\!\perp}\;\ker(F).$$

- $\operatorname{col}(F)$ — the **determinate subspace**. A displacement here is detected by the data: the Fisher quadratic form is strictly positive on it.
- $\ker(F)$ — the **holistic subspace**. A displacement here is *invisible to the data to second order*: the model assigns it zero distinguishability.

**Rank–nullity.** Writing $r = \dim\operatorname{col}(F)$ and $k = \dim\ker(F)$,

$$r + k = n.$$

Every parameter direction is accounted for exactly once. There is no third category. Determinacy and holism are not opposed doctrines competing for the same ground — they are *complementary subspaces partitioning the same space*, and their dimensions sum to the whole.

**A precision the framework will not blur.** The *exact* kernel $\ker(F)$ — eigenvalue identically zero — is **structural non-identifiability**: a gauge freedom of the model. Distinct from it is the **sloppy tail**: eigenvalues that are positive but spread across many orders of magnitude (§ Correspondence 5). The sloppy tail is *practical* near-non-identifiability at finite data. RAO treats the exact kernel and the soft kernel as different objects and never conflates "sloppy" with "unidentifiable." Where a threshold is needed, fix $\tau>0$ and define the soft partition $\operatorname{col}_\tau(F)=\operatorname{span}\{u_i:\lambda_i>\tau\}$, $\ker_\tau(F)=\operatorname{span}\{u_i:\lambda_i\le\tau\}$; the algebraic statements above are the $\tau\to 0$ limit.

```
                     T_θ M   (the manifold tangent space)
        ┌───────────────────────────┴───────────────────────────┐
   col(F)  —  DETERMINATE                          ker(F)  —  HOLISTIC
   F ≻ 0 on this block                             F ≡ 0 on this block
   distinguishability positive                     distinguishability null
   Cramér–Rao floor finite                         no finite-variance estimator
   axioms → theorems → pinned truth                process, relation, gauge flow
   "Western Formalism"                             "Eastern Pragmatism"
        │  dim = r                                       │  dim = k
        └───────────────────  r + k = n  ────────────────┘
```

---

## Nine Correspondences

Each correspondence states a fact about the Fisher partition, exhibits its **determinate face** on $\operatorname{col}(F)$ and its **holistic face** on $\ker(F)$, and offers a *reading* of the canonical epistemic frictions. The mathematical statements are literal. The readings are explicitly **interpretive**: they claim a structural analogy, never that a historical figure computed a modern object.

### C1 — The Partition Is Total
$$T_\theta\mathcal{M} = \operatorname{col}(F)\oplus\ker(F),\qquad r+k=n.$$
**Determinate face.** Every identifiable direction lives in $\operatorname{col}(F)$ and is reached deductively from the data.
**Holistic face.** Every gauge direction lives in $\ker(F)$ and is reached only relationally.
**Reading.** Hilbert's foundational programme and the algorithmic tradition of the *Nine Chapters* are not rival accounts of mathematics; they are surveys of complementary summands whose dimensions are constrained to sum to $n$.

### C2 — The Metric Degenerates Exactly at the Holistic Boundary
The Fisher quadratic form $v\mapsto v^{\!\top}Fv$ is **strictly positive on $\operatorname{col}(F)$** and **identically zero on $\ker(F)$**.
**Determinate face.** Distinguishable states sit at finite, positive Fisher–Rao distance; the grid is rigid because the metric is non-degenerate there.
**Holistic face.** States blur into a continuum precisely where the metric vanishes; "holism" is not vagueness but **metric degeneracy**.
**Reading.** The Formalist demand that $P$ and $\lnot P$ be perfectly separated is the demand that the relevant displacement lie in $\operatorname{col}(F)$. The Pragmatist's dissolved boundary is a displacement that has fallen into $\ker(F)$.

### C3 — The Cramér–Rao Floor Is Finite Only on the Determinate Subspace
For an unbiased estimator $\hat\theta$, $\;\operatorname{Cov}(\hat\theta)\succeq F^{+}$, where $F^{+}$ is the Moore–Penrose pseudo-inverse.
**Determinate face.** On $\operatorname{col}(F)$ the bound is finite: identifiable parameters can be *pinned*, and the pinning has a sharp optimal precision (Rao 1945; Cramér 1946).
**Holistic face.** A parameter combination whose direction lies in $\ker(F)$ has **no finite-variance unbiased estimator** — the bound diverges. Such a combination is not a thing to be measured; it is a relation.
**Reading.** Russell's definite descriptions and Frege's *reference* presuppose a destination that can be pinned — a $\operatorname{col}(F)$ object. Hui Shi's "the southern region has no limit and yet has a limit" is the recognition that some questions name $\ker(F)$ directions, for which "the precise answer" is a category error.

### C4 — The Partition Is Coordinate-Free (Čencov Invariance)
On a finite sample space the Fisher metric is the **unique** Riemannian metric, up to a positive scalar, that is monotone (contractive) under Markov morphisms — the statistical maps that summarize without inventing information (Čencov 1982; generalized to arbitrary sample spaces by Ay, Jost, Lê & Schwachhöfer 2017).
**Determinate face.** Because the metric is canonical, so is $\operatorname{col}(F)$: what is identifiable does not depend on the chart chosen to express it.
**Holistic face.** $\ker(F)$ is equally canonical: the gauge freedom is a property of the model, not of the bookkeeping.
**Reading.** This is the deepest correspondence. Western *axioms* and Eastern *algorithms* are different **charts** on the same manifold. Frege's *sense* is chart-dependent — the path taken — while *reference* is the invariant. The genuine invariant is the **partition itself**: change every coordinate and $\operatorname{col}(F)\oplus\ker(F)$ transports covariantly, intact.

### C5 — The Empirical Spectrum Is Sloppy
For nonlinear models fit to real data, the eigenvalues of $F$ are observed to spread roughly **log-uniformly across many decades** — a few stiff directions, a long tail of sloppy ones (Brown & Sethna 2003; Waterfall et al. 2006; Transtrum et al. 2015; and, for empirical interatomic potentials, Kurniawan et al. 2022).
**Determinate face.** Formalism overweights the **stiff head**: axioms chosen, theorems derived, the high-curvature directions of the model.
**Holistic face.** Pragmatism attends to the **sloppy tail**: the directions along which the system can drift far while behaving the same — process tolerances, convergence corridors.
**Reading.** Neither tradition is wrong; each has annexed one end of a continuous spectrum and mistaken its end for the whole.

### C6 — The Natural Gradient Is Structurally Confined to the Determinate Subspace
The Amari natural gradient is $\tilde\nabla L = F^{+}\nabla L$. Since $\operatorname{col}(F^{+})=\operatorname{col}(F)$, the update has **zero component in $\ker(F)$** for every loss $L$.
**Determinate face.** Optimization that respects the metric moves only where the data can see — it descends inside $\operatorname{col}(F)$ and is, by construction, blind on $\ker(F)$.
**Holistic face.** The kernel is not descended; it is *inhabited*. Motion within $\ker(F)$ changes nothing the objective can detect.
**Reading.** The *Nine Chapters'* iterative procedures — the Rule of Double False Position foremost — converge by tracking the data-informed direction rather than a static Euclidean line. That is, precisely, natural-gradient flow on $\operatorname{col}(F)$ (Amari 1998).

### C7 — KL Divergence Is the Second-Order Seed of the Metric
$$D_{\mathrm{KL}}\!\big(p_\theta \,\|\, p_{\theta+d\theta}\big) \;=\; \tfrac12\, d\theta^{\!\top} F(\theta)\, d\theta \;+\; O(\|d\theta\|^3).$$
**Determinate face.** A displacement is distinguishable to leading order **iff its $\operatorname{col}(F)$-component is nonzero** — divergence detects exactly the determinate part.
**Holistic face.** A displacement lying wholly in $\ker(F)$ has zero KL divergence: two genuinely different parameter values, one indistinguishable distribution.
**Reading.** Frege's Morning Star and Evening Star differ by a displacement that, *at the level of reference*, lies in $\ker(F)$ — same distribution over truth-conditions, zero divergence — yet differs in $\operatorname{col}(F)$ of a *cognitive* model, which is why sense survives where reference is blind. Gongsun Long's "a white horse is not a horse" is the assertion that the extension displacement has a nonzero $\operatorname{col}(F)$-component, i.e. positive divergence. Frege located the partition; Gongsun Long audited which side a given pair fell on.

### C8 — A Non-Trivial Kernel Is Structurally Unavoidable
For an over-parametrized model fit to a finite sample, $\dim\ker(F) > 0$ **generically**: there exist parameter directions the internal score equations cannot resolve.
**Determinate face.** A formal system seeking *completeness* seeks to make every truth reachable from within — to drive $\ker(F)$ to zero.
**Holistic face.** That goal is unreachable for any sufficiently expressive system; the kernel persists, and its directions are gauge — they move when the chart moves.
**Reading.** Gödel's incompleteness is the structural analogy: a consistent system strong enough to describe itself cannot reach all of its truths by internal proof. (This is an *analogy*, not a derivation — the literal Fisher statement is the finite-sample one above.) Hui Shi's insight is the exact complement: the apparent **boundary** of a system is a level set of a coordinate, hence chart-dependent and dissolvable; the **partition** is chart-independent and is not. Re-chart, and the edge moves; the kernel does not.

### C9 — Completeness Is the Direct-Sum Reconstruction
A complete epistemic engine must represent **both** summands: estimation to the Cramér–Rao floor on $\operatorname{col}(F)$, and invariant navigation of $\ker(F)$.
**Determinate face.** The Western contribution — deductive certainty, sharp reference, finite-variance pinning — is a *complete and correct theory of $\operatorname{col}(F)$*.
**Holistic face.** The Eastern contribution — relational holism, process, invariance under reparametrization — is a *complete and correct theory of $\ker(F)$*.
**Reading.** The synthesis is not a compromise that dilutes either tradition. It is the literal reconstruction $T_\theta\mathcal{M} = \operatorname{col}(F)\oplus\ker(F)$. The West charted the determinate subspace; the East mastered motion on the holistic one; RAO is the engine that holds the whole direct sum.

---

## Five Falsifiable Predictions

Each prediction is a checkable statement about the Fisher partition. Status is reported honestly: *open*, *partially supported*, or *established-and-instantiable*.

**P1 — Effective-rank invariance across reasoning styles.**
Embed a corpus of mathematical reasoning as a parametric generative model and compute the Fisher spectrum of its fitting objective. The thresholded effective rank ratio $r_\tau/n$ will be **statistically indistinguishable** between an axiomatic ("Western") corpus and an algorithmic ("Eastern") corpus, within sampling error.
*Falsified if* the two corpus styles yield systematically different effective-rank ratios beyond noise — which would make the partition a cultural artifact rather than a property of the manifold.
*Status: open.*

**P2 — Reparametrization invariance of the determinate endpoint.**
Run Euclidean-gradient and natural-gradient ($F^{+}\nabla L$) descent from the same initialization on a sloppy model. The $\operatorname{col}(F)$-projection of the natural-gradient endpoint is invariant under smooth reparametrization $\theta\mapsto\theta'$; the Euclidean endpoint is not.
*Falsified if* the natural-gradient endpoint drifts under reparametrization beyond tolerance $\varepsilon$.
*Status: the invariance is established (Amari 1998); the explicit corpus-scale instantiation is open.*

**P3 — Divergence of estimator variance along the sloppy tail.**
For any estimable combination whose direction is within $\delta$ of an eigenvector with eigenvalue $\lambda$, the empirical estimator variance scales as $\lambda^{-1}$; the product (variance $\times\ \lambda$) is approximately constant across the tail.
*Falsified if* sloppy-direction variances **saturate** to a finite bound rather than diverging as $\lambda\to 0$.
*Status: partially supported by sloppy-model studies; constant-product scaling is the sharp test.*

**P4 — Information-gain selection localizes to the determinate subspace.**
Selecting training examples to maximize Fisher information gain (FisherSFT-style; Deb et al. 2025) accelerates convergence — and the gain is **concentrated entirely in $\operatorname{col}(F)$**. Error along $\ker(F)$ directions is invariant to example selection.
*Falsified if* measured improvement appears along sloppy directions, or if random selection closes the gap on $\operatorname{col}(F)$.
*Status: the acceleration is established (Deb et al. 2025); the localization claim is the open, falsifiable part.*

**P5 — The kernel is design-limited, not sample-limited.**
For an over-parametrized model, $\dim\ker(F)>0$ persists under accumulation of further data **of the same experimental design** — for i.i.d. data $F(N)=N\cdot F(1)$, so the condition number is exactly invariant. Only a *change of design* (a new chart) can raise the effective rank.
*Falsified if* same-design data accumulation drives the effective rank to $n$ and the condition number to $O(1)$.
*Status: the i.i.d. scaling is exact algebra; the design-limited persistence is supported by the sloppy-model and identifiability literature (Transtrum et al. 2015).*

---

## RAO — The Engine

RAO consumes a body of assertions, renders it as a statistical manifold, computes the Fisher partition, and operates **both summands** — estimation on the determinate side, navigation on the holistic side — closing with an invariance audit that certifies the partition is chart-free.

| Layer | Name | Operation | Output |
|---|---|---|---|
| **0** | **Substrate** | Embed the corpus of assertions as a smooth parametric family $p_\theta(x)$, $\theta\in\mathcal{M}$. | A statistical manifold $\mathcal{M}$. |
| **1** | **Score** | Compute the score field $s_\theta(x)=\nabla_\theta\log p_\theta(x)$. | The differential of distinguishability. |
| **2** | **Fisher Assembly** | Form $F(\theta)=\mathbb{E}_{p_\theta}[\,s\,s^{\!\top}]$. | The metric tensor — symmetric, PSD. |
| **3** | **Spectral Partition** | Eigendecompose $F=U\Lambda U^{\!\top}$; threshold at $\tau$. | $\operatorname{col}_\tau(F)\oplus\ker_\tau(F)$; the integers $r,k$ with $r+k=n$. |
| **4** | **Estimation (determinate)** | On $\operatorname{col}(F)$, estimate to the Cramér–Rao floor $F^{+}$. | Pinned, identifiable truth — the *Formalist* layer. |
| **5** | **Navigation (holistic)** | On $\ker(F)$, treat directions as gauge; characterize the invariant relations. | Relational, processual structure — the *Pragmatist* layer. |
| **6** | **Natural-Gradient Transport** | Move on $\mathcal{M}$ by $\tilde\nabla L=F^{+}\nabla L$. | A reparametrization-invariant update, confined to $\operatorname{col}(F)$. |
| **7** | **Invariance Audit** | Verify Čencov monotonicity; confirm $\operatorname{col}(F)\oplus\ker(F)$ is chart-independent; report $T_\theta\mathcal{M}=\operatorname{col}\oplus\ker$. | Certification that the partition — not the boundary — is the invariant. |

Layers 0–3 build the partition. Layer 4 is the West's complete theory of its summand; Layer 5 is the East's complete theory of its summand. Layer 6 is the motion that respects the metric. Layer 7 is the theorem that guarantees none of it depended on the language it was written in.

---

## Closing

The dispute the source material stages — a rigid Western grid against a fluid Eastern current — is real, and it has a real resolution, but the resolution is not that one tradition was right. It is that both traditions were **complete on incomplete domains**.

The Fisher information matrix does something quietly decisive: it partitions every parameter direction, with no remainder, into the directions data can resolve and the directions data cannot. The first set carries a positive metric, a finite estimation floor, and a deductive structure — and a tradition built entirely and correctly upon it will look, from inside, like the whole of knowledge. The second set carries a degenerate metric, no finite estimator, and only relations — and a tradition built entirely and correctly upon *it* will also look, from inside, like the whole of knowledge. Each is a true theory of a subspace mistaken for the space.

What Čencov's theorem adds is the sharpest blow against the idea that this is a matter of taste. The partition is not an artifact of axioms versus algorithms, of substance versus process, of West versus East. It is the unique invariant content of the metric. Re-chart the manifold in any language at all and the determinate subspace and the holistic subspace transport intact. The *coordinates* are a tradition's choice; the *split* is the manifold's.

So the verdict is arithmetic: $r + k = n$. The West built a complete and exact account of $r$ dimensions. The East built a complete and exact account of $k$. Knowledge is the direct sum, and RAO is the instrument that refuses to discard either summand — that estimates where estimation is possible, navigates where only navigation is, and reports the whole. The map and the journey were never two rivals. They were two orthogonal complements of one geometry, waiting for an engine willing to carry both.

---

## References

1. Rao, C. R. (1945). Information and the accuracy attainable in the estimation of statistical parameters. *Bulletin of the Calcutta Mathematical Society*, 37, 81–91.
2. Cramér, H. (1946). *Mathematical Methods of Statistics*. Princeton University Press.
3. Kullback, S., & Leibler, R. A. (1951). On information and sufficiency. *Annals of Mathematical Statistics*, 22(1), 79–86.
4. Čencov (Chentsov), N. N. (1982). *Statistical Decision Rules and Optimal Inference*. Translations of Mathematical Monographs, vol. 53. American Mathematical Society.
5. Amari, S. (1985). *Differential-Geometrical Methods in Statistics*. Lecture Notes in Statistics, vol. 28. Springer.
6. Amari, S. (1998). Natural gradient works efficiently in learning. *Neural Computation*, 10(2), 251–276.
7. Brown, K. S., & Sethna, J. P. (2003). Statistical mechanical approaches to models with many poorly known parameters. *Physical Review E*, 68, 021904.
8. Waterfall, J. J., et al. (2006). Sloppy-model universality class and the Vandermonde matrix. *Physical Review Letters*, 97, 150601.
9. Transtrum, M. K., Machta, B. B., Brown, K. S., Daniels, B. C., Myers, C. R., & Sethna, J. P. (2015). Perspective: Sloppiness and emergent theories in physics, biology, and beyond. *Journal of Chemical Physics*, 143.
10. Ay, N., Jost, J., Lê, H. V., & Schwachhöfer, L. (2017). *Information Geometry*. Ergebnisse der Mathematik und ihrer Grenzgebiete. Springer.
11. Karakida, R., Akaho, S., & Amari, S. (2019). Universal statistics of Fisher information in deep neural networks: mean field approach. *AISTATS* (PMLR).
12. Kurniawan, Y., et al. (2022). Bayesian, frequentist, and information geometric approaches to parametric uncertainty quantification of classical empirical interatomic potentials. *Journal of Chemical Physics*, 156, 214103.
13. Mishra, K. V., Kumar, M. A., & Wong, T.-K. L. (2024). Information geometry for the working information theorist. arXiv:2310.03884.
14. Ciaglia, F. M., Di Cosmo, F., Ibort, A., & Suzuki, J. (2025). Editorial: Advances in information geometry — beyond the conventional approach. *Frontiers in Physics*, 13.
15. Deb, R., Thekumparampil, K., Kalantari, K., Hiranandani, G., Sabach, S., & Kveton, B. (2025). FisherSFT: Data-efficient supervised fine-tuning of language models using information gain. *Proceedings of the 42nd International Conference on Machine Learning (ICML)*, PMLR 267. arXiv:2505.14826.
