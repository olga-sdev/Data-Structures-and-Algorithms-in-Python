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
