---
layout: post
title: "3 years of Computer Science"
subtitle: "a brief summary of core concepts"
background: '/img/posts/life-is-a-game/earth-at-night.jpg'
---

# Introduction
This is a short summary of the core concepts underlying computer science and programming, based on my 3-year bachelor's degree in computer science. The most basic concepts of control flow in programming (such as if-statements and for-loops) will not be covered specifically, nor will related tangential topics such as human-computer interaction or areas of mathematics used in computer science (such as linear algebara and discrete mathematics).

The following concepts will be covered:
- [Data structures](#data-structures)
- [Algorithms](#algorithms)
- [Complexity](#complexity)
- [Models of computation](#models-of-computation)
- [Programming paradigms](#programming-paradigms)
- [Computer architecture and components](#computer-architecture-and-components)
- [Operating systems](#operating-systems)
- [Software engineering](#software-engineering)


# Data structures
*How to store data effectively?*

Data structures are different methods for connecting data into a collection of data. Depending on how the data is connected, the collection will vary in the properties of how data can be accessed or how the collection can be altered. For example, some data collections may allow a specific data element to be accessed directly, whereas other collections will require a searching process to find the requested element. 

Which data structure is most appropriate to use will vary based on the task. For certain tasks quick access of elements may be important, whereas for other tasks it may be more important to be able to quickly add elements to the collection. In general there is no data structure that performs the best on all imaginable properties of a structure. Therefore, there are often design choices and tradeoffs to be made when choosing a data structure. 

These are some of the most fundamental data structures:
- [Array](#array)
- [Stack](#stack)
- [Linked list](#linked-list)
- [Queue](#queue)
- [Hash table](#hash-table)
- [Binary tree](#binary-tree)
- [Graph](#graph)

## Array
An array is an indexed list with its elements laying sequentially in memory. Most programming languages start indexing at 0, so to access the first element of an array the element at index 0 should be accessed. In a programming language creating an array of integer numbers and accessing elements may look something like this:

```java
// array that can store 5 integers
int[] arr = new int[5];

// access first element
int first = arr[0];

// access last element
int last = arr[4];
```

Arrays provide quick access to elements, but adding more elements than the original array can fit requires creating a new bigger array and copying over the elements from the original array.

## Stack
A stack can be thought of as a vertical stack of elements, where elements can only be added to or removed from the top of the stack (these operations are usually called `push` and `pop`). A stack therefore follows the policy of Last In, First Out (LIFO).

For example if we have the following stack of numbers:

```
9  
4  
12
```

and we call `myStack.pop()` on the stack, we will then receive the element `9` and the stack will now be:

```
4  
12
```

if we now add an element with `myStack.push(7)` we get:

```
7
4  
12
```

A stack can be a handy structure for storing information temporarily before it has to be retrieved again.

## Linked list
A linked list is a list where each entry in the list contains an element and a link to the next entry. For example consider the following representation of a linked list:

```
(start) elem1 -> elem2 -> elem3 -> NULL (end)
```

In this linked list `elem1` is the first element and it points to the next element `elem2`. The last element is `elem3` and this is indicated by its pointer only pointing out a NULL (nothing) element.

Elements can easily be added to or removed from the start and end of the linked list by changing the links associated with the first or last element, but accessing or removing other elements requires stepping through the list until the correct element has been reached.

## Queue
A queue is a list that only allows elements to be added to the back of the queue and only removing elements form the front of the queue (these operations are usually called `enqueue` and `dequeue`). A queue follows the policy of First In, First Out (FIFO), as the element in the queue that was enqueued first is next to be dequeued. Consider the following queue:

```
(back) charlie -> bob -> alice (front)
```

where `enqueue("dennis")` would add dennis to the back of the queue, and `dequeue()` would retrieve alice from the front of the queue.

A queue can be though of as a linked list with the restriction that elements can only be added to the start of the list and elements can only be removed from the end.

## Hash table
Hash tables store key-value pairs. The key is used as input to a hash function to decide at which index in the hash table the key-value pair should be stored. Ideally each key-value pair would be stored at a unique index, but collisions can occur and be acommadated by having a list at each index.

Hash tables allow values to be found and accessed quickly with the help of the key, but entries may not be sorted in a logical manner (eg. numbers in ascending order) like they can be in a list.

## Binary tree
A binary tree starts with a single root node and every node in the tree can have two child nodes, one left child node and one right child node. The following is a representation of an example binary tree:

```
    5
   / \
  7   3
 / \   \
4   8   9
```

The binary tree above is not sorted, but we could the sort the numbers such that the left sub-tree is always smaller than the parent and the right sub-tree is always bigger than the parent, in order to create a sorted binary tree as shown below:

```
    5
   / \
  4   8
 /   / \
3   7   9
```

## Graph
A graph is a collection of nodes. The nodes can be connected together by edges. Different types of graphs can have edges with certain types of properties, for example:
- directed graph (edges have directions which limits how they can be traversed)
- undirected graphs (edges can be traversed in both directions)
- weighted graphs (edges have weights that can represent the cost or distance for traversing an edge)

# Algorithms
*How to solve problems effectively?*

Algorithms are a sequence of steps for performing a task or solving a problem. Some common types of algorithms are sorting algorithms and searching algorithms.

The amount of time or steps that an algorithm takes, known as its time complexity, is usually denoted in [Big-O notation](https://en.wikipedia.org/wiki/Big_O_notation), which describes an upper bound for the [time complexity](https://en.wikipedia.org/wiki/Time_complexity) of the algorithm. Some common time complexities are listed below, where the variable n is the size of the input to the algorithm:

- O(1), constant time, note that O(k) simplifies to O(1) for any constant k
- O(n), linear time
- O(log(n)), logarithmic time
- O(n*log(n)), linearithmic time
- O(n^k), polynomial time, where k is a constant
- O(k^n), exponential time, where k is a constant

A similar corresponding analysis can be done for the [space complexity](https://en.wikipedia.org/wiki/Space_complexity#:~:text=The%20space%20complexity%20of%20an,algorithm%20until%20it%20executes%20completely.) of an algorithm complexity to analyse the possible memory usage of an algorithm.

There are different approaches to designing an algorithm for solving a problem. A naive approach usually involves an **[Exhaustive Search](https://en.wikipedia.org/wiki/Brute-force_search)**, where all combinations are tested if necessary to find the solution. Another approach called a **[Greedy Algorithm](https://en.wikipedia.org/wiki/Greedy_algorithm)** uses a heuristic to find a solution that works but may not be optimal. A more sophisticated approach may utilize a **[Divide-and-Conquer](https://en.wikipedia.org/wiki/Divide-and-conquer_algorithm)** strategy, which seeks to split a problem into sub-problems, of the same type as the original problem, such that the sub-problems can be solved and the solutions thereto combined to solve the original problem. Another sophisticated approach called **[Dynamic Programming](https://en.wikipedia.org/wiki/Dynamic_programming)** seeks to define sub-problems that can be solved using a [recursive](https://en.wikipedia.org/wiki/Recursion_(computer_science)) process in a strategic order, such that the solutions to certain sub-problems can be stored ([memoization](https://en.wikipedia.org/wiki/Memoization)) and used to more quickly solve other sub-problems.

# Complexity
*How difficult is the problem to solve?*

The most common type of problems analysed in computer science are decision problems, which are problems that have a yes or no answer. Some other types of problems are optimazation problems, that are answered with an optimal value, and construction problems, that are answered with a constructed object.

Complexity classes have been defined for classifying decision problems into different difficulty categories. Some important such classes are the following:
- P: problems that can be solved in polynomial time
- NP: problems whose solutions can be verified in polynomial time
- NP-hard: problems for which all NP problems can be [karp-reduced](https://en.wikipedia.org/wiki/Polynomial-time_reduction) to the problems
- NP-complete: problems that are in NP and are NP-hard

A reduction is an algorithm for transforming one problem into another problem. This means that if problem A can be reduced to problem B, then an algorithm which solves problem B can be used to solve problem A.

# Models of computation
A model of computation is a model which describes how an output is computed given an input. More details about two of the most important models of computation are listed below.

## Turing machine
A [Turing machine](https://en.wikipedia.org/wiki/Turing_machine) is a state based universal model of computation that defines an abstract machine that manipulates symbols on a strip according to a table of rules. A Turing machine consists of:
1. Memory pointer (to symbol on strip) and a current state
2. Infinite strip with combination of 4 symbols (>, #, 1, 0)
3. Finite set of states the machine can be in

## Lambda calculus
[Lambda calculus](https://en.wikipedia.org/wiki/Lambda_calculus) is a functional universal model of computation that consists of 3 rules:
1. x, **variable**
2. ($\lambda$ x. M), **abstraction** (anonymous function that takes x and returns M)
3. (M N), **application** (apply function M to an input N)

# Programming paradigms
## Imperative
[Imperative programming](https://en.wikipedia.org/wiki/Imperative_programming) involves describing step-by-step how something should be computed and consists of:
1. Sequences
2. Control flow
3. Sub-routines
4. States

Example: [assembly language](https://en.wikipedia.org/wiki/Assembly_language)

## Object-oriented
[Object-oriented](https://en.wikipedia.org/wiki/Object-oriented_programming) programs contain different objects that interact with each other. Some important features are:
- Encapsulation
- Classes
- Inheritance

Examples: Java, Python

## Declarative
[Declarative programming](https://en.wikipedia.org/wiki/Declarative_programming) involves describing what should be computed, not how, which minimizes or eliminates side effects that modfiy states in the program.

Examples: functional and logical paradigms

### Functional
Some characteristics of [functional programming](https://en.wikipedia.org/wiki/Functional_programming) are:
- Immutability (state cannot be modified)
- Pure functions (always return same output given same input, no side effects)
- First class functions (functions can be passed as input to other functions)

Examples: Haskell, Erlang, Lisp

### Logical
[Logic programming](https://en.wikipedia.org/wiki/Logic_programming) is based on formal logic and involves specifying the conditions for a solution and then letting the logic programming language compute a solution.

Example: Prolog

## Parallel programming
[Parallel programming](https://en.wikipedia.org/wiki/Parallel_computing) seeks to utilize concurrency (handling many processes or threads at the same time) and parallelism (executing many processes or threads at the same time).

A parallel programming model can more efficiently perform tasks and utilize computing resources by distributing computations and running them in parallel on the available resources.

Examples: Golang, [multithreading](https://en.wikipedia.org/wiki/Multithreading_(computer_architecture)) in general

# Computer architecture and components
## Abstractions
Computer systems are built up of several layers of abstractions. If we start at the highest level of abstraction and work our way down, we could construct the following hierarchy of abstractions:

- Networked systems and systems of systems
    - Computer system
- Software
    - Application software
    - Operating system
- Hardware/Software interface
    - Instruction set architecture (ISA)
- Digital hardware design
    - Microarchitecture
    - Logic and building blocks
    - Digital circuits
- Analog design and physics
    - Analog circuits
    - Devices and physics

## Architecture
A simplified model of modern computer architecture is the [Von Neumann architecture](https://en.wikipedia.org/wiki/Von_Neumann_architecture):

![Von Neumann architecture](/img/posts/cs-summary/Von_Neumann_Architecture.png)

### Processor
A processor is typically divided into two parts:

**Data path**
- Operates on a word of data
- Consists of elements such as registers, memory, ALUs, etc.

**Control unit**
- Gets the current instruction from the data path and tells the data path how to execute the instruction

Programming a processor...

### Memory

<a href="https://commons.wikimedia.org/wiki/User:Kapooht">Kapooht</a>, <a href="https://commons.wikimedia.org/wiki/File:Von_Neumann_Architecture.svg">Von Neumann Architecture</a>, <a href="https://creativecommons.org/licenses/by-sa/3.0/legalcode" rel="license">CC BY-SA 3.0</a>



# Operating systems

# Software engineering

## Database technology

## Workflow

### Version control

### Testing

