September 15 scribe

Physical CT

Physical ECT
    Conjecture: P = BPP?    BPP \neq BQP
    
physical discoveries that might falsify physical ECT:
Maldment-Hogath:
  black hole, computer keeps approaching the event horizon of the black hole but never pass it.
  then in the reference frame of the computer, it gets huge amount of time.
  finite speedup, but can be very huge.
  but, this takes infinite amount of energy.

zeno like machine:
  infinitely split time (1st step 1 second, 2nd step 0.5 second, 3rd step 0.25 second... can solve halting problem)
  but when a step takes only Plank time, the energy will be big enough to make a black hole

  simplest computer: a photon bouncing between two mirros. it's just a clock.
  involves G, \bar{h} (Plank constant), c
  E = h \nu
  E = mc^2
  if M >= some constant involving \pi, G, and r (radius of the region), then we get a black hole
  r ~ 10^(-43) cm  Plank length
  
  Plank length is pixels of nature, Plank time is the frame rate
  but naive rectangular grid of Plank length does not satisfy basic symmetries (rotational, etc.) of physics
  but people still guess if nature is discrete in some sophisticated way
  
a paper reduce Halting problem to a variant of Navier-Stokes equation,
so if the water is an ideal continuous liquid, they can build turing machines that takes less and less time per step.
Scott believes that there must be some cutoff (like E = h\nu) that limits the continuity of universe, QM or else.

if you can measure frequencies arbitrarily precisely, you can solve NPC problems in polynomial time
subset sum, a_1, ..., a_n, and target K.
they build a analog device, split light and many frequencies corresponding to any possible sum of subsets.
then measure frequency K.
but how to measure your light when n -> 1000? the frequency will be ~ 2^1000, how do you measure?
you can wait for ~ 2^1000 time, longer than the life of universe.

you can solve NP problems by trying all 2^n possibilities at once,
but must take into account everything we know about physics, including QM and gravitation.

"the biggest application of quantum computer is to disprove the ones who said it's impossible. (it may refer to the falsity of physical ECT)"

physical CT and ECT are asymptotical claims

2nd war of thermodynamics  gas spread uniformly in a container, eventually it might collapse to one unit, but takes N years,
N fixed but enormous constant.

Boson sampling:
P, NP
P = { L | \exists poly time TM M, s.t. \forall x, x \in L <=> M(x) accepts }
NP = { L | \exists poly time TM M, s.t. \forall x,  x \in L <=> \exists w, M(x, w) accepts}  auxiliary w
L is NP-hard if NP \subset P^L
NP-complete: NP \intersect NP-hard

CoNP = { \complement(L): L \in NP}

does NP = CoNP?
if P = NP then P = CoNP = NP

P^NP (P with NP oracle) e.g.: given all solutions to an instance of subset sum, find the lexigraphically smallest one,
does that one contain some element (a_n, say). can be done with binary search with NP oracle, and it's P^NP -complete.

P^P = P  P is closed under calling itself as oracle, that's why we take P as a criteria of efficiency

BPP^BPP = BPP (probalistic polynomial)

BQP^BQP = BQP
Amplification + Uncomputing

NP^NP \neq P^NP
\exists x \forall y C(x,y) accepts  (2QP problem)
can be used to define two quantifier predicate, can be even worse than NP.
NP^NP also called \Sigma_2^P

CoNP^NP (aka \Pi_2^P)
e.g. \forall x \exists y C(x, y) accepts

NP^CoNP = NP^NP
because you can flip the answer of your oracle

polynomial hierachy (PH)
PH = \Union \Sigma_i^P
= P \union NP \union NP^NP \union NP^(NP^NP) \union ....
it also contain all the \Pi_i^P s
you cannot substitute the bottom, but you can substitiute the topmost exponentiate
so, if P = NP, then P = PH
if P = CoNP, then the whole hierachy collapse to NP.

\exists an oracle A, P^A \neq NP^A, even if P = NP
because adding an oracle is changing the definition of complexity itself.
even if P and NP happen to be equal, we cannot substitute P with NP in every context
"obama = president", "if romney wins, romney = president" does not imply that "if romney wins, romney = obama".

Conjecture: PH is infinite

NP \intersect CoNP: factoring (decision version). believe not in P
regardless of whether you want yes/no answer, the prime factorization is the witness

If \forall L \in NP \intersect CoNP, L is NP-complete, then NP = CoNP  (that means NP \subset P^L)
that't why we believe that factoring is not NP-hard, because then the PH collapse.

Ladner's theorem
if P \neq NP then there is intermediate problem in NP but not P or NP-complete

open problem: is there a complete problem for NP \intersect CoNP? don't know
NP and CoNP there is syntactical criteria (nondeterministic TM), but NP \intersect CoNP not


#P = f: {0, 1}^{*} -> Int s.t. \exists polytime M s.t. \forall x f(x) = # w's s.t. M(x, w) accepts  (w are the witnesses)
all combinatorial counting problems
leave the realm of languages now

#SubsetSum is #P complete
#SAT
it is believed that given a NPC problem X, then #X is #P complete. no counter example, but no general proof


P^(#P)
this contains NP
Toda 1990: PH \subset P^(#P)   uses some number theory, some probalistic arguments, not obvious
will be assumed for Boson sampling.
