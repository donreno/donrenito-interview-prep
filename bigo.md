# Big O 
Big O notes and cheat sheet

## Big O complexity order

```
  O(n!) > O(2^n) > O(n^2) > O(n*log n) > O(n) > O(log n)
```

## Famous algorithms time or time and space complexity
 - Heap Sort: time `O(n*log n)`
 - Buble Sort: time `O(n^2)`
 - Merge Sort: time `O(n*log n)` (average)
 - Quick Sort: time `O(n*log n)` (average picking a good pivot)
 - Retriving an element on a Hashtable `O(1)` (If there are zero or minimal collisions)

## Considerations when using hashtables in algorithms
If you are using a hashtable on your algorithms to make them "faster" remember that there is a trade of for space, so normally you will be adding O(n) space complexity when using it.
