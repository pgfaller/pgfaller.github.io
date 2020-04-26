Language Basics

Clojure provides a number of standard data types, most of which should look familiar:

* Vars provide mutable storage locations. These can be bound and rebound on a per-thread basis.
* Booleans can have a value of true or false; nil values are also treated as false.
* Numbers can be integers, doubles, floats, and fractions.
* Symbols are used as identifiers for variables.
* Keywords are symbols that reference themselves and are denoted by a colon; these are often used as keys in maps.
* Strings are denoted by double quotes and can span multiple lines.
* Characters are denoted by a by preceding backslash.
* Regular expressions are strings prefixed with a hash symbol.

In addition to the data types, Clojure provides us with a literal notation for common collection types such as lists, vectors, maps, and sets:

* List: '(1 2 3)
* Vector: [1 2 3]
* Map: {:foo "a" :bar "b"}
* Set: #{"a" "b" "c"}

**(defn myfunc ...)** is shorthand for **(def myfunc (fn ...)))**

Nesting data structures works like you'd expect:

``` clojure
#{:a
  [1 2 3]
  {:foo 11 :bar 12}
  #{"shirt" "coat" "hat"}}
```

Boolean values are *true* and *false*; same stupid truthiness concept as JavaScript means only *nil* and *false* are falsey, and this means that zero, the empty string, and empty core data structures are all *true*:

``` clojure
(if   0 :t :f)  ; ⇒ :t
(if  "" :t :f)  ; ⇒ :t
(if  [] :t :f)  ; ⇒ :t
(if  {} :t :f)  ; ⇒ :t
(if #{} :t :f)  ; ⇒ :t
```
