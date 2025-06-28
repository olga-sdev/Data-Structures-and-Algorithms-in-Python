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
