# DSA Pattern Study Reference Sheet

This reference sheet outlines the top coding patterns tested in 20 LPA SDE interviews, when to use them, and complexity bounds.

---

## 🚀 1. Core Coding Patterns

### A. Sliding Window
*   **Use Cases**: Linear structures (arrays, strings, linked lists) where you search for a contiguous subarray or substring matching a condition.
*   **Key Indicators**: "longest/shortest substring", "subarray size K", "minimum window".
*   **Time/Space Complexity**: $O(N)$ Time, $O(1)$ or $O(K)$ Space.

### B. Two Pointers
*   **Use Cases**: Sorted arrays or lists where pairs need to be compared without nested loops.
*   **Key Indicators**: "sorted array", "find pairs that sum to X", "trapping water", "container with most water".
*   **Time/Space Complexity**: $O(N)$ Time, $O(1)$ Space.

### C. Fast & Slow Pointers (Tortoise & Hare)
*   **Use Cases**: Cyclic structures in linked lists or arrays.
*   **Key Indicators**: "detect cycle", "find entry point of cycle", "find middle node of list".
*   **Time/Space Complexity**: $O(N)$ Time, $O(1)$ Space.

### D. Monotonic Stack
*   **Use Cases**: Linear search for the next/previous greater or smaller elements.
*   **Key Indicators**: "next greater element", "daily temperatures", "largest rectangle in histogram".
*   **Time/Space Complexity**: $O(N)$ Time, $O(N)$ Space.

### E. Two Heaps
*   **Use Cases**: Dynamically calculating the median or managing scheduling priority queues.
*   **Key Indicators**: "median of data stream", "find scheduling gaps".
*   **Time/Space Complexity**: $O(\log N)$ inserts, $O(1)$ peek, $O(N)$ Space.

---

## ⚡ 2. Time & Space Complexity Reference

| Data Structure / Algorithm | Operation | Average Complexity | Worst Case Complexity | Space Complexity |
| :--- | :--- | :--- | :--- | :--- |
| **Array** | Search | $O(N)$ | $O(N)$ | $O(1)$ |
| **Array** | Binary Search (Sorted) | $O(\log N)$ | $O(\log N)$ | $O(1)$ |
| **Linked List** | Insert / Delete | $O(1)$ | $O(1)$ | $O(1)$ |
| **HashMap / HashSet** | Get / Put | $O(1)$ | $O(N)$ (hash collision) | $O(N)$ |
| **Binary Search Tree** | Search / Insert | $O(\log N)$ | $O(N)$ (unbalanced) | $O(N)$ |
| **B+ Tree** | Search | $O(\log N)$ | $O(\log N)$ | $O(N)$ |
| **Trie** | Insert / Search | $O(L)$ (L = length) | $O(L)$ | $O(\text{Nodes})$ |
| **Merge Sort** | Sort | $O(N \log N)$ | $O(N \log N)$ | $O(N)$ |
| **Quick Sort** | Sort | $O(N \log N)$ | $O(N^2)$ (bad pivot) | $O(\log N)$ |

---

## 🧠 3. Decision Matrix: Graph Traversals

*   **Breadth-First Search (BFS)**: Use when searching for the **shortest path** or **minimum steps** in an unweighted graph (e.g., Word Ladder, network latency delay).
*   **Depth-First Search (DFS)**: Use when checking connectivity, finding cycles, traversing topological trees, or generating permutations (e.g., Number of Islands, N-Queens).
*   **Dijkstra's Algorithm**: Use for shortest path in graphs with **non-negative weights** (Priority Queue O((V+E) log V)).
*   **Bellman-Ford**: Use for shortest path when graphs contain **negative weights** ($O(V \cdot E)$).
