List of papers at tonight
Pick one by next Friday
Next Tues: Alex Arkhipov

Last Time:
Per - #P complete
Det - in P

Per(A) = 2^{-n} \Sum_{X_1, ... , X_n \in {-1, 1}} X_1 \times ... \times X_n \Prod_{i=1}^n (a_{i1}X_1 + ... + a_{in}X_n)
<= ||A||^n
approximate the expectation with expectation of random samples
|Per(A)| <= ||A||^n
the permanent of a unitary matrix <= 1
if you want to approximte something |Per| <=1, with O(n^2 / \epsillon^2) samples you get precision of \epsilon
suggested by Gurvits, Gurvits Algorithm

Quantum Mechanics of one particle with discrete states (modes)
(e.g. mode can be just physical position, but there are other modes, like polarization mode, energy mode,
but that doesn't matter, we just think of them as different buckets where the particles can be)
|\psi> = \Sum_{i=1}^{m} \alpha_i |i>, \Sum_{i=1}^{m} |\alpha_i|^2 = 1

U \in C^{m \times m}, U |\psi> is a new superposition (unitary transformation)

you have this unitary transformation that you want, how do you synthesis (implement) it?

basic unit: Beamsplitter - 2 x 2 unitary matrix
( cos\theta  sin\theta)
(-sin\theta  cos\theta)

Phaseshifter - 1 x 1 unitary matrix  (e^{i\theta})

you can apply beamsplitter to any two modes you want, phaseshifter to any one mode you want

like
(1 0 0)(1   0       0     )
(0 i 0)(0 1/sqrt2  1/sqrt2)
(0 0 1)(0 -1/sqrt2 1/sqrt2)
not a tensor product, it's called a direct sum of the hilbert space

this is very different from qbits (with n modes only logn qbits)

qbit-based quantum computing, there is no hope to implement all unitary transformation permitted by laws physics,
because the number of unitaries grows doubly exponential with n

but here the number of unitaries only grows exponential (not doubly),
with poly(m) basic units (beamsplitters, phaseshifters) we can implement any unitaries

Reck et al 1994 you can implement any unitary you want with O(m^2) basic units,
it's actually simpler than a similar theorem for qbit-based QC
idea is Gausian elimination

more interesting thing happens when there's more than one particle
suppose there're
m modes
n particles
|S_1, ..., S_m>  S >= 0, S_1 + ... + S_m = n
\Phi_{m,n} = { (S_1, ..., S_m) s.t. S_i >= 0 and sum(S_i) = n }, a hilbert space

sometimes it's possible to do universal quantum computing with just one particle, if m is large
but packing too many modes to limited space -> system collapses into a black hole

definition of a photon is what increases the occupation of the photon mode by 1
there is no distinction between this photon and that photon

this hilbert space (\Phi_{m,n}) is a different animal, symmetric product hilbert space
is there entanglement or no entanglement in this space? are the states entangled?
we'll never interact a particle with another (there's no force)
but in another sense, even one photon can be entangled (with itself)
"but you say that doesn't make sense, it takes two to tangle"

write your superposition in occupation number basis
|1,0> + |0, 1>
--------------
   sqrt(2)

the normal entanglement is defined for tensor product hilbert space. not for symmetric product hilbert space.
but if you project the above thing to tensor product hilbert space, it's in entanglement state.
"my favorite paper on Arxiv, title is 1,0 + 0,1, and the comment says 'is entangled'. "

someone use one photon like this to violate the Bell inequality.

we got m bins, how many ways to arrange n particles?
imagine n particles, put (m-1) bars
o | o o | | o
M = {n+m-1 \choose n}
"I'll call it the capital M, this is the dimension of my hilbert space."
it will be exponential
"in that regime, the capital M will be exponential, so we do have the exponentiality."

U \in C^{m \times m} -> \phi(U) \in \C^{M \times M}   (the former: 1 particle, the latter: n particles)
"we want to know how do phaseshifters and beamsplitters act when we lift from one particle to n particles"
\phi: the "lifting" operator
homomorphism
because then we can decompose any U into phaseshifters and beamsplitters (product of them),
and using homomorphism to solve the liftted version

Let's start with a phaseshifter
U = (e^{i\theta})  \phi(U) |n> = e^{in\theta} | n >
U = ( a b )
    ( c d )

