Last time:
Polynomial Hierachy etc.

Totem (?) theorem: P to the P^#P contain all the PH
another thm: BPP is contained in the PH

Today:
Quantum computing #P, and PP
Linear-optics

BPP = {L: \exists polytime M s.t. \forall x, x \in L => Pr_r[M(x,r) accepts] >= 2/3 && x \notin L => Pr_r[M(x,r) accepts] <= 1/3}
probalistic algorithm can be defined on deterministic turing machine, just taking a random string r.
it's so obvious that we don't even think about it (or devising some random turing machine).
yet it has a huge implication in QC.
we don't know how to pull out the quantumness out from a quantum computer.

with a BPP you can amplify it, you can run independent instances of the machine with lots of random strings,
and taking majority vote.
Sipser-Gacs-Lautemann

conjecture: BPP = P because of derandomization

PSPACE upperbound of P^#P, then EXP upperbound of PSPACE


BQP = {L: \exists polytime M, polynomial p s.t. \forall n-bits input x,
M(x) outputs a quantum circuit C_{X} over {H, } on p(n) qubits s.t.
x \in L => C_X|0>^{ ... p(n)} accepts w.p >= 2/3 && x \notin L => C_X|0>^{ ... p(n)} accepts w.p. <= 1/3}

p(n) to ensure uniformity, we don't want the circuit to be too different.
you need to use a classical computer to compute to which direction to turn the laser.

"How do we simulate BQP, anyone?"
use a lot of hadamard gates

"What about an upperbound of BQP, anyone?"
"Certainly BQP is contained in EXP"

Pr[accept] = \Sum_{y} | \alpha_{1_{y}} |^2 = ...
so this puts BQP \subset P^#P
"actually something stronger is true"
PP like BPP but without the huge gap b/w 2/3 and 1/3
PP = {L: \exists polytime TM M s.t. \forall x
x \in L => Pr_r[M(x,r) accepts] > 1/2 && x \in L => Pr_r[M(x,r) accepts] < 1/2}
we can change the first inequality to >= but that does not change the class
PP - probalistic polynomial  BPP - with Bound
PP \subset #P
PP \superset NP
something stronger: BQP \subset PP

"there is a class called AWPP"
"I wound't define it unless someone ask me to"
someone said "please define it"
....
"you asked"
it's useful as a class
"I'll tell you what it useful for"

Counting Hierachy
"PP sort of a cousin of NP"
P^PP = P^#P
"in that sense we can say that PP is almost powerful as #P"
because you can do binary search using PP to simulate #P oracle
CoPP = PP
P^PP might be stronger than PP, it's an interesting open problem

NP oracle and P^NP oracle have the same power

Beigel 1995: \exists oracle A, P^{NP^A} \not \subset PP^{A}
"I have a conjecture that in the real world, PP does contain PH"

a class BP \dot PP   (BP operator)
totem(?)'s thm also gives you that PH \subset BP \dot PP
if you believe in derandomization, and a BP operator always exists, BP \dot PP = PP ?

PP^PP, P^{PP^PP}, PP^{PP^PP}
another possibly infinite hierachy, all contained in PSPACE
can collapse to P if P = PP
most theorists believe that PH is infinite (not collapse)
but not so believe in the counting hierachy

because of Beigel, we have oracle that separates PP and P^PP, but other than that we don't have other separation

PP^AWPP = PP
PP^BQP = PP

traveling salesman problem
given you a set of city positions (like (x,y) points), and a distance bound K,
is there a route that visits each city once which does not exceed K?
people found it hard to put it in NP because of the square root.
it's not proved to be in NP, however it's in the counting hierachy (maybe 5th level)

OK, this is the tour of the complexity classes.

PostBQP = {L: \exists polynomial p, uniform family of poly-size quantum circuits {C_X}_X on p(n) qubits, s.t.
forall x, C_X|0>^{... p(n)} succceeds w.p >= 1/(2^p(n))
x \in L => Pr[C_x accepts | succeed] >= 2/3 && x \not \in L => Pr[Cx accepts | succeed] <= 1/3}

classical version of PostBQP is called PostBPP
it has an older name called BPP path, but I don't like it. started a campaign to call it PostBPP.

Is PostBPP = PostBQP?
our evidence that PostBQP is stronger than PostBPP is way way stronger than the evidence we have that BQP > BPP.

"What's the real power of PostBPP?"
"certainly it contains NP. why it contains NP?"
"if you're a true believer of the many world interpretation, how do you solve an NP problem?
guess the witness, check if it's correct, suicide if it's wrong, condition on alive"
"I don't recommend it"
"but what if the NP problem has no witness? then you will die in every possible world."
"there is a technical fix: with probability 2^{-n} do nothing,
then if there is a witness you'll find it, otherwise you find you in a world where you did nothing."

NP \subset PostBPP \subset BPP^NP
BPP^NP approximate counting: solve any #P problem approximately
I give you f: {0, 1}^n -> {0, 1}, ask you to compute the number of inputs s.t. f(x)=1, S = \Sum_{x \in {0,1}^n} f(x)
Random hash functions
pick an random matrix A \in F_2^{k \times n) (F_2: finite field of 2 elements) at random
ask my NP oracle if \exists x s.t. f(x) = 1 && Ax = 0 ?
let's say we fix k to be n/2
then I can vary k, say n/3
null space of A will have dimension 2^{n-k}
|S| = 2^n
the collision probability of S and nullspace(A)
test collision -> estimate |S| >= l(1+\epsilon) or |S| <= l

with an multiplictive error \epsilon we can do approximate counting
it's important that f(x) is non-negative, there is no cancellation

conclusion:
PostBPP \subset BPP^NP
for any oracle, BPP^A \subset NP^{NP^A}
so PostBPP is contained in PH

PostBQP \subset PP

Thm (Scott 2004): PostBQP = PP

big open problem: whether NP \subset BQP?

suppose PostBQP = PostBPP
then PP = PostBQP = PostBPP \subset BPP^NP
=> P^PP \subset P^{BPP^NP} = BPP^NP
=> P^{#P} \subset BPP^NP \subset \Sigma_{3}^{P}
so the entire PH collapse to the 3rd level!
