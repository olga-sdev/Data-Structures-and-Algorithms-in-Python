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
    call_stack.append(value)
    print("Call Stack:", call_stack)
    value -= 1
  print("\nBase Case Reached\n")
  while len(call_stack) != 0:
    print(f"Popping {call_stack.pop()} from call stack")
    print("Call Stack:", call_stack)

countdown(3)

"""
Output:

    
Call Stack: [3]
Call Stack: [3, 2]
Call Stack: [3, 2, 1]

Base Case Reached

Popping 1 from call stack
Call Stack: [3, 2]
Popping 2 from call stack
Call Stack: [3]
Popping 3 from call stack
Call Stack: []
"""
```

_Recursion in Python_

Recursive function accepts an arg and base case (condition), it has:
* _base case_ -> input evaluation to interrupt the recurtion;
* _recursive step_ -> call(s) to recursive function to bring the input to the base case.

```python
def countdown(value):
  if value <= 0:  # base case
    print('done')
  else:
    print(value)
    countdown(value - 1)  # recursive case
```


_Build Binary Search Tree_

```python
def build_binary_search_tree(list_of_records):
  if len(list_of_records) == 0:
    return 'no sub-elements'

  middle_index_of_list = len(list_of_records) // 2
  middle_value_of_list = list_of_records[middle_index_of_list]

  print(f'Middle index: {middle_index_of_list}')
  print(f'Middle value: {middle_value_of_list}')

  tree_node = {'middle_value_of_list': middle_value_of_list}
  tree_node['left_subelement'] = build_binary_search_tree(list_of_records[ : middle_index_of_list])
  tree_node['right_subelement'] = build_binary_search_tree(list_of_records[middle_index_of_list+1 : ])

  return tree_node

sorted_list = [1, 10, 15, 20, 50]
binary_search_tree = build_binary_search_tree(sorted_list)
print(binary_search_tree)

"""
Output:


Middle index: 2
Middle value: 15

Middle index: 1
Middle value: 10

Middle index: 0
Middle value: 1

Middle index: 1
Middle value: 50

Middle index: 0
Middle value: 20

{'middle_value_of_list': 15,

'left_subelement':

{'middle_value_of_list': 10,
'left_subelement': {'middle_value_of_list': 1, 'left_subelement': 'no sub-elements', 'right_subelement': 'no sub-elements'},
'right_subelement': 'no sub-elements'},

'right_subelement':

{'middle_value_of_list': 50,
'left_subelement': {'middle_value_of_list': 20, 'left_subelement': 'no sub-elements', 'right_subelement': 'no sub-elements'},
'right_subelement': 'no sub-elements'}}

"""
```

![image](https://github.com/user-attachments/assets/dbd47339-7db8-42bd-9b55-a7c51415026b)


