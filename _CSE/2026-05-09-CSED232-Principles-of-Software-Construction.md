---
title: "[CSED232] Principles of Software Construction"
date: 2026-05-09
tags:
  - POSTECH
excerpt: "Lecture note of CSED232 Principles of Software Construction."
---

## Lecture 8. Object Oriented Contracts

** 1.	Class Specification **

  Specification of each method:
    - Precondition   (@ requires)
    - Postcondition  (@ ensures)
  
  Stronger specification: Weaker Precondition & Stronger Postcondition

  Types of Operations:
    -	Observers (getters): Return information about the object without modifying it
    -	Mutators (setters): Modify the object’s state
    -	Producers: Create new objects without modifying the existing one

  Class Invariant (Representation Invariant): must be preserved by all operations
  

** 2.	Abstraction and Representation Exposure **

  Abstract objects: What the client observes
  Concrete objects: The internal representation
    = Mutating only the concrete objects is not observable by the client.
  
  Abstraction (function): surjective(onto) but not injective(one-to-one)

  Representation Exposure: Given direct access to the internal representation
    = Class invariants can be violated.
    
  Avoiding Representation Exposure:
    -) private: not enough (methods may return references to internal representation
    -) final (same as const in C++): still not enough (method calls can change internal representation)  
    
  Solution: Use immutable objects, return new objects = Safe sharing
    - Immutable containers: List.of(…), Set.of(…), Map.of(…), …
    - Immutable wrappers: Collections.unmodifiableList(…), Collections.unmodifiableSet(…), …
    - Records

  
** 3.	Records and Pattern Matching **

  Record: class for simple carriage of IMMUTABLE data
    ex) record Point(double x, double y) {}
    Compiler automatically generates:
      - constructors: to initialize the fields
      - public accessor: for each field
      - toString(), equals(), hashCode() methods
    
  Pattern Matching: checking/comparing multiple conditions of the data at once
    - PM for instanceof: if (obj instanceof Circle(Position(var x, var y), var r)) {…})
    - PM for switch: case Circle c when c.radius() > 10 -> ...);)
    Caveats in PM: switch must be exhaustive (via default or sealed interface)
    
  Example: Binary Tree
  sealed interface IntTree permits Leaf, Node {}
  record Leaf(int value) implements IntTree {}
  record Node(IntTree left, IntTree right) implements IntTree {}
  static int sum(IntTree tree) {
    return switch (tree) {
      case Leaf(int value) -> value;
      case Node(IntTree left, IntTree right -> sum(left) + sum(right);
    };
  }

  IntTree tree = new Node(new Leaf(1), new Node(new Leaf(2), new Leaf(3)));
  System.out.println("Sum: " + sum(tree));
  

4.	Equailty (not included??)

