## Problem: Two Sum
**Pattern:** Hashmap — "have I seen what I need?"
**Difficulty:** Easy
**Link:** https://leetcode.com/problems/two-sum/

### Brute Force
Nested loop — for each element, scan the rest of the array for its
complement (`target - nums[i]`).
Time: O(n²) | Space: O(1)

### Approach (Optimized)
For each number, compute the complement (`target - nums[i]`). Check if that
complement already exists in a map before inserting the current number.
If found, you've got your pair. This trades extra space for a single pass
instead of nested loops.

### Why check-before-insert matters
If you insert the current number into the map *before* checking, an element
can match against itself (e.g. `nums = [3, 3]`, target = 6 — index 0 would
incorrectly "find" itself). Always check first, then insert.

### Complexity
Time: O(n) — single pass, O(1) map operations
Space: O(n) — worst case every element gets stored before a match is found

### Code
```javascript
function twoSum(nums, target) {
  const map = new Map();
  for (let i = 0; i < nums.length; i++) {
    const complement = target - nums[i];
    if (map.has(complement)) {
      return [map.get(complement), i];
    }
    map.set(nums[i], i);
  }
  return [];
}
```

### Key gotcha
Check before insert — prevents an element from pairing with itself.