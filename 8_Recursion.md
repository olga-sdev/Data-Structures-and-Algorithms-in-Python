#### Recursion

_Recursion_ is a concept where a function calls itself within its definition.

Recursive solution is suited for a problem that does not exceed a certain number of recursive calls.

In case of too many oiterations it throws a stack overflow error.

_Fibonacci Sequence_ -> math sequence of nums when each next num is a sum of 2 previous:

![image](https://github.com/user-attachments/assets/b25dab43-7822-4a03-9560-c4ec071ab342)




_Binary Search Tree_ - recursive data structure for searching easier in sorted lists:
* reference 2 sub-elements per tree element;
* 'left' tree sub-element contains less value than an element;
* 'right' tree sub-element contains greater value than an element;

![image](https://github.com/user-attachments/assets/2bae12b0-877f-42dc-91c5-6dc88c9ad063)



_Recursion and Nested Lists_

Nested list can be tracked and flattened with recursive function by element evaluation in a list:
* if the type of the element is list, then the function retrieves the element from that list and adds it to the flatlist:

```python
def flatten(list_of_records):
  flatlist = []
  for element in list_of_records:
    if type(element) == list:
      flatlist += flatten(element)
    else:
      flatlist += element
  return flatlist

print(flatten(['1', ['2', '3'], ['4'], '5']))

# Output: ['1', '2', '3', '4', '5']
```


_Fibonacci Recursion_

Cases: index == 0 || index == 1

```python
def fibonaci(n):
  if n <= 1:
    return n
  else:
    return fibonacci(n-1) + fibonacci(n-2)
```


_Call Stack Model of Recursion_

* while loop and list -> print the call stack list in LIFO till the list is empty;
* another while loop and list: print the result which consists of poped items from the list;

```python
def countdown(value):
  call_stack = []
  while value > 0:
    call_stack.append({"input":value})
    print("Call Stack:", call_stack)
    value -= 1
  print("\nBase Case Reached\n")
  while len(call_stack) != 0:
    print(f"Popping {call_stack.pop()} from call stack")
    print("Call Stack:", call_stack)

countdown(3)

"""
Output:

Call Stack: [{'input': 3}]
Call Stack: [{'input': 3}, {'input': 2}]
Call Stack: [{'input': 3}, {'input': 2}, {'input': 1}]

Base Case Reached

Popping {'input': 1} from call stack
Call Stack: [{'input': 3}, {'input': 2}]
Popping {'input': 2} from call stack
Call Stack: [{'input': 3}]
Popping {'input': 3} from call stack
Call Stack: []
"""
```


