### Sorting Algorithms


#### Merge Sort Merging 

_Merge sort_ is a divide and conquer algorithm with parts:
* splitting orig list into smaller ones;
* merging back the presorted lists.

Merging portion (2 sublists) -> iterate till _left_/_right_ sublist is empty:
* IF _1st_ element of _left_ sublist < _1st_ element of _right_ sublist => 
=> add _1st left_ to new sorted list and removed from _left_ sublist;
* IF _1st_ element of _left_ sublist > _1st_ element of _right_ sublist => 
=> add _1st right_ to new sorted list and removed from _right_ sublist;
* Remaining non-empty sublist is added to the sorted list (in case it exists).


_Big-O Runtime for Merge Sort_

Algorithm is divided into 2 parts:
* _1st part_ splits lists into smaller single-element lists =>
=> best, worst and avg runtime for this part is O(log N) (theta);
* _2d part_ merges and sorts the single-element lists to twice its size till the orig input size is achieved =>
=> best, worst and avg runtime for this part is O(N) (theta);
* The combined runtime is O(N log N).