\phi(U) | s \
        | t /

there is a formula that you could take as a law of physics, but we'll try to see how to derive it
<s,t| \phi(U) |u, v>
where s+t = u+v

= \sqrt{\frac{u! v!}{s! t!}} \Sum_{k+l = u, k<=s, l<=t} {s \choose k}{t \choose l} a^{k} b^{s-k} c^{l} d^{t-l}

OK that is the answer
let me show you what is a better way to think of it

creational operators
so it's not a unitary
you can put a Hamiltonian of it

\Sum_{S = (s_1, ..., s_m) summing up to n} ways of distributing exponents among
homogeneous polynomials
\Sum_{S = (s_1, ..., s_m) summing up to n} \alpha_S X_1^{s_1} X_2^{s_2} ... X_{m}^{s_m}
Pr[ S ] = |\alpha_S|^2 s_1! ... s_n!

need to keep track of the normalizing factors! (\sqrt of factorials product)

X^{S} = x_1^{S_1} \times ... \times x_m^{S_m} (it's a short hand)

p(x) = \Sum_{S \in \Phi_{m,n}} \alpha_{S} X^{S}
q(x) = \Sum_{S \in \Phi_{m,n}} \beta_{S} X^{S}
Fock inner product
<p, q> = \Sum_{S} \bar{\alpha_S} \beta_{S} s_1! \times ... \times s_{m}!

<p, q> = E_{x ~ N(0, 1)^m_{C}} [ \bar{p}(x) q(x) ]   \bar means conjugate complex, N means gaussian distribution
E[X^{2s}] when X ~ Gaussian is just s!


step back
classical system,
classical balls, how many balls in each of m bins
an operator: probability of throwing a ball from bin i to bin j
a stochastic matrix (m by m, sum to one) transition matrix
what's the probability of getting to some state?
it gets messy we have to deal with normalization
Per(P)

the difficulty of quantum case is that the transition matrix is unitary (complex matrix),
and Per(P) cannot be efficiently approximated.

<p, q> = < U[p], U[q] >  it (< , >) is unitarily invariant

p(x) = \Sum_{S \in \Phi_{m,n}} \alpha_{S} X^{S} = \Sum_{S \in \Phi_{m,n}} \alpha_{S} x_1^{S_1} \times ... \times x_m^{S_m}
U[ p ]:
X_1 -> (U_{11} X_1 + ... + U_{1m} X_m)
X_2 -> (U_{21} X_1 + ... + U_{2m} X_m)
...
X_m -> (U_{11} X_1 + ... + U_{1m} X_m)

because Gaussian is unitarily invariant, so < , > must be

<s,t| \phi(U) |u, v>
= \sqrt{\frac{u! v!}{s! t!}} \Sum_{k+l = u, k<=s, l<=t} {s \choose k}{t \choose l} a^{k} b^{s-k} c^{l} d^{t-l}
x^{s}y^{t} -> (ax+by)^s (cx+dy)^t
coming from the Fock polynomials

look at these Fock polynomials
start with one photon
X_1 ... X_n   change of bases
->
(u_{11} X_1 + ... + u_{1n} X_n) \times ... \times (u_{n1} X_1 + ... + u_{nn} X_n)
Per(U)

<S| \phi(U) |T>
|S> = |s_1, ... , s_m>
|T> = |t_1, ... , t_m>
<S| \phi(U) |T>
= Per(U_{S, T} / \sqrt{s_1! ... S_m! t_1! ... t_m!})
U_{S,T} \in C^{n \times n}

e.g.
U = 1/\sqrt{2} (1  1)
               (1 -1)
S = (2, 1), T = (0, 3)

U_{S,T} = 1/\sqrt{2} ( 1  1  1
                       1  1  1
                      -1 -1 -1 )
duplicate each row of U S_i times, and each column of U T_j times

if S and T are collision-free (each element is 0 or 1), then U_{S,T} is just submatrix of U, otherwise it's not

|1, 1> apply a beamsplitter, classical should be 1/4 for  |2,0> |0,2> and 1/2 for |1,1>
but quantum, not, because of interference, it's actually 1/2 for |2,0> and |0,2>, and 0 for |1,1>

<1, 1| \phi(U) |1, 1> = 0

Hongou Mondel
