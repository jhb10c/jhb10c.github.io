## Introduction to Plonk - Part 1


#### Disclaimer: Feel free to reach out if there is any details that are incorrect. 

``` 
    For the Snark's a peculiar creature, that won't
    Be caught in a commonplace way.
    
```


The mysterious snark appears in the poem, The Hunting of the Snark by Lewis Carrol. During the referenced hunt, the Bellman describes five unmistakable marks of the snark. This description gives no indication of what a snark really is. In a similiar way, modern SNARKs are incoherent (to me at least) with out a large amount of background. The goal of these notes is to present enough information to paint the picture of these interesting objects. 

Future topics that will be covered will include:

- Plonk (Toy) Implementation 
- Fiat Shamir transformation 
- Fast Fourier Transform
- Elliptic Curve Cryptography
- Miller's algorithm

The acronym SNARK itself is short for “Succinct Non-Interactive Argument of Knowledge”. It allows one party to prove to another party that a statement is true with high probability. This is a particular instance of an interactive proof system. Let's look at an example of a proof system. Then we wil look more formally at it's defintion 


## Interactive Proof for Graph Non-isomorphism

Suppose Peggy and Vinny are two friends. Peggy and Vinny both have an astounding ability: they are both able to duplicate objects perfectly. One day they are strolling through a garden of graphs. They both notice two intricate graphs $G_1$ and $G_2$. Peggy boldly claims to Vinny that she is pretty good at telling graphs apart given enough time.Vinny does not believe really believe her. So Peggy proposes that they play a game. 

- Peggy will close her eyes, Vinny will duplicate both graphs ($G_1$ and $G_2$) and rotate or deform (no tearing) the graph in any way to produce the graphs $G_1'$ or $G_2'$. 
- Vinny then gives Peggy either (G_1,G_1') or (G_1,G_2').
- Peggy will open her eyes and decide whether this new graph $G_i'$ is a duplicate of $G_1$ or $G_2$.

Peggy claims she can pick correctly more often then not and is even willing to bet money on it! 

Here is why Peggy should bet on this game! 

1. Suppose $G_1$ and $G_2$ are not the same. (They are not isomorphic.) If Peggy receives $G_2'$ (resp. $G_1'$) then she is able to verify that $G_1$ (resp. G_2) is different from $G_2'$ (resp. $G_1'$) because $G_1$ and $G_2$ are not isomorphic. So she is able to always win in this scenario. 

2. Suppose $G_1$ and $G_2$ are the same. Given $G_i'$, Peggy has 1/2 probability of choosing correctly since all graphs are isomorphic to each other. 

If these events are equally likely to occur and then Peggy can correctly choose with probability 3/4! Therefore Peggy should play this game as much as possible given the right bet setup. 


## Definiton of a Proof System 

Lets define now what an interactive proof system formally is: 


An interactive proof system for a set S is a two-party game between a verifier executing a probabilistic polynomial time strategy and a prover that executes a (computationally unbounded) strategy satisfying the following two conditions:

- Completeness: For every $x \in S$, the verifier always accepts after interacting with the prover P on common input x.
- Soundness: For every $x$ not in $S$ and every Prover P, the verifier rejects with probability at least $1/2$ after interacting with P on common input x. 


The completeness condition more or less states that the verifier will always accept the results of an honest prover. While the soundness condition states that the verifier will accept at the results of a dishonest prover with at most a 1/2 probability. 

In the example above, our verifer (Vinny) accepts always when our prover (Peggy) is honest if the graphs are not isomorphic. In this sense, Vinny will always be okay with losing. On the otherhand, Vinny while accept (1/2) of the time when our prover (Peggy) is guessing and the other half of the time he will catch her guessing.  


## Reference

- https://www.wisdom.weizmann.ac.il/~oded/pps-primer.html



```python

```
