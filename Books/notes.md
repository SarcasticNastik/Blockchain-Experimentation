# Bitcoin and Cryptocurrency Technologies

## Basics

- **Message Digest**: Application of the property `collision resistance`
    
- **Hiding**: A hash function `H` is `hiding` if when a secret value `r`  is chosen from a probability distribution that has `high min-entropy`, given `H(r || x)`, it is infeasible to find `x`. 
Applications: 
1. Commitment scheme : Consists of two algos:
    - `com` := `commit(message, nonce)`
        Takes message and secret random value as input and returns commitment.
    - `ver` := `verify(com, message, nonce)`
        True if `commit(message, nonce) == com`.
    *Properties*: Hiding and Binding(infeasible to find distinct (msg1, nonce1) and (msg2, nonce2) s.t. com1 == com2).

- **Puzzle Friendliness**: A hash function H is said to be puzzle friendly if for every possible n-bit output value y, if k is chosen from a distribution with high min-entropy, then it is infeasible to find x such that H(k ‖ x) = y in time significantly less than 2ⁿ.
