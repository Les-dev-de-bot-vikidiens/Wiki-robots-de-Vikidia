# Merge sort - Wikipedia

![An example of merge sort. First, divide the list into the smallest unit (1 element), then compare each element with the adjacent list to sort and merge the two adjacent lists. Finally, all the elements are sorted and merged.](https://upload.wikimedia.org/wikipedia/commons/thumb/c/cc/Merge-sort-example-300px.gif/250px-Merge-sort-example-300px.gif)

* Class: [Sorting algorithm](/broken/pages/4a9224b98acad6cf54e65573e278bc48fadb9161)
* Data structure: [Array](/broken/pages/1e71ce0b6b7b8801b7dd8202fc0e33f554ad8188)
* Worst-case performance: O(n log n)
* Best-case performance: Ω(n log n) typical, Ω(n) natural variant
* Average performance: Θ(n log n)
* Worst-case space complexity: O(n) total with O(n) auxiliary, O(1) auxiliary with linked lists [\[1\]](merge-sort-wikipedia.md#cite_note-1)

In [computer science](/broken/pages/5248336dedd7b7a032621eb6ebcca48cf5ef38fc), merge sort (also commonly spelled mergesort or merge-sort [\[2\]](merge-sort-wikipedia.md#cite_note-goodrich12-2)) is an efficient, general-purpose [comparison-based](/broken/pages/ca60586cf7f1d7be12cd5119f13fe19697c549c8) sorting algorithm. Most implementations are [stable](/broken/pages/4a9224b98acad6cf54e65573e278bc48fadb9161#Stability). Merge sort is a [divide-and-conquer](/broken/pages/2bf738ee3c41c2992affb780e33550eed085af75) algorithm invented by [John von Neumann](/broken/pages/99348c528ca565e6e2a56bd5947487a072b96823) in 1945.[\[3\]](merge-sort-wikipedia.md#cite_note-3)

## Algorithm

Conceptually, a merge sort works as follows:

{% stepper %}
{% step %}
### Divide into single-element sublists

Divide the unsorted list into n sub-lists, each containing one element (a list of one element is considered sorted).
{% endstep %}

{% step %}
### Repeatedly merge

Repeatedly [merge](/broken/pages/1b7bc5dae2436fb743f4ee1fc2607a11fc9815a4) sublists to produce new sorted sublists until there is only one sublist remaining. This will be the sorted list.
{% endstep %}
{% endstepper %}

***

## Top-down implementation

Example C-like code using indices for top-down merge sort that recursively splits the list into sublists until sublist size is 1, then merges those sublists to produce a sorted list. The example shows alternating source/destination arrays to avoid repeated copying.

{% code title="Top-down merge sort (C-like)" %}
```c
// Array A[] has the items to sort; array B[] is a work array.
void TopDownMergeSort(A[], B[], n)
{
    CopyArray(A, 0, n, B);           // one time copy of A[] to B[]
    TopDownSplitMerge(A, 0, n, B);   // sort data from B[] into A[]
}

// Split A[] into 2 runs, sort both runs into B[], merge both runs from B[] to A[]
// iBegin is inclusive; iEnd is exclusive (A[iEnd] is not in the set).
void TopDownSplitMerge(B[], iBegin, iEnd, A[])
{
    if (iEnd - iBegin <= 1)                     // if run size == 1
        return;                                 //   consider it sorted
    iMiddle = (iEnd + iBegin) / 2;              // iMiddle = mid point
    TopDownSplitMerge(A, iBegin,  iMiddle, B);  // sort the left  run
    TopDownSplitMerge(A, iMiddle,    iEnd, B);  // sort the right run
    TopDownMerge(B, iBegin, iMiddle, iEnd, A);
}

//  Left source half is A[ iBegin:iMiddle-1].
// Right source half is A[iMiddle:iEnd-1   ].
// Result is            B[ iBegin:iEnd-1   ].
void TopDownMerge(B[], iBegin, iMiddle, iEnd, A[])
{
    i = iBegin, j = iMiddle;

    for (k = iBegin; k < iEnd; k++) {
        if (i < iMiddle && (j >= iEnd || A[i] <= A[j])) {
            B[k] = A[i];
            i = i + 1;
        } else {
            B[k] = A[j];
            j = j + 1;
        }
    }
}

void CopyArray(A[], iBegin, iEnd, B[])
{
    for (k = iBegin; k < iEnd; k++)
        B[k] = A[k];
}
```
{% endcode %}

Sorting the entire array is accomplished by `TopDownMergeSort(A, B, length(A))`.

***

## Bottom-up implementation

Example C-like code for bottom-up merge sort which treats the list as an array of n runs of size 1, and iteratively merges sublists back and forth between two buffers:

{% code title="Bottom-up merge sort (C-like)" %}
```c
// array A[] has the items to sort; array B[] is a work array
void BottomUpMergeSort(A[], B[], n)
{
    for (width = 1; width < n; width = 2 * width)
    {
        for (i = 0; i < n; i = i + 2 * width)
        {
            BottomUpMerge(A, i, min(i+width, n), min(i+2*width, n), B);
        }
        CopyArray(B, A, n);
    }
}

void BottomUpMerge(A[], iLeft, iRight, iEnd, B[])
{
    i = iLeft, j = iRight;
    for (k = iLeft; k < iEnd; k++) {
        if (i < iRight && (j >= iEnd || A[i] <= A[j])) {
            B[k] = A[i];
            i = i + 1;
        } else {
            B[k] = A[j];
            j = j + 1;
        }
    }
}

void CopyArray(B[], A[], n)
{
    for (i = 0; i < n; i++)
        A[i] = B[i];
}
```
{% endcode %}

***

## Top-down implementation using lists

Pseudocode for top-down merge sort that divides the input list into smaller sublists until trivially sorted, then merges sublists while returning up the call chain.

{% code title="Top-down merge sort (lists, pseudocode)" %}
```
function merge_sort(list m) is
    if length of m ≤ 1 then
        return m

    var left := empty list
    var right := empty list
    for each x with index i in m do
        if i < (length of m)/2 then
            add x to left
        else
            add x to right

    left := merge_sort(left)
    right := merge_sort(right)

    return merge(left, right)
```
{% endcode %}

***

## Bottom-up implementation using lists

Pseudocode for bottom-up merge sort using a small fixed-size array of references, merging runs of growing sizes:

{% code title="Bottom-up merge sort (lists, pseudocode)" %}
```
function merge_sort(node head) is
    if head = nil then
        return nil
    var node array[32]; initially all nil
    var node result
    var node next
    var int  i
    result := head
    while result ≠ nil do
        next := result.next;
        result.next := nil
        for (i = 0; (i < 32) && (array[i] ≠ nil); i += 1) do
            result := merge(array[i], result)
            array[i] := nil
        if i = 32 then
            i -= 1
        array[i] := result
        result := next
    result := nil
    for (i = 0; i < 32; i += 1) do
        result := merge(array[i], result)
    return result
```
{% endcode %}

***

## Top-down implementation in a declarative style

Haskell-like pseudocode demonstrating a functional style:

{% code title="Haskell-like pseudocode" %}
```
mergeSort :: Ord a => [a] -> [a]
mergeSort []  = []
mergeSort [x] = [x]
mergeSort xs  = merge (mergeSort l, mergeSort r)
  where (l, r) = splitAt (length xs `div` 2) xs

merge :: Ord a => ([a], [a]) -> [a]
merge ([], xs) = xs
merge (xs, []) = xs
merge (x:xs, y:ys) | x <= y    = x : merge(xs, y:ys)
                   | otherwise = y : merge(x:xs, ys)
```
{% endcode %}

***

## Analysis

![Merge sort diagram](https://upload.wikimedia.org/wikipedia/commons/thumb/e/e6/Merge_sort_algorithm_diagram.svg/500px-Merge_sort_algorithm_diagram.svg.png)

For sorting n objects, merge sort has average and worst-case performance O(n log n). The recurrence T(n) = 2 T(n/2) + n follows from splitting and merging. The number of comparisons in the worst case is given by the sorting numbers and is between (n log n − n + 1) and (n log n + n + O(log n)). For large n and random input, the expected number of comparisons is about α·n fewer than the worst case, where α ≈ 0.2645.

Merge sort uses approximately 39% fewer comparisons than quicksort's average case in the worst case, and in terms of moves its worst-case complexity is O(n log n). Merge sort is stable and is more efficient than quicksort for data that can only be accessed sequentially (e.g., linked lists). Typical array-based implementations are not in-place; they require O(n) extra space (though there are in-place variants and optimizations).

***

## Natural merge sort

A natural merge sort is similar to bottom-up merge sort but exploits naturally occurring runs (sorted sequences) in the input. It may require fewer passes if the input contains long runs; in the best case (already sorted), it needs only one pass. Natural merge sort is a key component of [Timsort](/broken/pages/f2e6d0227437f58cd6a5edaf06f218896534d361).

Example:

```
Start       :  3  4  2  1  7  5  8  9  0  6
Select runs : (3  4)(2)(1  7)(5  8  9)(0  6)
Merge       : (2  3  4)(1  5  7  8  9)(0  6)
Merge       : (1  2  3  4  5  7  8  9)(0  6)
Merge       : (0  1  2  3  4  5  6  7  8  9)
```

***

## Ping-pong merge sort

A ping-pong merge merges four blocks at a time: four sorted blocks are merged simultaneously into auxiliary space into two sorted blocks, which are then merged back to main memory. This avoids a copy operation and reduces moves. Variants include WikiSort (2014) and Quadsort (2020).

***

## In-place merge sort

Merge sort's O(n) extra memory requirement has motivated many in-place variants:

* Kronrod (1969) suggested a constant-space version.
* Katajainen et al. present an algorithm using constant working memory but not stable.[\[13\]](merge-sort-wikipedia.md#cite_note-13)
* Geffert et al. showed in-place, stable merging in O(n log n) time with constant scratch space but with high constants.[\[14\]](merge-sort-wikipedia.md#cite_note-14)
* Practical in-place merges with low overhead have been proposed (e.g., Huang & Langston).[\[15\]](merge-sort-wikipedia.md#cite_note-Research_Contributions-15)
* Block merge sort is a modern stable, linear, and in-place variant using a section of unique values as swap space.
* Space overhead can be reduced to O(√n) using binary searches and rotations (used by C++ STL and quadsort).[\[17\]](merge-sort-wikipedia.md#cite_note-17)
* Merging by relinking nodes (for records with pointer fields) avoids moving entire records.

A simple reduction to n/2 extra space copies only the left part into temporary space and merges into the original array.

***

## Use with tape drives

Merge sort algorithms were practical on early machines with small memory by using sequential I/O with tape drives. External merge sort is used when data doesn't fit in memory. A typical tape-drive approach (using four drives A,B,C,D) follows an iterative merge pattern.

{% stepper %}
{% step %}
Merge pairs of records from A; write two-record sublists alternately to C and D.
{% endstep %}

{% step %}
Merge two-record sublists from C and D into four-record sublists; write these alternately to A and B.
{% endstep %}

{% step %}
Merge four-record sublists from A and B into eight-record sublists; write these alternately to C and D.
{% endstep %}

{% step %}
Repeat until one sorted list remains — log2(n) passes.
{% endstep %}
{% endstepper %}

A hybrid approach often creates long initial runs by reading many records into memory and sorting them internally (e.g., internal sort of 1024 records saves nine passes). Knuth's 'snowplow' technique (a binary min-heap) can generate runs longer than available internal memory on average.[\[18\]](merge-sort-wikipedia.md#cite_note-18)

External variants can use fewer tapes with some overhead; using k > 2 tapes (and O(k) items in memory) allows k/2-way merges to reduce tape operations.

***

## Optimizing merge sort

Locality of reference and cache-awareness are important for performance. Tiled merge sort stops partitioning subarrays when size S (fitting in cache) is reached, sorts each tile with an in-place algorithm (e.g., insertion sort), then completes merges recursively. This can improve performance on modern architectures. (LaMarca & Ladner 1997)

***

## Parallel merge sort

Merge sort parallelizes well. Variants include parallel recursion, parallel merging, and parallel multiway merge sort.

### Merge sort with parallel recursion

A straightforward parallelization forks recursive calls:

{% code title="Parallel recursion (pseudocode)" %}
```
// Sort elements lo through hi (exclusive) of array A.
algorithm mergesort(A, lo, hi) is
    if lo+1 < hi then  // Two or more elements.
        mid := floor((lo + hi) / 2)
        fork mergesort(A, lo, mid)
        mergesort(A, mid, hi)
        join
        merge(A, lo, mid, hi)
```
{% endcode %}

This naive approach does not parallelize the merge step, limiting speedup.

### Merge sort with parallel merging

Using a parallel merge algorithm (e.g., binary selection of a pivot element and splitting the other sequence with binary search) yields better parallelism. Cormen et al. present such a variant where parallel merges reduce span and improve theoretical parallelism.

### Parallel multiway merge sort

K-way merges generalize binary merge; a practical parallel approach distributes data across p processors, sorts locally, selects global splitters (via multisequence selection), partitions sequences, then each processor performs a p-way merge on its assigned subsequences.

Basic steps:

1. Distribute n elements equally to p processors; sort locally.
2. Find splitter elements v1...vp of global ranks j·(n/p).
3. Partition each sequence Si at positions determined by splitters.
4. Assign parts S1,i...Sp,i to processor i; processor i merges its received subsequences.

The multi-sequence selection (msSelect) finds split positions via iterative pivot selection and parallel/sequential binary searches across sequences.

Pseudocode (high level):

{% code title="Parallel multiway mergesort (pseudocode)" %}
```
algorithm parallelMultiwayMergesort(d : Array, n : int, p : int) is
    o := new Array[0, n]                         // output array
    for i = 1 to p do in parallel
        S_i := d[(i-1) * n/p, i * n/p]          // Sequence of length n/p
        sort(S_i)                               // sort locally
    synch
    v_i := msSelect([S_1,...,S_p], i * n/p)     // splitter elements
    synch
    (S_i,1, ..., S_i,p) := sequence_partitioning(si, v_1, ..., v_p)
    o[(i-1) * n/p, i * n/p] := kWayMerge(s_1,i, ..., s_p,i)
    return o
```
{% endcode %}

This approach is scalable and suitable for large clusters, though practical concerns like memory hierarchy and communication overhead must be considered. Hierarchical multi-level approaches reduce communication (see Sanders et al.).

***

## Further variants

Many parallel and optimized variants exist (e.g., Richard Cole's subsampling for O(1) merge, Quadsort, Timsort). Sophisticated parallel algorithms or sorting networks may achieve different time bounds in specific models.

***

## Comparison with other sorting algorithms

* Heapsort: same time bounds as merge sort but uses Θ(1) auxiliary space instead of Θ(n).
* Quicksort: often faster for RAM-based arrays due to better cache locality; quicksort typically uses O(log n) space. Merge sort is stable and preferred for linked lists (can be implemented with Θ(1) extra space).
* Timsort (hybrid of merge and insertion sort) is widely used (Python, Java platforms) and exploits runs; Powersort is a recent update used by Python 3.11.

Perl 5.8 uses merge sort as its default; Java's Arrays.sort uses merge or tuned quicksort depending on types and switches to insertion sort for small arrays. The Linux kernel uses merge sort for its linked lists.

***

## References

(Selected references; full list preserved in original source)

1. Skiena (2008), p. 122.
2. Goodrich, Michael T.; Tamassia, Roberto; Goldwasser, Michael H. (2013). "Chapter 12 - Sorting and Selection". Data structures and algorithms in Python. Wiley. pp. 538–549. ISBN 978-1-118-29027-9.
3. Knuth (1998), p. 158.
4. Katajainen, Jyrki; Träff, Jesper Larsson (March 1997). "Algorithms and Complexity". Proceedings of the 3rd Italian Conference on Algorithms and Complexity. Lecture Notes in Computer Science. Vol. 1203. pp. 217–228. doi:10.1007/3-540-62592-5\_74.
5. Cormen et al. (2009), p. 36.\
   ... (additional numbered references in original)

***

## Bibliography

* Cormen, Thomas H.; Leiserson, Charles E.; Rivest, Ronald L.; Stein, Clifford (2009). Introduction to Algorithms (3rd ed.). MIT Press. ISBN 0-262-03384-4.
* Katajainen, Jyrki; Pasanen, Tomi; Teuhola, Jukka (1996). "Practical in-place mergesort". Nordic Journal of Computing. 3 (1): 27–40.
* Knuth, Donald (1998). The Art of Computer Programming, Vol. 3. Addison-Wesley.\
  (see original for full bibliography)

***

## External links

* The Wikibook "Algorithm implementation" has a page on: Merge sort — https://en.wikibooks.org/wiki/Algorithm\_implementation/Sorting/Merge\_sort
* Animated Sorting Algorithms: Merge Sort (archived) — https://web.archive.org/web/20150306071601/http://www.sorting-algorithms.com/merge-sort
* Open Data Structures - Section 11.1.1 - Merge Sort — http://opendatastructures.org/...
* C Program to Implement Merge Sort Algorithm — https://www.sanfoundry.com/c-program-merge-sort-using-recursion/
* Merge Sort Code with Java — https://javachallengers.com/merge-sort-with-java/
* C++ Program for Merge Sort — https://www.ccbp.in/blog/articles/merge-sort-cpp

***

Categories: Comparison sorts; Stable sorts; Divide-and-conquer algorithms

Retrieved from "https://en.wikipedia.org/w/index.php?title=Merge\_sort\&oldid=1329972465"
