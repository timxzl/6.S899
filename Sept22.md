
Sampling Problems

Decision Problems
  (Languages)

Promise Problems
\Pi_Y, \Pi_N \subset {0, 1}^k
\Pi_Y \intersect \Pi_N = \emptyset

relate estimation problem with probmise problems: exact is \rho, decide \Pi_Y (> \rho + \epsilon) or \Pi_N (< \rho - \epsilon)

BQP completeness problem: given a quantum circuit, accept P > 2/3 or P < 1/3

BPP =?= BQP ??
PromiseBPP =?= PromiseBQP ??
  BPP =?= BQP =?=> PromiseBPP =?= PromiseBQP
  but BPP =?= BQP <= PromiseBPP =?= PromiseBQP, because BPP and BQP can be seemed as Promise version with trivial (empty) promise

Relation Problems
  R \subset {0,1}^* x {0,1}^*
  given x find y, poly s.t. xRy
  "function problem"
  e.g. give you a game, find a Nash equilibrium. the "decision" problem is always yes, proved by Nash. finding it is nontrivial.
  but if you put any constraint on your equilibrium (like what kind of equilibrium), deciding whether there exists
  is NP-hard, not always exists.
    e.g. not every game has a pure Nash equilibrium, such as stone-scissor game.
    (pure stratgegy is not mixed strategy, not randomized)
  And this decision problem and the searching problem is not equivalent (one does not imply another)

PPAD
  the problem of finding Nash equilibrium is complete in a set of Relation problem.

FBPP =?= FBQP  (f - function problem, or Relation problem)
FBPP =?= FBQP => PromiseBPP =?= PromiseBQP, because Promise version is just a special case of Relation case

Sampling Problems
  x |---> Distribution_X
  sample exact, and sample approximate (e.g. D s.t. ||D - D_X|| <= \epsilon)

SampBPP =?= SampBQP
  SampBPP_0 =?= SampBQP_0 (zero error case)
  SampBPP_{\epsilon} =?= SampBQP_{\epsilon}

Scott's paper: equivalence of sampling and searching: SampBPP_{\epsilon} = SampBQP_{\epsilon} <=> FBPP = FBQP
the "=>" directino is easy?
the "<=" direction:
Sample Q
Supp(Q)
paradoxical?
there is a way to cut through this paradox
Kolmogorov Complexity
K(x) - min |P| s.t. P() = x (P() - output of program P)
not Kolmogorov first thought about it, it's not a complexity
better name: algorithmic entropy
a pure random string x, K(x) close to the length(x)

problem: output a string with Kolmogorov complexity at least n: just output random string. you can never be totally certain,
because K(x) is uncomputable.

Here is the relation problem I would like you to solve:
output X_1, ... , X_K in the Supp(Q), and they have large Kolmogorov Complexity
if a classical Turing Machine solves this relation problem, it must be sampling from a distribution close to Q.

at least for exact sampling, SampBQP \neq SampBPP, otherwise the PH collapse.

If SampBPP_0 = SampBQP_0 then PH collapse to the second level.
Scott want to establish same thing for SampBPP_\epsilon and SampBQP_\epsilon

X \in C^{n x n} (complex number matrices)
Per(X) = \Sum_{\sigma \in S_n} \Prod_{i=1}^{n} X_{i, \sigma(i))
Det(X) = \Sum_{\sigma \in S_n} (-1)^{sgn(\sigma)} \Prod_{i=1}^{n} X_{i, \sigma(i))
\sigma: a permutation, S_n: all permutations of [1..n]

compute Det is equivalent to matrix multiplication n^2.37...
Per is #P complete, even for matrix with just {0, 1} (Valiont 1979 that introduced #P problems), as hard as any counting problem
perhaps harder than any NP problems.

The decision version of Per is not NP-complete: given a matrix with just 0,1, decide whether its Per(X) > 0
  => find a permutation with all 1's, perfect matching problem.
Per disprove this: if a problem is #P complete then its decision problem is NP complete.

Approximating the permanent of a non-negative matrix
  at the very least this must \in BPP^{NP}
  there is a much stronger result due to Je.. - Sirdair? - Virgoda 1997, it's \in BPP  (using Markov Chain Monte Carlo)
    you can get poly(1/\epsilon)

Approximating permanent for an arbitrary matrix is just as hard as computing Per, i.e. it's #P complete

Naive way of computing Per: n!, but there is a more clever way, 2^n * n, this is the fastest known
"how can you compute the permanent in merely 2^n*n time?"
two different beautiful formula
Glynn Formula
  Per(A) = \frac{1}{2^n} \Sum_{x \in {-1, 1}^n} x_1 \times ... \times x_n \Prod A[x_1, ..., x_n]^{transpose}
  rotate x_i's in Gray code, so you can re-use the previous AX result when changing just one x_i

