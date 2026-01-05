# Mutual recursion - Wikipedia

Two functions defined from each other

In [mathematics](/broken/pages/d856f51518ea692bbfeb89d0bebc69911ea7f47d) and [computer science](/broken/pages/5248336dedd7b7a032621eb6ebcca48cf5ef38fc), **mutual recursion** is a form of [recursion](/broken/pages/7978d43c1bef7ed92e9b47a4059f07bf61e02755) where two or more mathematical or computational objects, such as functions or datatypes, are defined in terms of each other.\[1] Mutual recursion is very common in [functional programming](/broken/pages/e7717a6c03fb2c65cba76a82355e867bd7f7ebd6) and in some problem domains, such as [recursive descent parsers](/broken/pages/0c12e8d64adad1a8fdf6e2eb06bc512abfc5773b), where the datatypes are naturally mutually recursive.

### Examples

#### Datatypes

Further information: [Recursive data type](/broken/pages/b703ecbfe5c4df2cb7fb198fda5156a519d2cb56)

The most important basic example of a datatype that can be defined by mutual recursion is a [tree](/broken/pages/4de6f22bbf73216b0a513fe9a4691cd21b3726e6), which can be defined mutually recursively in terms of a forest (a list of trees). Symbolically:

```
f: [t[1], ..., t[k]]
t: v f
```

A forest f consists of a list of trees, while a tree t consists of a pair of a value v and a forest f (its children). This definition is elegant and easy to work with abstractly (such as when proving theorems about properties of trees), as it expresses a tree in simple terms: a list of one type, and a pair of two types. Further, it matches many algorithms on trees, which consist of doing one thing with the value, and another thing with the children.

This mutually recursive definition can be converted to a singly recursive definition by [inlining](/broken/pages/db9c4141ca83b18cbd84dcf620a0c7d6fc4caf04) the definition of a forest:

```
t: v [t[1], ..., t[k]]
```

A tree t consists of a pair of a value v and a list of trees (its children). This definition is more compact, but somewhat messier: a tree consists of a pair of one type and a list of another, which require disentangling to prove results about.

In [Standard ML](/broken/pages/79c10d2343611df39da41984a782c2fdf5ce3d8a), the tree and forest datatypes can be mutually recursively defined as follows, allowing empty trees:\[2]

{% code title="Standard ML" %}
```sml
datatype 'a tree = Empty | Node of 'a * 'a forest
and      'a forest = Nil | Cons of 'a tree * 'a forest
```
{% endcode %}

#### Computer functions

Just as algorithms on recursive datatypes can naturally be given by recursive functions, algorithms on mutually recursive data structures can be naturally given by mutually recursive functions. Common examples include algorithms on trees, and [recursive descent parsers](/broken/pages/0c12e8d64adad1a8fdf6e2eb06bc512abfc5773b). As with direct recursion, [tail call optimization](/broken/pages/f407e1a2542cb7cfd3af5bc23052bca604380895) is necessary if the recursion depth is large or unbounded, such as using mutual recursion for multitasking. Note that tail call optimization in general (when the function called is not the same as the original function, as in tail-recursive calls) may be more difficult to implement than the special case of tail-recursive call optimization, and thus efficient implementation of mutual tail recursion may be absent from languages that only optimize tail-recursive calls. In languages such as [Pascal](/broken/pages/ac77b3130af9545c8909cf31253c02733233b028) that require declaration before use, mutually recursive functions require [forward declaration](/broken/pages/ab70025067f0ef5cadddc25a92ca7e46a2bf3ca2), as a forward reference cannot be avoided when defining them.

