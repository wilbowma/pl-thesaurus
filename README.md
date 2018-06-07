# A Thesaurus For Programming Languages Jargon


For now, this is list of synonyms for technical words that I want to stop
keeping in my head and allow people to publicly contribute to/comment on.
Maybe one day I'll turn it into structured data that a tool can consume.

There's also a wiki for discussion: https://github.com/wilbowma/pl-thesaurus/wiki

# Thesaurus

- dependent function type, pi type, dependent product type, universal quantifier
  - This may be at odds with one's intuition, since, in non-dependent settings, product type can mean pair.
    It may help to note that we can implement (lazy) "product types" as a function from a tag to either the first or second component, whose type depends on the tag---that is, product types can be implemented with as a dependent functions (with `bool`, `if`, and large elimination).
    ```
    A * B = Pi (x : bool) (if x then A else B)
    pi_1 M = M true
    pi_2 M = M false
    (M_1,M_2) = lambda x. if x then M_1 else M_2
    ```
- dependent pair type, sigma type, dependent sum type, existential quantifier, subset type, refinement type
  - This can be particularly confusing since, in non-dependent settings, sum type can mean tagged union.
    This is not as confusing as it may first appear, since we can implement sum
    types as a pair of a tag plus its computational content, whose types depends
    on its tag---that is, sum types can be implemented with dependent pairs as
    long as we also have `boolean`, `if`, and large elimination:
    ```
    A + B = Sigma (x: bool) (if x then A else B)'
    inl y = (true, y)
    inr z = (false, z)
    case x of { inl y -> M | inr z -> N } = if (pi_1 x) then (M[pi_2 x]) else (N[pi_2 x])
    ```
- pair (type), product (type), tuple (type)
- sum (type), disjoint union (type), tagged union (type), variant (type) 
- dependent types, type dependency
  - The latter form can be confusing because dependency has been used to refer to information flow, as in the Dependency Core Calculus.
- certifying compilation, translation validation
- Adjunction
  - When the categories are Posets, an adjunction is called a *Galois connection*
- Monad, (Kleisli) triple, S4 possibility modality
  - When the category is a poset, a monad is called a *closure operator*
- Strong Monad, S4 lax modality
- Comonad, S4 necessity modality
  - When the category is a poset, a comonad is called an *interior operator*
- Coreflection 
  - When the categories are posets, it is called a Galois Insertion or Galois Injection
  - When the posets are domains/cpos, it is called an *embedding-projection pair*
- Reflection (category theory)
  - when the categories are posets, it is called a Galois Surjection
- Right adjoint (category theory)
  - In order theory, the right adjoint of a Galois connection is called the *upper adjoint*
  - In abstract interpretation, the right adjoint of a Galois connection is called the *Concretization function*
- Left adjoint (category theory)
  - In order theory, the left adjoint of a Galois connection is called the *lower adjoint*
  - In abstract interpretation, the left adjoint of a Galois connection is called the *abstraction function*
- ⊤⊤-closure, ⊥⊥-closure, biorthogonality
- axiom K, equivalence reflection, propositional extensionality

# References

- Intuitionistic S4 Modal Type Theory
  - [Pfenning and Davies, A Judgmental Reconstruction of Modal Logic](https://www.cs.cmu.edu/~fp/papers/mscs00.pdf)
