## Cheat Sheet - [SouJava Online] Let's make a contract: the art of designing a Java API - Mario Fusco

[video](https://www.youtube.com/watch?v=bfJZDetMKEc)

* Costs little to write it, a lot to mantain it.
* Keep minimal exposed front.
* Javadoc for: valid values, errors, exceptions, use common annotations.
* Use semantic naming, use typed args.
* Consistent naming.
* Consistent # arguments ,  use factories:
    - can return different subclasses, good to check preconditions.
    - can use a fluent e.g. stream API.
* Overload for primitives (necessary evil), but keep minimal.
* Use interfaces with broader usage the most, e.g. not ArrayList but Collection or Iterable:
    - List, does the order meaningful?
    - Are element distinct? Else use Set or Collection. Avoid useless copy of objects.
* Use lambda: @FunctionalIterface as arguments of your API, use std. Consumer Interfaces as much as possibile.
* Avoid checked Exceptions, (lambda forbid them).
* Loan pattern, avoid leak of resources:
    - version 1: use finally || try with resources J7+;
    - version 2: functional withFile(name , @FunctionalInterface apply consumer ).
* Break big interfaces into small interfaces, delegate to subinterfaces from the master interface:
    - e.g. group by topic.
* Be defensive on data, immutable problem of list returned:
    - return Collections.unmodifiableList();
    - this is does not cover for content of the collection, try use guava, use vavr.
* Prefer enum to boolean, opens to future multiple value and adds more semantic.
* Avoid string typing, give it a name Map<String, ...> 
* Avoid Primitive Obsession.
* Create Classes with Empty instances.
* Return optionals or empty collections. to avoid NullPointer.
* Warning Optional.of throws a NullPointerExc if value null:
    - wrong default, use ofNullable();
    - it help express intent of nullability of return, not the NOT NULL, it's a warning to consumer not a garantee;
    - using of with nullpointer help with a fast fail logic, if you use without check at least it breaks fast.
* Design API is all about tradeoffs and iterative discover.
* Design, minimal guidlines:
    - remove duplicates;
    - avoid leaks;
    - avoid unclear intentions;
    - favor broader usage;
    - use your API, with writing tests;
    - check for quality feedback.
