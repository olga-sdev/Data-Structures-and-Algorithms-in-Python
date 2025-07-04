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


_Depth First Traversal_

The BinarySearchTree Python class _.depth_first_traversal()_ method prints the in-order depth-first traversal of the tree in ASC.

```python
def depth_first_traversal(self):
    if self.left is not None:
        self.left.depth_first_traversal()
    print(f'Depth={self.depth}, Value={self.value}')
    if self.right is not None:
        self.right.depth_first_traversal()
```


_Getting Node by value_

The BinarySearchTree Python class _.get_node_by_value()_ method takes value and returns _None_ or _BinarySearchTree node_.

Searching through the sides of the tree with recursion.

Performance for avg balanced binary search tree => O(logN):

```python
def get_node_by_value(self, value):
    if self.value == value:
        return self
    elif self.left is not None and value < self.value:
        return self.left.get_node_by_vlue(value)
    elif self.right is not None and value >= self.value:
        return self.right.get_node_by_value(value)
    else:
        return None
```

_Insertion_

The BinarySearchTree class _.insert()_ method with _value_ arg and recursion.

Method returns None.

Performance O(logN).

```python
def insert(self, value):
    if value < self.value:
        if self.left is None:
            self.left = BinarySearchTree(value, self.depth + 1)
            print(f'Tree node {value} added to the left of {self.value} at depth {self.depth + 1}')
        else:
            self.left.insert(value)
    else:
        if self.right is None:
            self.right = BinarySearchTree(value, self.depth + 1)
            print(f'Tree node {value} added to the right of {self.value} at depth {self.depth + 1}')
        else:
            self.right.insert(value)
```


_Constructor_

The constructor of BinarySEarchTree contains parameters:
* value;
* depth (default value is 1)
* left (None)
* right (None)


```python
def __init__(self, value, depth=1):
    self.value = value
    self.depth = depth
    self.left = None
    self.right = None
```
