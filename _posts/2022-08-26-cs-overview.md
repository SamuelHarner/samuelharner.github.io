---
layout: post
title: "3 years of computer science"
subtitle: "a brief overview of some core concepts"
background: '/img/posts/cs-overview/motherboard.jpeg'
---
*(this post is a work in progess)*

# Introduction
This is a short overview of some of the core concepts underlying computer science and programming, based on my 3-year bachelor's degree in computer science. The most basic concepts of control flow in programming (such as if-statements and for-loops) will not be covered specifically, nor will related tangential topics such as human-computer interaction or areas of mathematics used in computer science (such as linear algebara and discrete mathematics). 

The following concepts will be covered:
- [Data structures](#data-structures)
- [Algorithms](#algorithms)
- [Complexity](#complexity)
- [Models of computation](#models-of-computation)
- [Programming paradigms](#programming-paradigms)
- [Computer architecture and components](#computer-architecture-and-components)
- [Operating systems](#operating-systems)
- [Software engineering](#software-engineering)

<br />

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

<br />

# Algorithms
**Recommended litterature:** Introduction to Algorithms, Thomas H. Cormen, Charles E. Leiserson, Ronald L. Rivest, and Clifford Stein

***

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

<br />

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

<br />

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

<br />

# Computer architecture and components
**Recommended litterature:** Computer Organization and Design: the Hardware/Software Interface, David A. Patterson and John L. Hennessy

Some of the following notes were derived from the course IS1500 at KTH Royal Institute of Technology

***

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

![Von Neumann architecture](/img/posts/cs-overview/Von_Neumann_Architecture.png)
<a href="https://commons.wikimedia.org/wiki/User:Kapooht">Kapooht</a>, <a href="https://commons.wikimedia.org/wiki/File:Von_Neumann_Architecture.svg">Von Neumann Architecture</a>, <a href="https://creativecommons.org/licenses/by-sa/3.0/legalcode" rel="license">CC BY-SA 3.0</a>

### Processor
A processor is typically divided into two parts:

**Data path**
- Operates on a word of data
- Consists of elements such as registers, memory, ALUs, etc.

**Control unit**
- Gets the current instruction from the data path and tells the data path how to execute the instruction

A processor is programmed by utilizing the processors [Instruction Set Architecture (ISA)](https://en.wikipedia.org/wiki/Instruction_set_architecture) to issue instructions for the processor to execute. The ISA is an abstract model of the processor and provides an interface between software and hardware through the set of instructions.

Microarchitecture is the implementation of the ISA, for example both Intel and AMD implement [x86 ISA](https://en.wikipedia.org/wiki/X86), but they have different implementations.

A program written in a [compiled programming language](https://en.wikipedia.org/wiki/Compiled_language) would be compiled to the assembly language of the processor which is then converted to the corresponding machine code (instructions coded in 0s and 1s) which the processor can run.

So writing a C program for an Intel processor may proceed as following:

<p style="text-align: center;">C program --> x86 assembly --> machine code</p>

### Memory
A processor has registers which it uses for storing data when carrying out instructions. The number of registers however is very limited and is therefore bolstered by computer storage called memory. Memory has many more data locations than registers but is also much slower to access than memory. The [memory hierarchy](https://en.wikipedia.org/wiki/Memory_hierarchy) of a computer is a setup of memory that tries to balance the properties of speed, capacity, and cost.

![Memory hierarchy](/img/posts/cs-overview/640px-ComputerMemoryHierarchy.png)

The primary memory in the form of [random-access memory (RAM)](https://en.wikipedia.org/wiki/Random-access_memory), which usually serves as a first layer of memory after the registers, is together with the registers a tempory storage location for working data while the computer is on. The secondary memory, often in the form of a hard drive, serves a permanent storage location for data.

A small cache memory is also used to store frequently used data close to the processor for faster access than from the other more longer term memory.

![Cache memory](/img/posts/cs-overview/cache.png)

When programming the processor it is desirable to utilize the cache as much as possible to decrease time spent on retriveing data from memory. As the cache is a very small memory it is important to think strategically about what data should be loaded in to the cache, two forms of memory access patterns that are therefor important to consider are:

**Temporal locality:**
The processor is likely to access recently accessed memory addresses again.

**Spatial locality:**
The processor is likely to access addresses close to each other.

When the cache is full it is also important to be strategic about what data is evicted to make room for new data. This is done by using a replacement policy, such as the [Least Recently Used (LRU)](https://en.wikipedia.org/wiki/Cache_replacement_policies#Least_recently_used_(LRU)) policy which evicts the data that has not been used for the longest time.

### Important trends
**[Moore's law](https://en.wikipedia.org/wiki/Moore%27s_law)**  
It has been observed, and treated as a goal, that the number of transistors on a microchip doubles every 2 years. The years during which this law has held has led to exponential increases in processig power, but it is predicted this trajactory will not hold for much longer.

![Moore's law](/img/posts/cs-overview/Moore's_Law_Transistor_Count_1970-2020.png)
Max Roser, Hannah Ritchie, <a href="https://commons.wikimedia.org/wiki/File:Moore's_Law_Transistor_Count_1970-2020.png">Moore's Law Transistor Count 1970-2020</a>, <a href="https://creativecommons.org/licenses/by/4.0/legalcode" rel="license">CC BY 4.0</a>

**Parallelism**  
Another important trend is the development of [multi-core](https://en.wikipedia.org/wiki/Multi-core_processor) computer systems and [parallel computing](https://en.wikipedia.org/wiki/Parallel_computing) models that can increase computer performance by utilising parallelism.

<br />

# Operating systems
**Recommended litterature:** Operating Systems: Three Easy Pieces, Remzi and Andrea Arpaci-Dusseau

Some of the following notes were derived from the course ID1200 at KTH Royal Institute of Technology

***

An [operating system (OS)](https://en.wikipedia.org/wiki/Operating_system) provides abstraction, virtualiszation, managing of resources, and serves as an interface between the applications running on a computer and the computer's hardware.

<p style="text-align: center;">applications <--> operating system (kernel) <--> hardware</p>

**Abstraction:**
create layers of abstraction to simplify interaction with/use of the OS.

**Virtualization:**
present one hardware resource as several virtual resources so that several programs can share a single hardware resource.

**Resource management:**
allocate and regulate use of limited resources.

![Kernel](/img/posts/cs-overview/kernel.png)
<a href="https://commons.wikimedia.org/wiki/User:Bobbo">Bobbo</a>, <a href="https://commons.wikimedia.org/wiki/File:Kernel_Layout.svg">Kernel Layout</a>, <a href="https://creativecommons.org/licenses/by-sa/3.0/legalcode" rel="license">CC BY-SA 3.0</a>

## Processes
Applications run processes. A process is:
- a program (i.e. a sequence of operations)
- a set of data structures
- a set of registers
- a means to interact with other processes or external entities

In C a process consists of:
- a program: a set of named procedures
- a call stack: provides the means to call and return from a procedure
- a heap where new data structres can be allocated
- a current program pointer
- open file descriptors, etc.

A model of a process can be seen in the diagram below, showing how memory is allocated to the code, static data, and the heap and stack as well as how they may be expanded:

![Process](/img/posts/cs-overview/process.png)

Contexts are also created by the OS to store certain necessary information about the processes, so that the OS can switch, without losing information, between different processes by switching and maintaining contexts.

It is important for the OS to maintain control over processes, so as to allocate execution time fairly and prevent processes from acting dangerously (eg. accessing areas of memory that they should not). A way of achieving this is limited direct execution. This mecahnism allows a user program to execute directly but with limitations, such as:
- it will not be able to execute all possible instructions
- it will only be able to access its own memory
- it will only be allowed to executed for a limited time (interrupts can switch contexts)

Hardware can also help by allowing an execution to be in either "user mode" for user programs or "kernel mode" for the OS.

## Memory management
Another assignment of the OS is to manage memory used by processes. Among other things, this involves memory virtualization to simplify how processes handle memory addresses. This allows processes to make assumptions about the virtual memory addresses it works, such as the address of where the memory starts, instead of rewuiring knowledge about the status of the real physical memory addresses.

The OS is also responsible fot keeping track of what memory is being used and what memory is free and can be allocated. The OS may also utilize different strategies for which blocks of memory should be allocated and how blocks of memory should be grouped together, so as to minimize memory fragmentation, which for example could result in many small blocks of memory to small to be useful.

Some important principles the OS tries to follow are:
- processes should be unaware of virtualization (they do not have to worry about the details)
- processes should not be able to interfere with each other
- execution should be as close to real execution as possible

## Concurrency
Another job of the OS is to manage and enable the execution of several things at the same time, or at least the illusion thereof, for example in the form of several programs running simultaneously. In such cases (which is most of the time), and in the case of processes running multiple concurrent threads of execution, the OS must have tools and systems in place for managing shared resources such that executions have the desired outcome. 

Without the right considerations however, concurrent threads accessing shared resources may overwrite each others work or, if the tools (such as [locks](https://en.wikipedia.org/wiki/Lock_(computer_science))) for enabling concurrency are used incorrectly, threads may become locked in place waiting for each other access the share resources.

## File system
A file system is the user space implementation of persistent storage.
- a file is persistent (it survives the termination of a process)
- a file can be accessed by several processes (i.e. a shared resource)
- a file can be located given a path name

To the user the file system basically consists of directories (folders) and files, while the behind scenes implementation may consist of a system of [nodes](https://en.wikipedia.org/wiki/Inode), that point to data blocks, and information about the status of the [nodes](https://en.wikipedia.org/wiki/Inode).

To make writing to files in the file system resilient to crashes, mechanism like [journalling](https://en.wikipedia.org/wiki/Journaling_file_system) may be used. Journalling basically entails logging the modifications intended to be made, such that if the modifications are interrupted the logs can be used to recover and finish or repeat the modifications.

<br />

# Software engineering

## Database systems
**Recommended litterature:** Database Systems: The Complete Book, Héctor García-Molina, Jeffrey Ullman, and Jennifer Widom

Some of the following notes were derived from the course DD1368 at KTH Royal Institute of Technology

***

**Data vs Information**  
Data is unprocessed information that can be converted into knowledge used to take actions.

<p style="text-align: center;">Data --> Information --> Knowledge --> Action</p>

**Database types**  
Databases provide a means to store data about entities and the relationships between entities, for example a database that has the entities people and cars and the relationships of which people the cars are registered to.

[Relational databases](https://en.wikipedia.org/wiki/Relational_database) sort data in a structured tabular format and are often queried using the language [SQL (Structured Query Language)](https://en.wikipedia.org/wiki/SQL) that implements the principles of [relational algebra](https://en.wikipedia.org/wiki/Relational_algebra). [Relational algebra](https://en.wikipedia.org/wiki/Relational_algebra) provides a theory for how data can be selected from tables using criteria as well as how tables of data can be combined to gather together data from different entities or relationships.

The entity-relationship model (E-R model) of a relational database can be modeled using a modelling notation, such as Chen notation used in the diagram below for an E-R model of an online role-playing game.

![E-R model](/img/posts/cs-overview/673px-ER_Diagram_MMORPG.png)

Another modelling framework that is popular for creating high level conceptual models of data or processes is [UML (Unified Modeling Language)](https://en.wikipedia.org/wiki/Unified_Modeling_Language).

[Non-relational databases](https://en.wikipedia.org/wiki/NoSQL) provide a document-oriented means for storing data in a format that is non-tabular and less strucutred than the [relational model](https://en.wikipedia.org/wiki/Relational_model). This format is suitable for [unstructured data](https://en.wikipedia.org/wiki/Unstructured_data) and [semi-structured data](https://en.wikipedia.org/wiki/Semi-structured_data).

**Database design**

When designing the model or [schema](https://en.wikipedia.org/wiki/Database_schema) of the database it is important to structure the database such that it minimizes the presence of redundant information that may lead to anomalies such as certain data being updated in one place but not another. This is done through a process of decomposition that ensures modularity of the groups of data that will be stored. Key values (such as unique IDs) and dependencies are then utilized to connect groups of data together, so that they for example can be updated together or joined for the sake of a query.

**Database modification**

When performing [database transactions](https://en.wikipedia.org/wiki/Database_transaction) (groups of operations performed together) it is important to guarantee that data validity will be preserved, for example by following the **[ACID](https://en.wikipedia.org/wiki/ACID)** properties:
- **Atomicity:** every operation in a transaction succeeds or the transaction fails and nothing is changed
- **Consistency:** transaction is subject to constraints of the database
- **Isolation:** transactions must be independent, i.e. resulting changes should be as if transactions were done sequentially
- **Durability:** effect of a transaction must not be lost once transaction has completed

## Workflow
As software development is often a very iterative process, agile workflows such as [SCRUM](https://en.wikipedia.org/wiki/Scrum_(software_development)) are popular ways of managing projects. SCRUM usually consists of short sprints of work to achieve goals that will vary between different sprints. This model intends to enable continous iteration and delivery of results and quick response to demands. SCRUM is also usually characterized by a shared visual workspace where tasks are catalogued as well as a SCRUM-master that helps to manage and delegate tasks within the development team.

## Version control
In order to store changes and versions of the software a [version control system (VCS)](https://en.wikipedia.org/wiki/Version_control) is used. The most popular VCS likely being Git combined with GitHub for online storage and access to Git code repositories. A VCS creates a history of all the changes being made to the codebase, so that changes can be rolled back or to enable separate branches of development from a shared starting point to more easily be combined later by mergin them onto the main branch of the codebase.

## Testing
[Software testing](https://en.wikipedia.org/wiki/Software_testing) is used to try to verify that th software produces the correct outcomes. Testing may be done through manual testing of applications, to try to generate and detect improper outcomes, or through automated tests, that may focus more on verifying the behaviour of indivdual functions or components used within the application.

The [test-driven development (TDD)](https://en.wikipedia.org/wiki/Test-driven_development) philosophy of software development advocates for tests to be written, that serve as a specification of necessary functionality, before the software is written. The TDD approach aims to ensure software correctness throughout the whole software development process, as opposed to writing tests at the end of the process when a large technical debt that involves systematic errors or bugs has already been incurred, thus risking more time and larger [code refactoring](https://en.wikipedia.org/wiki/Code_refactoring) efforts being necessary to achieve correctness. While an advantage of TDD may be argued that it focuses devlopment on necessary functionality, a disadvantage may be argued that it limits the speed of development and the process of quick iteration. A tradeoff may therefore exist between correctness and speed or flexibility of development.
