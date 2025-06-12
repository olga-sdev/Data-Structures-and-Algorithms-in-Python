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


_Swapping Variables in Bubble Sort_

Bubble sort function -> iteratively swap element with neighbor with smaller value till elements in list is sorted ASC.

```python
def swap(arr, left_pos, right_pos):
    arr[left_pos], arr[right_pos] = arr[right_pos], arr[left_pos]


def bubble_sort(arr):
    for item in arr:
        for index in range(len(arr) - 1):
            if arr[index] > arr[index + 1]:
                swap(arr, index, index + 1)
    return arr


my_arr = bubble_sort([2, 45, 3, 899, 6, 71])
print(my_arr)

# [2, 3, 6, 45, 71, 899]
```


#### _Merge Sort Implementation in Python_

* Main function -> merge_sort(lst);
* Helper function -> merge(left, right).

```python
def merge_sort(lst):
    if len(lst) <= 1:
        return lst
    middle = len(lst) // 2
    left = lst[:middle]
    right = lst[middle:]
    sleft = merge_sort(left)
    sright = merge_sort(right)
    return merge(sleft, sright)
    

def merge(left, right):
    result = []
    while left and right:
        if left[0] < right[0]:
            result.append(left[0])
            left.pop(0)
        else:
            result.append(right[0])
            right.pop(0)
    if left:
        result += left
    if right:
        result += right
    return result
```

#### Quick Sort Performance

Inefficient in case of imbalanced partitions.
Worst case -> 1st | last element is always partition point for an array or sub-array:
one side of partition contains all elements.
Making recursive stack deeper (O(N^2) runtime).


#### Quick Sort General

_Quicksort_ is a method for sorting an array by repeatedly partitioning it into sub-arrays by:

* selecting element from the current array (_pivot element_);
* comparing element from array with _pivot element_ (swap elements);
* _partition point_ is point where elements before is less, after is greater then;
* repeat the process on sub-arrays separated by the partition point -> continue till sub-array contains 1 element.
* when the partitioning-swapping are done -> array is sorted from smallest to largest.

The worst case runtime -> O(N^2);
Avg -> O(N logN);


#### Bubble Sort Algorithm

Sort a list in ASC order: iterating through a list and comparing:

* inner iteration: compare 1st and 2nd elements - swapping, then 2nd and 3d etc.
* outer iteration: repeated for all elements.

_Bubble sort Big-O Runtime_

2 loops:

* outer loop (_N_ iterations): iterate over each element in the input list;
* inner loop (_N-1_ iterations): compare and exchange a pair of values in the list.

Big-O runtime for the algorithm is a product of O(N) and O(N-1) => O(N^2).


_Bubble sort Swapping Variables_

The Bubble Sort algorithm requires swapping of variables in order to sort them.
The swapping algorithm is dependent on programming language.
For the most languages, temporary variable is needed to hold one of the values being swapped:

```python
temp = num_1
num_1 = num_2
num_2 = temp
```


For others (Python), it can be done with the single assignment:

```python
num1_, num_2 = num_2, num_1
```
