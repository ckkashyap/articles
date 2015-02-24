# Best programming language!

Many may discount the idea of "best programming language" with "all
languages have positives and negetives and that no one language could
be the best". But I believe, given a set of criteria we could compare
various programming languages and attempt to figure out which one is
better in most criteria. I will attempt to do so in this article.

And to those who may say that "languages dont matter; only algorithms
do" - may I remind you - COBOL is (was?) a programming language.

Just so you know where I am coming from - I am very familiar with C (I
have used it to implement x86 kernels) and Perl (I've read and love
the Camel) and have studied the following languages - Haskell,
Clojure, Go, Rust and Nim. (I'll leave Java and C++ out of the
discussion because they make me bitter). I consider myself as a power
vim user - I switched to Emacs about 4 years ago after being bitten by
the functional bug.

## Non criteria

### Static vs Dynamic typing

One argument that supports Static typing is that it helps in proving
correctness. The argument against it is that one can only prove that
the types line up - whether the program is correct from the programmer
intention point of view is questionable. Second, it is argued that
static types help with refactoring. Again, to the extent of types
aligning. Remember

```Haskell
sum = foldr (-) 0
```

is correct Haskell code - as in it compiles.

The argument for dynamic type system, in my opinion is flawed - they
talk about "compiler does not come in the way" etc - as in, one is
allowed to write "incorrect code" and are told about it only at run
time.

Anyway, my point is - if you have to shoot for correctness and speed
(development and runtime) - shoot for a good design first. The rest
will follow.

Design is a somewhat diluted term in the software industry so I'll go
with Rich Hickey's defintion - which is, I paraphrase here - the art
of breaking down a problem such that it can be composed
back. Essentially, your implementation must contain tiny modules each
of which do one thing. This, will help writing "evident code" that is
"obviously correct; instead of, without obvious mistakes"[0]. The
typesystem of the language per se does not help or come in the way of
design.

### IDE support

I'm just saying that I am not considering that as a parameter for
language comparison. If you think that's a grave ommision, you should
stop reading this article here.

### Indentation level as block structure

I can totally get it if you hate the idea. I myself did not like it
one bit. It was only after I studied Haskell that I learnt to bear it
and later love it.

So I feel - "Don't judge a language by it's choice for block
structure"!

### Software Transaction memory, CSP style channels

Clojure has demonstrated that these things can be built as a library
when your language powerful enough.

## Criteria

### Higher order function / Function as first class value

Lambda calculus is "Turing Complete" and it contains nothing more than
function definition and function application. There are plenty of
articles on the internet that demonstrate how, using just the
capability of function definition and function application, one could
build all the computing constructs - starting from numerals, booleans
etc

Even in "Why function programming matters", John Hughes demonstrated
how vital higher order functions are. Ofcourse, he also said that lazy
evaluation is vital - I disagree there since one can build "lazy
evaluation" once equiped with higher order functions [2].

Therefore, a programming language that has first class functions is more powerful
than a programming language that does not have it.

Almost all modern languages (new versions of old languages) support
hugher order functions in some form or other.


### Macro support

If the word macro evokes "C macro" / "conditional compilation" in your
mind, your probably also believe macros are bad. On the other hand,
folks from LSIP side believe that macros give them that extra power
(super power of programs that write programs[4]).

[4] covers the power of macros in great detail.

Therefore, a programming language that does not have a "powerful
macro" (access to AST at compile time) support is inferiour.

Languages (that I know of) that support macros are - Lisp/Scheme, Clojure, Nim,

### Strict (Applicative order) evaluation

According to "Why Functional Programming Matters" - Lazy evaluation is
one of the two key features that is necessary for a language to
fascilitate modularity. The other feature being higher order
functions. Two points to keep in mind here

  1. Lazy evaluation can be implemented in strict languages -
  http://matt.might.net/articles/implementing-laziness/

  2. Laziness mixed with IO is unpleasant (to put it very mildly)

So I conclude that a language that has Laziness by default and a
tedious way to do/reason about IO is undesirable.

The only "mainstream" language that has lazy evaluation by default and
unreasonable (as in hard to reason about) IO is Haskell.


### Reach

These days I almost always have to deal with Mac, Linux and Windows
and switch between them. On top of that I play with Raspberry-pi. So
if I have to invest "10,000 hours" I'd like to it to be in a language
that I can use across all machines (of today and tomorrow).

A language that limits my reach is inferior to the one that does not.

Only C and Nim are the good languages in this category.

### Ability to target machine code

It is a good idea to program an abstract machine, instead of a real
machine. However, not at the cost of never being able to program a
specific machine for it's cool features - or having to jump through
hoops to do it.

Generating native binaries also make it easier to use it with other
systems. Almost all languages (that dont generate native code) provide
a mechanism to load shared libraries (DLL's) and invoke functions.

Now, you may say that, so long as your job gets done, it does not
really matter if the actual machine code is executed vs iterpreted by
another layer of software. Also, you may argue that virtual machines
provide additional opportunities for optimization. I don't agree with
either.

First of all, I'd like to waste as little cycles as possible. Now,
battery life etc are legitimate reasons for it but I argue that it is
actually the essence of using computers - improving efficiency. So, it
does matter to me if I am not using optimum memory and CPU cycles. I
mean, if you use up more than required resources in "getting your
job", the remaining resources will limit what more can be achieved.

About optimization opportunity - yes, it is possible to demonstrate
some kind of runtime optimization that may not be possible on today's
hardware - but that can never be something that cannot be fixed in the
next version of the processor/compiler.

So, if your compiler does not emit native code, it's inferior to the
one that does.

Haskell, C, OCaml, Rust, Go and Nim are the good languages in this
category.

### Memory management / Garbage collection

Garbage colleciton are of two kinds[5] - tracing and non-tracing. The
tracing variety is the most common and it involves keeping track of
which objects are "reachable" from root. This introduces a fair amount
of non-determinism in the runtime of the program. Typically, the
languages that have tracing garbage collector do not give direct
access to memory. So, if a language uses a tracing garbage collector
and does not give you a mechanism to handle memory directly then it's
inferior to the oned that give you direct access to memory and either
dont have garbage collection or use a non-tracing garbage collection.

C, Rust and Nim are the good languages in this category.

## Summary

Based on the criteria that I came up with, Nim is a clear winner :)


#### References
* [0] Simon Peyton Jones talks
* [1] http://matt.might.net/articles/implementing-laziness
* [2] http://www.cs.kent.ac.uk/people/staff/dat/miranda /whyfp90.pdf
* [4] http://www.paulgraham.com/avg.html
* [5] http://en.wikipedia.org/wiki/Garbage_collection_%28computer_science%29