As with directly recursive functions, a [wrapper function](/broken/pages/7978d43c1bef7ed92e9b47a4059f07bf61e02755#Wrapper_function) may be useful, with the mutually recursive functions defined as [nested functions](/broken/pages/0d39ca9b745e6461d47df9f40a79592697105d4c) within its scope if this is supported. This is particularly useful for sharing state across a set of functions without having to pass parameters between them.

**Basic examples**

A standard example of mutual recursion determines whether a non-negative number is even or odd by defining two separate functions that call each other, decrementing by 1 each time.\[3] In C:

{% code title="C (is_even / is_odd)" %}
```c
bool is_even(unsigned int n) {
    if (n == 0) {
        return true;
    } else {
        return is_odd(n - 1);
    }
}

bool is_odd(unsigned int n) {
    if (n == 0) {
        return false;
    } else {
        return is_even(n - 1);
    }
}
```
{% endcode %}

These functions are based on the observation that the question "is 4 even?" is equivalent to "is 3 odd?", which is in turn equivalent to "is 2 even?", and so on down to 0. This example is mutual [single recursion](/broken/pages/92965d5e810d6c65ba9dce5ea524c79e2f8f2251), and could easily be replaced by iteration. In this example, the mutually recursive calls are [tail calls](/broken/pages/dc90bd3d6f09e918fbf30d820c9e7720bf7d0a90), and tail call optimization would be necessary to execute in constant stack space. In C, this would take O(n) stack space, unless rewritten to use jumps instead of calls.\[4] This could be reduced to a single recursive function is\_even. In that case, is\_odd, which could be inlined, would call is\_even, but is\_even would only call itself.

As a more general class of examples, an algorithm on a tree can be decomposed into its behavior on a value and its behavior on children, and can be split up into two mutually recursive functions, one specifying the behavior on a tree, calling the forest function for the forest of children, and one specifying the behavior on a forest, calling the tree function for the tree in the forest. In Python:

{% code title="Python" %}
```python
def f_tree(tree: Tree) -> None:
    f_value(tree.value)
    f_forest(tree.children)

def f_forest(forest: Forest) -> None:
    for tree in forest:
        f_tree(tree)
```
{% endcode %}

In this case the tree function calls the forest function by single recursion, but the forest function calls the tree function by [multiple recursion](/broken/pages/6a3df5291d0393b2c8c235f0b8115009330fd206).

Using the Standard ML datatype above, the size of a tree (number of nodes) can be computed via the following mutually recursive functions:\[5]

{% code title="Standard ML (size_tree / size_forest)" %}
```sml
fun size_tree Empty = 0
  | size_tree (Node (_, f)) = 1 + size_forest f
and size_forest Nil = 0
  | size_forest (Cons (t, f')) = size_tree t + size_forest f'
```
{% endcode %}

A more detailed example in [Scheme](/broken/pages/834fd3d9ce77622ecabbd4f19055ce7d19e75a58), counting the leaves of a tree:\[6]

{% code title="Scheme (count-leaves)" %}
```scheme
(define (count-leaves tree)
  (if (leaf? tree)
      1
      (count-leaves-in-forest (children tree))))

(define (count-leaves-in-forest forest)
  (if (null? forest)
      0
      (+ (count-leaves (car forest))
         (count-leaves-in-forest (cdr forest)))))
```
{% endcode %}

These examples reduce easily to a single recursive function by inlining the forest function in the tree function, which is commonly done in practice: directly recursive functions that operate on trees sequentially process the value of the node and recurse on the children within one function, rather than dividing these into two separate functions.

**Advanced examples**

A more complicated example is given by [recursive descent parsers](/broken/pages/0c12e8d64adad1a8fdf6e2eb06bc512abfc5773b), which can be naturally implemented by having one function for each [production rule](/broken/pages/6e24a68b357847a9f14584c75577b478f0a0b2d8) of a grammar, which then mutually recurse; this will in general be multiple recursion, as production rules generally combine multiple parts. This can also be done without mutual recursion, for example by still having separate functions for each production rule, but having them called by a single controller function, or by putting all the grammar in a single function.

Mutual recursion can also implement a [finite-state machine](/broken/pages/b05aef192fedcdbe5cee0ed7326971291297b16f), with one function for each state, and single recursion in changing state; this requires tail call optimization if the number of state changes is large or unbounded. This can be used as a simple form of [cooperative multitasking](/broken/pages/5e2d54a08507701d5048978f0fa3ea39a069c946). A similar approach to multitasking is to instead use [coroutines](/broken/pages/9e0963caaa64643bf52385a4b563ba4a18c2633e) which call each other, where rather than terminating by calling another routine, one coroutine yields to another but does not terminate, and then resumes execution when it is yielded back to. This allows individual coroutines to hold state, without it needing to be passed by parameters or stored in shared variables.

There are also some algorithms which naturally have two phases, such as [minimax](/broken/pages/720ef88b9c191fa22500501239cd12d5132e1009) (min and max), which can be implemented by having each phase in a separate function with mutual recursion, though they can also be combined into a single function with direct recursion.

#### Mathematical functions

In mathematics, the [Hofstadter Female and Male sequences](/broken/pages/584a93778fc784951bfe1ccc2a6396531204eaef) are an example of a pair of integer sequences defined in a mutually recursive manner.

Fractals can be computed (up to a given resolution) by recursive functions. This can sometimes be done more elegantly via mutually recursive functions; the [Sierpiński curve](/broken/pages/22c67d23cebe65c3103617878db8a87b5603971c) is a good example.

### Prevalence

Mutual recursion is very common in [functional programming](/broken/pages/e7717a6c03fb2c65cba76a82355e867bd7f7ebd6), and is often used for programs written in [LISP](/broken/pages/084478db2a320be5fb8cd8c08d4c850e2601ffcd), [Scheme](/broken/pages/834fd3d9ce77622ecabbd4f19055ce7d19e75a58), [ML](/broken/pages/ef88c2e987f6d2493e1e95a798f506e7c1c2ba5f), and similar [programming languages](/broken/pages/bc39e627c48de21ab77f3fd32b5e0e871c5bda90). For example, Abelson and Sussman describe how a [meta-circular evaluator](/broken/pages/824bfd5fa84d4bddf184cd71f80d62d483917d45) can be used to implement LISP with an eval-apply cycle.\[7] In languages such as [Prolog](/broken/pages/99180eb773649df473ec1497e1e62ff5d90fb682), mutual recursion is almost unavoidable.

Some programming styles discourage mutual recursion, claiming that it can be confusing to distinguish the conditions which will return an answer from the conditions that would allow the code to run forever without producing an answer. [Peter Norvig](/broken/pages/20206f1449697d05e75c90d9b8cf314f1da4c7c3) points to a [design pattern](/broken/pages/ca800e53cab13c74768984b578e9ef63f4972f42) which discourages the use entirely, stating:\[8]

> If you have two mutually-recursive functions that both alter the state of an object, try to move almost all the functionality into just one of the functions. Otherwise you will probably end up duplicating code.

### Terminology

Mutual recursion is also known as [indirect recursion](/broken/pages/cf39084b9e49c264f12afb89fc56dc3527fbb707), by contrast with [direct recursion](/broken/pages/50eae4288ddfc39185271293c0dc6a3b282069d9), where a single function calls itself directly. This is simply a difference of emphasis, not a different notion: "indirect recursion" emphasises an individual function, while "mutual recursion" emphasises the set of functions, and does not single out an individual function. For example, if f calls itself, that is direct recursion. If instead f calls g and then g calls f, which in turn calls g again, from the point of view of f alone, f is indirectly recursing, while from the point of view of g alone, g is indirectly recursing, while from the point of view of both, f and g are mutually recursing on each other. Similarly a set of three or more functions that call each other can be called a set of mutually recursive functions.

### Conversion to direct recursion

Mathematically, a set of mutually recursive functions are [primitive recursive](/broken/pages/b33657221caad56c3147d2db7d73ee5344201816), which can be proven by [course-of-values recursion](/broken/pages/2a4ec7c1ce9a1be9c1479f6e66fb4d2621062fbb), building a single function F that lists the values of the individual recursive function in order: F = f1(0), f2(0), f1(1), f2(1), … and rewriting the mutual recursion as a primitive recursion.

Any mutual recursion between two procedures can be converted to direct recursion by inlining the code of one procedure into the other.\[9] If there is only one site where one procedure calls the other, this is straightforward, though if there are several it can involve code duplication. In terms of the call stack, two mutually recursive procedures yield a stack ABABAB..., and inlining B into A yields the direct recursion (AB)(AB)(AB)...

Alternately, any number of procedures can be merged into a single procedure that takes as argument a [variant record](/broken/pages/fe724e52cf797eb58f8b3edc549e0d1b8dbae42c) (or [algebraic data type](/broken/pages/fd882ffe2d166b554ed7f40834a6e3d20f3a9ce2)) representing the selection of a procedure and its arguments; the merged procedure then dispatches on its argument to execute the corresponding code and uses direct recursion to call self as appropriate. This can be seen as a limited application of [defunctionalization](/broken/pages/5bc4e191fb557d3176cb1771bb53f84e8c37398f).\[10] This translation may be useful when any of the mutually recursive procedures can be called by outside code, so there is no obvious case for inlining one procedure into the other. Such code then needs to be modified so that procedure calls are performed by bundling arguments into a variant record as described; alternately, wrapper procedures may be used for this task.

### See also

* [Cycle detection (graph theory)](/broken/pages/28e297b4be96c38efedfbb3bfd0b85ee0103bf59)
* [Recursion (computer science)](/broken/pages/7978d43c1bef7ed92e9b47a4059f07bf61e02755)
* [Circular dependency](/broken/pages/a88a7153bf048d5793f9e9ce3ca61bcde04d082f)

### References

1. Manuel Rubio-Sánchez, Jaime Urquiza-Fuentes, Cristóbal Pareja-Flores (2002), "A Gentle Introduction to Mutual Recursion", Proceedings of the 13th annual conference on Innovation and technology in computer science education, June 30–July 2, 2008, Madrid, Spain.
2. Harper 2000, "Date Types". https://www.cs.cmu.edu/\~rwh/introsml/core/datatypes.htm
3. Hutton 2007, 6.5 Mutual recursion, pp. 53–55. https://books.google.com/books?id=olp7lAtpRX0C\&pg=PA53\&dq=%22mutual+recursion%22
4. "Mutual Tail-Recursion" and "Tail-Recursive Functions", A Tutorial on Programming Features in ATS, Hongwei Xi, 2010. http://www.cs.bu.edu/\~hwxi/ATS/DOCUMENT/TUTORIALATS/HTML/c244.html
5. Harper 2000, "Datatypes". https://www.cs.cmu.edu/\~rwh/introsml/core/datatypes.htm
6. Harvey & Wright 1999, V. Abstraction: 18. Trees: Mutual Recursion, pp. 310–313. https://books.google.com/books?id=igJRhp0KGn8C\&pg=PA310\&dq=%22mutual%20recursion%22
7. Abelson, Harold; Sussman, Gerald Jay; Sussman, Julie (1996). Structure and Interpretation of Computer Programs (PDF). p. 492. ISBN 978-0262510875. https://web.mit.edu/alexmv/6.037/sicp.pdf
8. Solving Every Sudoku Puzzle — Peter Norvig. http://norvig.com/sudoku.html
9. On the Conversion of Indirect to Direct Recursion by Owen Kaser, C. R. Ramakrishnan, and Shaunak Pawagi (1993). http://delivery.acm.org/10.1145/180000/176510/p151-kaser.pdf?key1=176510\&key2=1857140721\&coll=GUIDE\&dl=GUIDE\&CFID=82873082\&CFTOKEN=54657523
10. Reynolds, John C. (August 1972). "Definitional Interpreters for Higher-Order Programming Languages" (PDF). Proceedings of the ACM Annual Conference. pp. 717–740. http://www.brics.dk/\~hosc/local/HOSC-11-4-pp363-397.pdf

Further reading:

* Harper, Robert (2000), Programming in Standard ML. https://www.cs.cmu.edu/\~rwh/introsml/
* Harvey, Brian; Wright, Matthew (1999). Simply Scheme: Introducing Computer Science. MIT Press. ISBN 978-0-26208281-5.
* Hutton, Graham (2007). Programming in Haskell. Cambridge University Press. ISBN 978-0-52169269-4.

External links

* Mutual recursion at Rosetta Code: http://rosettacode.org/wiki/Mutual\_recursion

Retrieved from "https://en.wikipedia.org/w/index.php?title=Mutual\_recursion\&oldid=1325630775"

Categories: Theory of computation; Recursion
