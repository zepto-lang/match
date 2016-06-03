# match

A minimal pattern matching library for zepto.

## Installation
```
zeps install zepto-lang/match
# if you want to test your version of match
zeps test match
```

## Usage

For the normal user, there is but one endpoint
named `match`. Let's see how fizzbuzz is defined in terms
of this:

````clojure
(define (fizzbuzz n)
  (do ((i 1 (add1 i))) ((> i n))
    (match (list (modulo i 5) (modulo i 3))
      (((0 0) (write "fizzbuzz"))
       ((_ 0) (write "fizz"))
       ((0 _) (write "buzz"))
       ((_ _) (write i))))))
(fizzbuzz 15) ; => will print fizzbuzz until 15 inclusively
```

What does this do? Well, it counts from 1 to n (including n),
and doing a match function on the two needed moduli. If both are 0,
`fizzbuzz` is printed. If the second one (mod 3) is 0, `fizz` is printed...
You get the idea.

Deeply nested structures can also be matched, of course.

## Caveats

The pattern matching is *really* basic (the whole module amounts
to 34 lines). Some of the weaknesses are:

- Nesting and taking doesn't really play well with data structures other than lists.
  While (byte)vectors also work within structures, they currently do not work on the top level.
- There are no regexes, simply because zepto does not have regexes *yet*.
- There is no "catch-all" clause.

I hope this does not put you off too much. It should be somewhat
interesting to use anyway.

<hr/>

Have fun!
