# DSA Prep — Pattern-Based Problem Solving

Structured DSA practice with a focus on **pattern recognition** over
memorization. Problems are grouped by pattern (e.g. all hashmap problems
together) rather than following Striver's A2Z sheet in its literal
sequence — this is a deliberate choice to build one mental model deeply
before moving to the next, rather than interleaving patterns. Each solution
includes brute force → optimized progression, complexity analysis, and
gotchas — not just code.

## Progress

| # | Problem | Pattern | Difficulty | Link |
|---|---------|---------|------------|------|
| 1 | Two Sum | Hashmap — "have I seen what I need?" | Easy | [solution](./01-arrays-hashing/two-sum.md) |
| 2 | Contains Duplicate | Hashmap/Set — existence check | Easy | [solution](./01-arrays-hashing/contains-duplicate.md) |
| 3 | Group Anagrams | Hashmap — signature as key | Medium | [solution](./01-arrays-hashing/group-anagrams.md) |
| 4 | Longest Consecutive Sequence | Hashmap/Set — skip to real starting points | Medium | [solution](./01-arrays-hashing/longest-consecutive-sequence.md) |

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

- **"Have I seen what I need?" (Hashmap/Set)** — Two Sum, Contains Duplicate, Group Anagrams, Longest Consecutive Sequence
  - Trade O(n) space for a reduction from O(n²) (or O(n log n)) down to O(n) time
  - Check-before-insert matters when self-matching is a bug (Two Sum, Contains Duplicate); not needed when matching a *different* prior element is the actual goal (Group Anagrams)
  - Sometimes the trick isn't existence-checking alone, but filtering *which* elements should even start a computation (Longest Consecutive Sequence's "is `num - 1` missing?" check) — this avoids redundant work and keeps the algorithm truly O(n) despite looking like nested loops (amortized analysis)