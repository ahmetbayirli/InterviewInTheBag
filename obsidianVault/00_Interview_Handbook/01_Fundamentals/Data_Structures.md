---
id: top_107
title: Data Structures
tags:
  - fundamentals
  - data-structures
  - interview-essential
---

# Data Structures

A data structure is a specialized format for organizing, processing, retrieving, and storing data. Choosing the right data structure is the difference between an algorithm that scales ($O(n)$ or $O(\log n)$) and one that crashes the system ($O(n^2)$).

---

## Arrays & Static Arrays
Arrays are the most fundamental data structure, storing elements in contiguous memory locations. Because the memory is adjacent, you can access any element in $O(1)$ time if you know the index, thanks to simple memory address math.

However, static arrays have a fixed size. Inserting or deleting an element (especially at the beginning) is expensive ($O(n)$) because every subsequent element must be shifted in memory. They are best used when the data size is known and random access is frequent.



---

## Linked Lists (Singly & Doubly)
A Linked List consists of nodes where each node contains data and a pointer (reference) to the next node. Unlike arrays, they do not require contiguous memory; nodes can be scattered anywhere, making them very flexible for dynamic memory allocation.

The trade-off is that they do not support random access; to find the $i$-th element, you must traverse from the head ($O(n)$). However, if you already have a reference to a node, insertion and deletion are a constant $O(1)$ operation. Doubly Linked Lists add a "previous" pointer, allowing two-way traversal at the cost of extra memory.



---

## Hash Tables (HashMap / HashSet)
Hash Tables store key-value pairs and use a **Hash Function** to compute an index into an array of buckets. In an ideal scenario, they provide $O(1)$ time complexity for search, insertion, and deletion, making them the "gold standard" for performance in many applications.

The challenge with Hash Tables is handling **Collisions** (when two keys hash to the same index). Common solutions include **Chaining** (using a linked list at each bucket) or **Open Addressing**. As a senior, you must remember that if the hash function is poor, the complexity can degrade to $O(n)$.

---

## Stacks & Queues
These are "Linear" data structures with strict access rules. A **Stack** follows **LIFO** (Last-In, First-Out), much like a stack of plates. It is essential for managing function calls (the "Call Stack") and undo mechanisms.

A **Queue** follows **FIFO** (First-In, First-Out), like a line at a bank. It is the backbone of asynchronous messaging systems and "Breadth-First Search" (BFS) algorithms. Both structures offer $O(1)$ for their primary operations: push/pop for stacks and enqueue/dequeue for queues.



---

## Binary Trees & Binary Search Trees (BST)
A tree is a hierarchical structure. A **Binary Tree** limits each node to two children. A **Binary Search Tree (BST)** adds a rule: the left child is smaller than the parent, and the right child is larger. This allows for searching in $O(\log n)$ time.

However, a standard BST can become "unbalanced" (turning into a linked list) if data is inserted in order. Senior engineers look toward self-balancing trees like **AVL Trees** or **Red-Black Trees** (used in Java’s `TreeMap`) to guarantee logarithmic performance regardless of input order.



---

## Heaps (Priority Queues)
A Heap is a specialized tree-based structure that satisfies the "Heap Property." In a **Min-Heap**, the parent is always smaller than its children, ensuring the smallest element is always at the root.

Heaps are most commonly used to implement **Priority Queues** and in the **HeapSort** algorithm. Accessing the min/max element is $O(1)$, while inserting or deleting (re-balancing) takes $O(\log n)$.

---

## Graphs
Graphs consist of nodes (Vertices) connected by Edges. They are the most complex and versatile structure, used to model social networks, maps, and dependency graphs. They can be **Directed**, **Undirected**, **Weighted**, or **Unweighted**.

Graphs are typically represented in code using an **Adjacency List** (memory efficient) or an **Adjacency Matrix** (faster for checking if an edge exists). Algorithms like Dijkstra’s or $A^*$ are used to find the shortest path between nodes.



---

## Tries (Prefix Trees)
A Trie is a digital tree used for storing strings. Each node represents a character of a word. It is incredibly efficient for "prefix" queries, such as auto-complete features or spell checkers.

