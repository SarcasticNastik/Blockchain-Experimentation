# Blockchain Experimentation

## Introductory Stuff

## Cryptography

- **RSA**: *Asymmetric Key Cryptosystems* 

  Check the implementation for more info. (check the notebook)

  ​	<u>Problems</u>:  

- **Birthday Paradox** : In a room of $n$ people, alteast two people have birthday in a year of $d$ days on the same day? Ans: around $O(n)$.

**Digital Signatures**: Much like the signature on a currency. 

> A mathematical technique used to validate the authenticity and integrity of a message, software or digital document.

- Shouldn't be possible to forge.

Requirements: **Sign**$(sk; m)$, **Verification**$(V(pk;m;Sig) = True\ if \ valid \ signature)$ and **Key Generation**$(pk, sk)$.

#### Discrete Log Problem

*El' Gamal* problem reduces to *Discrete log problem*. (So as computationally hard as the other one)

#### Elliptical Curve Discrete Log Problem

$$x^2 / a^2 + y^2 / b^2 = 1$$

- Security provided by `168` bits ECDLP := by `1024` El' Gamal

#### Cryptographic Hash Functions

##### Desirable Properties

- Deterministic, Efficient
- Difficult to find a message from its hash (**pre-image resistance**)
- Infeasible to find out two messages having same has (**collision resistance**)

##### Properties

$hash\ =\ H()$

1. **Pre-image resistance** :: Given $h$, difficult to compute $m = H^{-1}(h)$
2. **Second pre-image resistance**:: Given message $x$, difficult to compute $y$ s.t. $H(x) = H(y), x \ne y$.
3. **Collision resistance**:: Difficult to find $x$, $y$ s.t $H(x) = H(y)$.

#### Usage

- Distributing trust :stuck_out_tongue:
- Message Digest

**Ex:** SHA, SHA1, SHA2, RIPEMD.