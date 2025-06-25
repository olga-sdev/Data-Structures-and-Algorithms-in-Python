### Divide and Conquer

_Complexity of Binary Search_

A dataset of length _n_ can be divided _log n_ times til everything is completely divided.

The search complexity of binary search is O(log n).


_Iterative Binary Search_

A binary search can be performed in an iterative approach. 
Loop -> calling function withing the function in recursion.

```python
def iterative_binary_search(target, records, left, right):
    while right > left:
        mid = (right + left) / 2
        if target < records[mid]:
            right = mid
        elif target > records[mid]:
            left = mid
        else:
            return mid
    return -1
```


_Recursive Binary Search_

In recursive binary search, if the value has not been found then the recursion 
must continue on the list by updating the left and right pointers after comparing
the target value to the mid value:

```python
def recursive_binary_search(records, first, last, target):
    mid = (first + last) // 2
    if target < records[mid]:
        return recursive_binary_search(records, first, mid, target)
    else:
        return recursive_binary_search(records, mid, last, target)
```


_Binary Search Sorted Dataset_

Binary search performs the search for the target withing a sorted array.
Array must be sorted before performance of binary search.


_Operation of Binary Search_

The binary search starts the process with comparing the mid element of sorted dataset with the target value for a match.
When the mid element == to the target val -> algorithm completed.

Otherwise, the half in which the target cannot logically exist is eliminated and the search continues on the remaining half.

The decision of discarding one half is achievable since the dataset is sorted.


_Binry Search Performance_

Worst-case time complexity -> O(log N);

As the number of values in dataset increases, the performance time of the algorithm increases.

Binary searching a list of 64 elements takes at most _log2(64) = 6_ comparisons to complete.


_Binary Search_

The binary search algorithm efficiently finds a goal element in a sorted dataset.

The algorithm comapares the goal with the value in the mid of data subset.

The process begins with the whole dataset.

_goal_ < _mid element_ => the algorithm repeats the process on the smaller (left) half of the dataset.

_goal_ > _mid element_ => the algorithm repeats the process on the larger (right) half of the dataset.



_Recursive Binary Search_

Binary search can be implemented using recursion by creating a function with args:
* sorted list;
* left pointer;
* right pointer;
* target

The base case must account for when the _left pointer_ == _right pointer_ OR _target_ is found => index is returned.

Initialization:
* set the _left_ pointer => index _0_ of the list;
* set the _right_ pointer => index _n_ of the list (length of the list is n).

Cases:
* IF _mid val_ > _target_ => _right pointer_ = _mid val_;
* IF _mid val_ < _target_ => _left pointer_ = _mid val_.


_Divide and Conquer Algorithm_

* Divide-and_Conquer solves a large problem by recursively breaking it down into smaller 
sub-problems till the problem can be solved directly.
* 3 steps of algorithm: divide, conquer, combine.
* more efficient than brute force approach;
* prone to stack overflow error because of recursion.

