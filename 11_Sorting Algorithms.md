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