While they consume more memory than a Hash Set, they allow you to find all words starting with a specific prefix in $O(k)$ time, where $k$ is the length of the prefix, regardless of how many millions of words are in the dictionary.

---

# Interview Questions

1. What is the difference between a `List` and an `Array` in terms of memory?
	   Arrays use a single contiguous block of memory, allowing for $O(1)$ random access. Lists (like `LinkedList`) use nodes scattered in memory connected by pointers, requiring $O(n)$ time to access an element by index but allowing for easier resizing.
2. How does a HashMap handle collisions?
	   Most modern implementations use **Chaining**. When two keys hash to the same index, they are stored in a linked list at that bucket. In Java 8+, if a bucket becomes too crowded, the linked list is converted into a **Balanced Tree** to improve search time from $O(n)$ to $O(\log n)$.
3. When would you use a Doubly Linked List over a Singly Linked List?
	   Use a Doubly Linked List when you need to traverse the list in both directions or when you need to delete a node given only a reference to that node (since you need the 'previous' pointer to bypass it).
4. What is the time complexity of searching in a balanced Binary Search Tree?
	   The time complexity is $O(\log n)$ because each comparison allows you to skip half of the remaining tree.
5. What is the difference between a Stack and a Queue?
	   A Stack is LIFO (Last-In, First-Out), used for backtracking and recursion. A Queue is FIFO (First-In, First-Out), used for task scheduling and processing data in the order it arrived.
6. Why is an Adjacency List usually preferred over an Adjacency Matrix for Graphs?
	   Most real-world graphs are **sparse** (few edges). An Adjacency List only stores the existing edges ($O(V+E)$), whereas an Adjacency Matrix always uses $O(V^2)$ space, most of which would be zeros in a sparse graph.
7. What is a "Self-Balancing" Tree?
	   It is a tree (like AVL or Red-Black) that automatically rearranges its structure during insertion and deletion to keep its height minimal. This ensures that operations remain $O(\log n)$ and prevents the tree from degrading into a $O(n)$ linked list.
8. How do you detect a cycle in a Linked List?
	   The most common method is **Floyd’s Cycle-Finding Algorithm** (the "Tortoise and the Hare"). You use two pointers: one moving one step at a time and another moving two steps. If they ever meet, a cycle exists.
9. What is the Big O complexity of inserting an element into a Min-Heap?
	   Insertion is $O(\log n)$. The element is added to the bottom and "bubbled up" (heaped up) to its correct position to maintain the heap property.
10. In what scenario would a Trie be better than a HashMap?
    A Trie is better when you need to perform **prefix searches** (e.g., "find all words starting with 'app'"). A HashMap can only tell you if the exact key "app" exists; it cannot efficiently find related prefixes.

---

> [!TIP]
> **Senior Insight:** In high-performance systems, **Cache Locality** matters. Arrays are often faster than Linked Lists even for some insertions because the CPU can pre-fetch contiguous memory into its cache. Pointers in a Linked List cause "cache misses" because the CPU has to jump around in memory.

> [!TIP]
> Think of **Big O notation** not as a stopwatch, but as a **growth curve**. It describes the _upper bound_ of an algorithm's execution time or space requirements as the input size ($n$) grows.
> **The Common Hierarchy (from fastest to slowest):**
> 	1. **$O(1)$ - Constant:** Time stays the same regardless of $n$ (e.g., accessing an array index).    
>	2. **$O(\log n)$ - Logarithmic:** Time increases slightly as $n$ doubles (e.g., Binary Search).    
>	3. **$O(n)$ - Linear:** Time grows 1:1 with $n$ (e.g., a simple `for` loop).    
>	4. **$O(n \log n)$ - Linearithmic:** The standard for efficient sorting (e.g., Merge Sort, Quick Sort).    
>	5. **$O(n^2)$ - Quadratic:** Time grows exponentially (e.g., Nested loops). **Avoid these for large datasets.**    
> **Senior Insight:** In interviews, always mention **Space Complexity** alongside Time Complexity. A fast algorithm that consumes $O(n)$ extra memory might be less desirable in a memory-constrained environment (like your IoT tennis racket project) than a slightly slower one that runs in $O(1)$ space.

---