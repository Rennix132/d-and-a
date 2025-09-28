# d-and-a
# Assignment 1 Report

1. Architecture
MergeSort: For small arrays it switches to insertion sort. A single auxiliary buffer is reused to avoid many memory allocations.  
QuickSort: Uses a randomized pivot and always recurses into the smaller part, while the larger part is processed iteratively. This keeps the recursion depth about `O(log n)`.
Deterministic Select: Uses the median-of-medians method. Recursion continues only into the needed side of the array, which keeps the depth small.  
Closest Pair of Points: The array is sorted once by `x`. The algorithm splits recursively, and in the strip check each point is compared with at most 7–8 neighbors by `y`.  

2. Recurrence Analysis
MergeSort  
  `T(n) = 2T(n/2) + O(n)`  
  Master Theorem (Case 2) → `Θ(n log n)`  

QuickSort (randomized)  
  Average: `T(n) = T(k) + T(n-k-1) + O(n)`  
  Expected complexity: `Θ(n log n)`  
  Worst case: `Θ(n^2)` (rare with random pivot).  

Deterministic Select (Median-of-Medians)  
  `T(n) ≤ T(n/5) + T(7n/10) + O(n)`  
  Solved with Akra–Bazzi → `Θ(n)`  

Closest Pair  
  `T(n) = 2T(n/2) + O(n)`  
  Master Theorem (Case 2) → `Θ(n log n)`  

3. Experimental Results (described)
Sorting algorithms grew about `n log n` in runtime.  
Recursion depth was about `log n` for MergeSort and Closest Pair.  
QuickSort also had depth `≈ log n` in practice due to smaller-first recursion.  
Select had very small depth since it only recurses into one side.  

Constant factors:  
MergeSort is faster on small arrays due to insertion sort cutoff.  
QuickSort is usually faster than MergeSort but has variance.  
Deterministic Select has higher overhead than random pivot selection.  
Closest Pair has an initial sorting cost but then efficient scanning.  

4. Summary
Theory matched practice: MergeSort and Closest Pair ran in `O(n log n)`, QuickSort in `O(n log n)` on average, Select in `O(n)`.  
Differences came from constant factors such as caching, array copies, and cutoff thresholds.  
QuickSort and MergeSort are both good for large sorting tasks, while Select is useful for finding order statistics.  
