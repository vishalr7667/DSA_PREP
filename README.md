# DSA Prep — Pattern-Based Problem Solving

Structured DSA practice following [Striver's A2Z](https://takeuforward.org/dsa/strivers-a2z-sheet-learn-dsa-a-to-z) topic ordering, with a focus on **pattern recognition** over memorization. Each solution includes the core insight, complexity analysis, and gotchas — not just code.

## Progress

| # | Problem | Pattern | Difficulty | Link |
|---|---------|---------|------------|------|
| 1 | Two Sum | Hashmap — "have I seen what I need?" | Easy | [solution](./01-arrays-hashing/two-sum.md) |
| 2 | Contains Duplicate | Hashmap/Set — existence check | Easy | [solution](./01-arrays-hashing/contains-duplicate.md) |
| 3 | Group Anagrams | Hashmap — signature as key | Medium | [solution](./01-arrays-hashing/group-anagrams.md) |

## Topics

- [x] Arrays & Hashing *(in progress)*
- [ ] Two Pointers / Sliding Window
- [ ] Binary Search
- [ ] Stacks & Queues
- [ ] Linked Lists
- [ ] Trees & BSTs
- [ ] Graphs (BFS/DFS)
- [ ] Recursion & Backtracking
- [ ] Dynamic Programming
- [ ] Heaps & Greedy

## Pattern Index

Patterns that have shown up so far, and where:

- **"Have I seen what I need?" (Hashmap/Set)** — Two Sum, Contains Duplicate, Group Anagrams
  - Trade O(n) space for a reduction from O(n²) to O(n) time
  - Check-before-insert matters when self-matching is a bug (Two Sum, Contains Duplicate); not needed when matching a *different* prior element is the actual goal (Group Anagrams)