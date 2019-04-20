---
layout: page
---

# [map](https://clojuredocs.org/clojure_core/clojure.core/map)

```
    (map f)
    (map f coll)
    (map f c1 c2)
    (map f c1 c2 c3)
    (map f c1 c2 c3 & colls)
```

Returns a lazy sequence consisting of the result of applying f to the set of first items of each coll, followed by applying f to the set of second items in each coll, until any one of the colls is exhausted. Any remaining items in other colls are ignored. Function f should accept number-of-colls arguments. Returns a transducer when no collection is provided.

# [filter](https://clojuredocs.org/clojure_core/clojure.core/filter)

```
    (filter pred)
    (filter pred coll)
```

Returns a lazy sequence of the items in coll for which (pred item) returns logical true. pred must be free of side-effects. Returns a transducer when no collection is provided.

# [assoc](https://clojuredocs.org/clojure.core/assoc):

```
    (assoc map key val)
    (assoc map key val & kvs)
```

When applied to a map, returns a new map of the same (hashed/sorted) type, that contains the mapping of key(s) to val(s). When applied to a vector, returns a new vector that contains val at index. Note - index must be <= (count vector).

# [reduce](https://clojuredocs.org/clojure_core/clojure.core/reduce)

```
    (reduce f coll)
    (reduce f val coll)
```

f should be a function of 2 arguments. If val is not supplied, returns the result of applying f to the first 2 items in coll, then applying f to that result and the 3rd item, etc. If coll contains no items, f must accept no arguments as well, and reduce returns the result of calling f with no arguments. If coll has only 1 item, it is returned and f is not called. If val is supplied, returns the result of applying f to val and the first item in coll, then applying f to that result and the 2nd item, etc. If coll contains no items, returns val and f is not called.

# [re-seq](https://clojuredocs.org/clojure_core/clojure.core/re-seq)

```
    (re-seq re s)
```

Returns a lazy sequence of successive matches of pattern in string, using java.util.regex.Matcher.find(), each such match processed with re-groups.
