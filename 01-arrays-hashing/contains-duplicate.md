## Problem: Contains Duplicate
**Pattern:** Hashmap/Set — "have I seen what I need?"
**Difficulty:** Easy
**Link:** https://leetcode.com/problems/contains-duplicate/

### Brute Force
Nested loop — for each element, compare it against every other element
to check for a match.
Time: O(n²) | Space: O(1)

### Approach (Optimized)
Walk through the array once. For each value, check if it's already in a
Set before adding it. If it's already there, you've found a duplicate.
A Set is enough here (instead of a Map) because we only need to know
*whether* we've seen a value, not *where*.

### Why check-before-insert matters
Same reasoning as Two Sum — if you insert the current value first, the very
first element would immediately "find itself" in the set and incorrectly
report a duplicate on iteration one.

### Complexity
Time: O(n) — single pass, O(1) set operations
Space: O(n) — worst case (all distinct) stores every element

### Code
```javascript
function containsDuplicate(nums) {
  const seen = new Set();
  for (let i = 0; i < nums.length; i++) {
    if (seen.has(nums[i])) {
      return true;
    }
    seen.add(nums[i]);
  }
  return false;
}
```

### Key gotcha
Use a Set, not a Map — we only need existence, not index/position.
Map vs Set choice depends on what the problem asks you to return.