### Heaps and Heapsort

_.add() method_ in MaxHeap class for adding new values to max-heap.
Max=heap property - parent must have larger value than its child.


```python
def add(self, element):
    self.count += 1
    print(f'Adding: {element} to {self.heap_list}')
    self.heap_list.append(element)
    self.heapify_up()
```


_heapify_up() method_ for rebalancing the heap data structure after adding the element.

Beginning from the end (location of the new element), the new element is compared to its parent value:
* IF _parent_val_ < _child_val_ -> swap elements
Process is finished when the element has no parent values.


```python
def heapify_up(self):
    print('Heapifying up')
    index = self.count
    while self.parent_index(index) > 0:
        child_e = self.heap_list[index]
        parent_e = self.heap_list[self.parent_index(index)]
        if parent_e < child_e:
            print(f'swapping {parent_e} with {child_e}')
            self.heap_list[index] = parent_e
            self.heap_list[self.parent_index(index)] = child_e
        index = self.parent_index(index)
    print(f'Heap restored {self.heap_list}')
```

_Heapsort_ - sorting algorithm that utilizes the heap data structure to sort an unordered list of data.

Implementation of heapsort algorithm:
* add items of unsorted list to max-heap;
* when 1 element in heap -> remove _heap root_ -> locate _heap root_ to the beginning of the list;
* when _heap_ is empty -> return the sorted list.


```python
def heapsort(records):
    sort = []
    max_heap = MaxHeap()
    
    # Add items of an unsorted list into a max-heap
    for item in records:
        max_heap.add(item)
        
    """
    While there is at least one element in the heap,
    remove the root of the heap and place it at the beginning of the list
    that will hold the sorted values.
    Whenever the root is extracted,
    the hep must be rebalanced.
    """
    while max_heap.count > 0:
        max_value = max_heap.retrieve_max()
        sort.insert(0, max_value)
        
    # Return the sorted list
    return sort
    

new_records = [21, 34, 56, 93, 192, 74]
sorted_records = heapsort(new_records)

print(sorted_records)
# [21, 34, 56, 74, 93, 192]

```


_.retrieve_max() method_ - return the largest value in a heap:
* _heap root_ is extracted and replaced by the last element in the heap.
* _.heapify_down()_ - rebalancing the heap data structure.
* returns the largest value.


```python
def retrieve_max(self):
    if self.count == 0:
        print('Empty heap')
        return None

    # Store the largest value in a variable
    max_value = self.heap_list[1]
    print(f'Removing: {max_value} from {self.heap_list}')
    
    # Replace the root of the heap with the last element in list
    self.heap_list[1] = self.heap_list[self.count]
    
    # Decrease the count
    self.count -= 1
    
    # Remove the last element in the list
    self.heap_list.pop()
    print(f'Last element moved to first: {self.heap_list}')
    
    # Rebalance the heap
    self.heapify_down()
    
    # Return the largest value
    return max_value
```

