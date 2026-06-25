## Problem: Group Anagrams
**Pattern:** Hashmap — "build a signature, group by signature"
**Difficulty:** Medium
**Link:** https://leetcode.com/problems/group-anagrams/

### Brute Force
For every pair of words, build a character-count map for each and compare
them for equality to check if they're anagrams; group matches together.
Let `n` = number of words, `k` = average word length.
Time: O(n² · k) — O(n²) pairs, O(k) to compare counts per pair | Space: O(1) extra

### Approach (Optimized)
Two words are anagrams if and only if they have identical character counts.
Sorting a word's letters produces a "signature" that is identical for every
anagram of that word (e.g. "eat", "tea", "ate" all sort to "aet"). Use that
sorted string as a map key, and group original words under it.

### Why check-before-insert is NOT a concern here (unlike Two Sum)
In Two Sum, the danger was an element matching *itself*. Here, when a word
finds its key already in the map, it's always finding a *different*,
earlier word — never itself. Grouping different words under a shared key
is the entire goal, not a bug. So append-or-create can be done safely in
either order.

### Complexity
Time: O(n · k log k) — sorting each word costs O(k log k), done once per word
Space: O(n · k) — storing all words and their signatures

### Code
```javascript
function groupAnagrams(strs) {
  const map = new Map();
  for (const word of strs) {
    const key = word.split('').sort().join('');
    if (map.has(key)) {
      map.get(key).push(word);
    } else {
      map.set(key, [word]);
    }
  }
  return Array.from(map.values());
}
```

### Key gotcha
The hard part isn't the hashmap pattern itself — it's figuring out *what to
use as the key* so that related items collapse to the same value. Sorting
is one way to build a signature; character-count arrays are another
(faster, O(k) instead of O(k log k), useful if asked to optimize further).