#### Asymptonic Notation

Speed of algorithm (number of iterations) with a help of while loop and counter:

```python
def algorithm_speed(n):
  counter = 0
  while n > 1:
    n -= 1
    counter += 1
  return counter

print(algorithm_speed(10))  # 9
```


_Queue_ -> based on FIFO: takes _O(1)_ runtime to retrieve the 1st item in a Queue;

_Stack_ -> based on FILO: takes _O(N)_ runtime to retrive the 1st value in Stack;


![Queue](https://github.com/user-attachments/assets/8ccc6a32-8abb-482e-bbe8-f01db3ce07df)


_Max Value Search in List_

Big-O runtime for locating the max value in a list of size N is _O(N)_ because of the entire list of N has to be overpassed.

```python
def find_max_element(linked_list):
  current_head = linked_list.get_head_node()
  max_value = current_head.get_value()
  while current_head.get_next_node():
    current_head = current_head.get_next_node()
    val = current_head.get_value()
    if val > max_value
      max_value = val
  return max_value
  
print(find_max_element([1, 3, 5, 98]))
```


_Bubble Sort with Linked List_


Bubble sort -> comparison of element with neighbor and swap thm in case of descending order.

Each pass of swap takes O(N).

Since there are N elements in list -> N*N swaps or (N^2).

Big O runtime is O(N*N) or O(N^2).


_Asymptonic Notation_ describes the running time of algorithm: time the algorithm takes with a given input N.

Notations:
* big O -> the worst case running time;
* big Theta (Θ) -> running time is the same for all cases;
* big Ω -> the best case running time.

In cases of many part of algorithm structure -> it's runtime described based on the slowest part of the program.

Algorithmic Common Runtimes from fastest to slowest:
* constant Θ(1)
* logarithmic Θ(log N)
* linear Θ(N)
* polynomial Θ(N^2)
* exponential Θ(2^N)
* factorial Θ(N!)

![image](https://github.com/user-attachments/assets/78066a03-2fcf-446c-85b4-0905b13fcf74)



_Big-O Notation_ -> describes the worst-case running time of program: 
counting numbers of iterations that the algorithm takes in the worst case scenario with an input N.

O(log n) describes the Big-O of a binary search algorithm.

_Big-Ω Notation_ -> describes the best-case running time of program.
Bubble Sort algorithm has a running time of Ω(N) because in the best case scenario the list is sorted already - 
the bubble sort will terminate after the first iteration.
