## Problem: Longest Consecutive Sequence
**Pattern:** Hashmap/Set — "skip to the real starting points"
**Difficulty:** Medium
**Link:** https://leetcode.com/problems/longest-consecutive-sequence/

### Brute Force
Sort the array, then walk through once tracking a running streak count
(reset to 1 whenever the gap to the previous number isn't exactly 1).
Track the max streak seen. Requires a final comparison after the loop ends,
to catch a streak that runs all the way to the end of the array without
ever being "closed" by a break in the sequence.
Time: O(n log n) — dominated by the sort | Space: O(1) extra

### Approach (Optimized)
Sorting is only useful because it puts close-in-value numbers next to each
other — but a `Set` gives O(1) "does this value exist?" checks without
needing to sort at all.

The naive hashmap idea (start a forward-walk from *every* number) looks O(n)
per number, which would make the whole thing O(n²) in the worst case — e.g.
`[1,2,3,4,5]` would redundantly re-walk `2,3,4,5` after already walking it
from `1`.

**The real trick:** only start counting a streak from `num` if `num - 1` is
NOT in the set. That guarantees `num` is a genuine starting point — not the
middle of some earlier streak. With that filter, every number across the
whole array only ever gets visited once by exactly one streak's forward
walk, so the total work stays bounded by `n` (amortized O(n)), even though
the code looks like a nested loop (for-loop + while-loop).

### Complexity
Time: O(n) — amortized; every element is visited at most once across all
inner while-loop runs combined, even though it looks nested
Space: O(n) — the Set holding all elements

### Code
```javascript
function longestConsecutive(arr) {
  if (arr.length < 1) return 0;

  const set = new Set(arr);
  let maxStreak = 0;

  for (const num of set) {
    if (set.has(num - 1)) continue; // not a real starting point, skip

    let currentStreak = 1;
    let value = num;

    while (set.has(value + 1)) {
      value += 1;
      currentStreak += 1;
    }

    maxStreak = currentStreak > maxStreak ? currentStreak : maxStreak;
  }

  return maxStreak;
}
```

### Key gotchas
1. **Starting-point filter is the whole trick** — without `if (set.has(num - 1)) continue`, the solution silently degrades toward O(n²) by re-walking the same streak from multiple starting numbers.
2. **Iterate the Set, not the original array** — looping the raw array re-processes duplicates and gains nothing; the Set already de-duplicates.
3. **Brute force boundary bug** — the running-streak version needs one extra comparison *after* the loop ends, or the longest streak gets missed entirely when it happens to end at the last element of the sorted array.
4. **Empty array edge case** — return `0`, not a bare `return;` (which silently returns `undefined` in JS).