# Data Structures and Algorithms (DSA)

## Algorithms

Algorithm is a step-by-step (or divided in simpler steps) approach to implement a desired source flow.

Various categories of algorithms exist:

1. Searching
2. Sorting
3. String Manipulation
4. Hashing
5. Tree Traversal
6. Graph Traversal

## Data Structures

Data structures is an implementation to store data effectively.

Data structures can be classified into Linear and Non-Linear Data Structures.

### Linear Data Structures

1. Array
    a. Nested Arrays
    b. String - Array of characters
2. List (variable-sized arrays)
3. Linked List
    a. Singly Linked List
    b. Doubly Linked List
4. Map
    a. Ordered Map - In C++, Ordered Map uses a self-balancing Red-Black Tree (RBT) for balancing tree height during intersion and deletion while keeping the search time close to O(log2(n)).
    b. Unordered Map - Unordered Map may use a Binary Search Tree (BST).

### Non-Linear Data Structures

Also known as Planar (for 2-D) or Multi-Dimensional Data Structures.

1. Matrix / Grid
2. Tree
    a. Binary Search Tree
    b. Self-Balancing Trees: AVL (Adelson-Velsky and Landis) Tree, Red-Black Tree
    c. B-Tree: A tree with a fixed maximum degree or order which determines the maximum number of child nodes for any parent node in the tree.
        i. B+ - Tree: A variant of B-Tree where all data items are stored in leaf nodes, making searches faster. It is commonly used in File Systems and Databases.
    d. Segment Tree (also called Statistical Tree)
3. Graph

Programmatically in C++ (v11 and later), when returning objects from within a function (local scope to enclosing scope), move semantics & return value optimization (RVO) helps with saving the overhead to copy the local items out of the function return value to the assigned container by optimizing the space to be retained for usage in the enclosing scope.

## References

1. [DSA Tutorial - W3 Schools](https://www.w3schools.com/dsa/index.php)
2. [Types of Binary Tree - GeeksForGeeks](https://www.geeksforgeeks.org/types-of-binary-tree/)
3. [List of data structures - Wikipedia](https://en.wikipedia.org/wiki/List_of_data_structures)

## Subject Topics (from [GATE 2026 CS](https://gate2026.iitg.ac.in/doc/GATE2026_Syllabus/CS_2026_Syllabus.pdf) syllabus)

- Algorithms: Searching, sorting, hashing. Asymptotic worst case time and space complexity. Algorithm design techniques: greedy, dynamic programming and divide‐and‐conquer. Graph traversals, minimum spanning trees, shortest paths.
- Programming and Data Structures: Programming in C. Recursion. Arrays, stacks, queues, linked lists, trees, binary search trees, binary heaps, graphs.