# Blockchain Experimentation

## Introductory Stuff

### Cryptography

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

##### **El' Gamal**

$g$ -> Generator, large prime

- $h = g^x\ mod\ p$

**Public Key**: $$(h, g, p)$$					

**Secret Key**: $(x, g, p)$

- **Encryption:** If a message $m$ ought to be sent, 

  1. Choose random $y$ from (1, p)
  2. $S =  h^y\ mod\ p$
  3. $c_2 = m \times s\ mod\ p$
  4. $c_1 = g^y\ mod\ p$

- Send $(c_1, c_2)$

- **Decryption:** $(c_1^x)^{-1}c_2$ is the decrypted message.

- **Signature**: $(r, s)$

  1. $$h = g^x\ mod\ p$$

  2. Select random $k$ from $(1, p - 1)$

  3. $r = g^k\  mod\ p$; $s = k^{-1} (m\ - xr)\ mod\ p$ (;;m is message here)

- **Verification**:

   $$\begin{align*} h^r r^s\ mod\ p &= g^{xr}(g^{k})^{k^{-1}(m - xr)}\ mod\ p\\ &= g^{xr} \times g^{m - xr}\ mod\ p\end{align*}$$

#### Elliptical Curve Discrete Log Problem

$$x^2 / a^2 + y^2 / b^2 = 1\ mod\ p$$ given $(a, b)$

- Security provided by `168` bits ECDLP := by `1024`bits El' Gamal

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

### Desirable properties of Cryptocurrency

- Decentralized
- Anonymous
- Mining not associated with any currency/ commodity (in real world)
- Should avoid *double spending*

## [Distributed Consensus](https://www.preethikasireddy.com/post/lets-take-a-crack-at-understanding-distributed-consensus)

- [Fischer-Lynch-Paterson Impossibility](https://en.wikipedia.org/wiki/Consensus_(computer_science)#The_FLP_impossibility_result_for_asynchronous_deterministic_consensus): Under some conditions, distributed consensus is impossible even with one single faulty node.

- **Paxos**: Never produces inconsistent results.(but assumptions are many) 
- **RAFT** used now-a-days.

### Bitcoin Consensus

- Broadcast transactions to all the nodes
- Each node collects new transactions into a block.
- A *random* node gets chance to write the ledger. It broadcasts this block.
- Nodes accept the blog, if they include it's hash in the next block they create.
- *Longest chain* is considered **valid**.

#### Selecting a random node

- Not using *IP*, cuz of *Sybil attacks*.
- Solving a crypto puzzle and select whoever solves it first.

#### Malicious Node

- **Stealing**
- **DoS** (Denial of Service)
- **Double spending**

### Puzzles

**Ex:-** $$Find\ out \ a\ nonce\ s.t.: \\ H(nonce || prev\_hash || tx_1 || tx_2 || \ldots)\ \lt target$$

- **Miner**: Node which writes the next block.
- **Block reward**: Miner plays himself (using game theory just google :p)

### Applications of BitCoin Scripts

1. **Escrow Transactions**:
2. **Green Addresses**:
3. **Micro-payments**:

