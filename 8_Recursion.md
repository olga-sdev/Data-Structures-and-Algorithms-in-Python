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

```

![image](https://github.com/user-attachments/assets/dbd47339-7db8-42bd-9b55-a7c51415026b)

```python

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


_Call stack_ for a recursive function calls the last function in stack when the base case met.

_Big-O Runtime for Recursive function_ == number of recursive function calls.
The value varies depending of algorithm complexity.

Recursive function of input N which calls _N times_ has runtime of _N(O)_.

Recursive function of input N which calls _itself twice per function_ has runtime of _O(2^N)_.


_Weak Base Case_ -> does not stop the function from recurtion and lead to stack overflow error.

_Execution context_ -> set of args to recursive function call.


_Recursive depth of Binary Search Tree_

_Binary search tree_ -> data structure that builds a sorted input list into 2 subtrees (subelements).

Left subelement value < root value;

Right subelement value > root value;

Recursive function to determine the depth of tree:

```python

class Node:
    def __init__(self, value):
        self.value = value
        self.left = None
        self.right = None

def depth(node):
    if node is None:
        return 0
    
    left_depth = depth(node.left)
    right_depth = depth(node.right)
    
    return max(left_depth, right_depth) + 1

# Example usage
root = Node(10)
root.left = Node(5)
root.right = Node(15)
root.left.left = Node(3)
root.left.right = Node(7)

print(f'Depth of the BST {depth(root)}')  # Output: Depth of the BST

"""
Output:

Depth of the BST 3

```

_Sum Digits with Recursion_

```python
def sum_digits(digit):
  if digit <= 9:
    return digit
  last_digit = digit % 10
  return sum_digits(digit // 10) + last_digit

print(f'Sum of digits {sum_digits(749)}')  # 749 -> 7 + 4 + 9
# Sum of digits 20

```


_Panildrome in Recursion_

Palindrome - the work cam be read the same both ways (forward and backwork).

Recursive function for palindrome word:

```python
def is_palindrome(word):
  if len(word) <= 1:
    return True
  if word[0] != word[-1]:
    return False
  return is_palindrome(word[1:-1])

print(is_palindrome('abba')) # True
print(is_palindrome('abc')) # False
```

Other example of function without recurtion:

```python
def is_palindrome(word):
  return word == word[::-1]
  
print(is_palindrome('abba'))  # True

```


_Fibonacci Iterative Function_

In particular example: fibonacci from 11 

```python
def fibonacci(digit):
  if digit < 0:
    raise ValueError('Input beginning from 0')
  fibonacci_record = [0, 1]
  for num in range(2, digit+1):
    record = fibonacci_record[num-1] + fibonacci_record[num-2]
    print(record)
    fibonacci_record.append(record)
  return fibonacci_record[num]

print(f'Fibonacci: {fibonacci(11)}')


"""
Output:

1
2
3
5
8
13
21
34
55
89
Fibonacci: 89
"""

```



