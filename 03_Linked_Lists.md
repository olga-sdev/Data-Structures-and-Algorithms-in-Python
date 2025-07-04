#### Concept of Linked lists

The list is involved numbers of nodes:
* head node -> at the beginning of the list.
* each node contains data and a link (or pointer) to the next node in the list.
* The list is terminated when a node’s link is null. Last node -> tail node.

Common operations:
* adding nodes -> link new node to the current head node;
* removing nodes -> removing all references to the node (be sure to adjust the link on the previous node so that it points to the following node);
In order to remove node_b, you must first link node_a to node_c (where node_b was linking). Then you can remove node_b.
* finding a node;
* traversing (or traveling through) the linked list.


#### Node Implementation
Implementation of linked list in Python.

_Task_
1. Create an empty Node class.   
Inside, define an __init__() method for the Node. It should take a value and a next_node.
next_node should default to None if not provided. These variables should be saved to self with corresponding key names.
2. Define .get_value() and .get_next_node() methods. These should return the corresponding values from self.
3. Define a .set_next_node() method that takes self and next_node as parameters and allows you to update the link to the next node.
4. Outside the Node class, create an instance of Node called my_node with a value of 44.
Use .get_value() to print the value of my_node.

```
# Define your Node class below:
class Node:
  def __init__(self, value, next_node=None):
    self.value = value
    self.next_node = next_node

  def get_value(self):
    return self.value

  def get_next_node(self):
    return self.next_node

  def set_next_node(self, next_node):
    self.next_node = next_node

my_node = Node(44)
print(my_node.get_value())
```


#### Linked List Implementation I

_Task_
1. Create an empty LinkedList class.
Define an .__init__() method for the LinkedList. We want to be able to instantiate a LinkedList with a head node, so .__init__() should take value as an argument.
Make sure value defaults to None if no value is provided.
Inside the .__init__() method, set self.head_node equal to a new Node with value as its value.
2. Define a .get_head_node() method that helps us peek at the first node in the list.
Inside the method, return the head node of the linked list.

```
# We'll be using our Node class
class Node:
  def __init__(self, value, next_node=None):
    self.value = value
    self.next_node = next_node
    
  def get_value(self):
    return self.value
  
  def get_next_node(self):
    return self.next_node
  
  def set_next_node(self, next_node):
    self.next_node = next_node


# Create your LinkedList class below:
class LinkedList:
  def __init__(self, value=None):
    self.value = value
    self.head_node = Node(value)

  def get_head_node(self):
    return self.head_node
```


#### Linked Lists Implementation II

_Task_
1. Define an .insert_beginning() method which takes new_value as an argument.
Inside the method, instantiate a Node with new_value. Name this new_node.
Now, link new_node to the existing head_node.
Finally, replace the current head_node with new_node.
2. Define a .stringify_list() method we can use to print out a string representation of a list’s nodes’ values.
The method should traverse the list, beginning at the head node, and collect each node’s value in a string.
Once the end of the list has been reached, the method should return the string.
You can use str() to convert integers to strings!
Be sure to add "\n" between values so that each value prints on a new line.


```
# We'll be using our Node class
class Node:
  def __init__(self, value, next_node=None):
    self.value = value
    self.next_node = next_node
    
  def get_value(self):
    return self.value
  
  def get_next_node(self):
    return self.next_node
  
  def set_next_node(self, next_node):
    self.next_node = next_node

# Our LinkedList class
class LinkedList:
  def __init__(self, value=None):
    self.head_node = Node(value)
  
  def get_head_node(self):
    return self.head_node
  
# Add your insert_beginning and stringify_list methods below:
  def insert_beginning(self, new_value):
    new_node = Node(new_value)
    new_node.set_next_node(self.head_node)
    self.head_node = new_node

  def stringify_list(self):
    string_list = ''
    current_node = self.get_head_node()
    while current_node: 
      if current_node.get_value() != None:
        string_list += str(current_node.get_value()) + '\n'
      current_node = current_node.get_next_node()
    return string_list


# Test your code by uncommenting the statements below - did your list print to the terminal?
ll = LinkedList(5)
ll.insert_beginning(70)
ll.insert_beginning(5675)
ll.insert_beginning(90)
print(ll.stringify_list())
```


#### Linked List Implementation III
Update the link within the a node to match what _b_ was pointing to prior to removing it from the linked list:
From a -> b -> c 
To a -> c

_Task_
1. Add a .remove_node() method to LinkedList. It should take value_to_remove as a parameter. We’ll be looking for a node with this value to remove.
In the body of .remove_node(), set a new variable current_node equal to the head_node of the list.
We’ll use current_node to keep track of the node we are currently looking at as we traverse the list.
2. Still inside the method body, use an if statement to check whether the list’s head_node has a value that is the same as value_to_remove.
If it does, we’ve found the node we’re looking for and we need to adjust the list’s pointer to head_node.
Inside the if clause, set self.head_node equal to the second node in the linked list.
3. Add an else clause. Within the else clause:
Traverse the list until current_node.get_next_node().get_value() is the value_to_remove.
(Just like with stringify_list you can traverse the list using a while loop that checks whether current_node exists.)
When value_to_remove is found, adjust the links in the list so that current_node is linked to next_node.get_next_node().
After you remove the node with a value of value_to_remove, make sure to set current_node to None so that you exit the loop.

```
# We'll be using our Node class
class Node:
  def __init__(self, value, next_node=None):
    self.value = value
    self.next_node = next_node
    
  def get_value(self):
    return self.value
  
  def get_next_node(self):
    return self.next_node
  
  def set_next_node(self, next_node):
    self.next_node = next_node

# Our LinkedList class
class LinkedList:
  def __init__(self, value=None):
    self.head_node = Node(value)
  
  def get_head_node(self):
    return self.head_node
  
  def insert_beginning(self, new_value):
    new_node = Node(new_value)
    new_node.set_next_node(self.head_node)
    self.head_node = new_node
    
  def stringify_list(self):
    string_list = ""
    current_node = self.get_head_node()
    while current_node:
      if current_node.get_value() != None:
        string_list += str(current_node.get_value()) + "\n"
      current_node = current_node.get_next_node()
    return string_list
  
  # Define your remove_node method below:
  def remove_node(self, value_to_remove):
    current_node = self.get_head_node()
    if current_node.get_value() == value_to_remove:
      # set the head_node to the second node in the list
      self.head_node = current_node.get_next_node()
    else:
      while current_node:
        next_node = current_node.get_next_node()
        if next_node.get_value() == value_to_remove:
          current_node.set_next_node(next_node.get_next_node())
          current_node = None
        else:
          current_node = next_node
```

Example_1:

```
class Node:
  def __init__(self, value, next_node = None):
    self.value = value
    self.next_node = next_node
    
class LinkedList:
  def __init__(self, head_node=None):
    self.head_node = head_node
    
  def stringify_list(self):
    string_list = ""
    current_node = self.head_node
    while current_node:
      string_list += str(current_node.value) + "."
      current_node = current_node.next_node
    return string_list
  
a = Node(5)
b = Node(70, a)
c = Node(5675, b)
d = Node(90, c)
ll = LinkedList(d)

print(ll.stringify_list())

# 90.5675.70.5.
```


Example_2:

```
class Node:
  def __init__(self, value, next_node=None):
    self.value = value
    self.next_node = next_node

class LinkedList:
  def __init__(self, head_node=None):
    self.head_node = head_node
    
  def remove_node(self, node_to_remove):
    current_node = self.head_node
    if current_node == node_to_remove:
      self.head_node = current_node.next_node
    else:
      while current_node:
        next_node = current_node.next_node
        if next_node == node_to_remove:
          current_node.next_node = next_node.next_node
          current_node = None
        else:
          current_node = next_node
```


Example_3:
```
class Node:
  def __init__(self, value, next_node=None):
    self.value = value
    self.next_node = next_node

class LinkedList:
  def __init__(self, head_node=None):
    self.head_node = head_node
    
  def add_new_head(self, new_head_node):
    new_head_node.next_node = self.head_node
    self.head_node = new_head_node
```


#### Swap two nodes in a singly linked list in Python

Swapping nodes in a linked list is useful for changing the order of elements without changing their values. 
This can help with sorting, organizing data, or meeting specific requirements in a program. 
Swapping nodes keeps the list structure, but rearranges the nodes’ positions.

Given a linked list and the 2 elements to be swapped _val1_ and _val2_, required to keep track of 4 values:

* node1 -> val1
* node1_prev -> previous node of val1
* node2 -> val2
* node2_prev -> previous node of val2

Steps for iteration:
* Iterate through the list looking for _node1_ to be swapped, keeping track of the _node1_prev_.
(To find the node with the value val1, start at the head of the linked list.
As you move through each node, check if the current node’s value matches val1. If it does, stop.
If not, remember the current node as the previous node (node1_prev) and move to the next node.
Repeat this until you find the match or reach the end of the list. This way, you always know both the node to swap and the node before it.);
* Repeat step 1 looking for the _node2_;
* If _node1_prev_ is None, _node1_ -> head of the list -> set the list’s head to _node2_.
(If node1_prev is None, it means there was no node before node1.
This only happens if node1 is the first node in the list (the head).
To swap correctly, make node2 the new head of the list by updating the list’s head pointer to point to node2.);
![Your paragraph text (1)](https://github.com/user-attachments/assets/d94201cf-0e8a-4ef5-83ee-1e8daa4b4eea)


* Otherwise, set _node1_prev_‘s next node -> _node2_;
![Your paragraph text (2)](https://github.com/user-attachments/assets/d524afc9-7cd6-48b0-ae76-a817f3d7eb50)


* If _node2_prev_ is None, set the list’s head -> _node1_;
![Your paragraph text (3)](https://github.com/user-attachments/assets/b84ad8ff-2d5e-41e7-905b-95b336d805b1)


* Otherwise, set _node2_prev_‘s next node to _node1_;
![Your paragraph text (4)](https://github.com/user-attachments/assets/043773ae-d6f4-48d8-b341-c7cb1d886645)


* Set _node1_‘s next node to _node2_‘s next node;
![Your paragraph text (5)](https://github.com/user-attachments/assets/15e108a3-d268-49b0-83b5-f0bea4703b56)


* Set _node2_‘s next node to _node1_‘s next node.
![Your paragraph text (6)](https://github.com/user-attachments/assets/70db2a6b-ebe7-4fbc-b790-77ca684faf60)



Step-by-step explanation:

* Start at the head of the list and look for the node with value val1. As you move, remember the previous node (node1_prev).
* Do the same to find the node with value val2 and its previous node (node2_prev).
* If node1 is the head (no previous node), update the head to point to node2.
(After updating the head to node2, node1 is no longer the first node in the list.
Next, the pointers are adjusted so that _node1 and node2 swap places_.
node1 will be somewhere else in the list, and its position depends on the rest of the swap logic.
The list’s structure is updated so both nodes remain in the list, just in each other’s original positions.)
* If not, make node1_prev point to node2.
* If node2 is the head, update the head to point to node1.
* If not, make node2_prev point to node1.
* Swap the next pointers of node1 and node2 so they take each other’s place in the list.


#### Finding the Matching and Preceding Nodes

Implementing code for steps 1 and 2. 
In order to swap the two nodes -> first find them. 
Use the Node class’s _.get_next_node()_ method in order to access the next node:

* Set _node1_ equal to the head of the list;
* Create a while loop that runs while node1 isn’t None. 
* Inside the loop, check if node1‘s value matches val1.
* If so, break out of the loop as the node was found.
* If there is no match, update node1_prev to be node1 and move node1 to its next node.

```
def swap_nodes(input_list, val1, val2):
  node1 = input_list.head_node
  node2 = input_list.head_node
  node1_prev = None
  node2_prev = None

  while node1 is not None:
    if node1.get_value() == val1:
      break
    node1_prev = node1
    node1 = node1.get_next_node()

  while node2 is not None:
    if node2.get_value() == val2:
      break
    node2_prev = node2
    node2 = node2.get_next_nore()
```


#### Updating the Preceding Nodes’ Pointers

Set node1_prev and node2_prev‘s next nodes, starting with node1_prev: 
* Check if node1_prev is None.
* If it is, then the node1 is the head of the list: update/swap node2 -> head.
* If node1_prev isn’t None -> set its next node to node2 (node1 -> node2).

```
# Still inside the swap_nodes() function
if node1_prev is None:
  input_list.head_node = node2
else:
  node1_prev.set_next_node(node2)

if node2_prev is None:
  input_list.head_node = node1
else:
  node2_prev.set_next_node(node1)
```

#### Updating the Nodes’ Next Pointers

The last step is to update the pointers from node1 and node2 with a help of temporary variable. 

```
temp = node1.get_next_node()
node1.set_next_node(node2.get_next_node())
node2.set_next_node(temp)
```

#### Edge Cases

1. If there is no matching node for one of the inputs:
The current swap_nodes() function will not run because of accessing the next node of a node that is None.

For this case check if either node1 or node2 is None:

```
if (node1 is None or node2 is None):
  print("Swap not possible - one or more element is not in the list")
  return
```

2. If the two nodes to be swapped are the same:
Checks if the val1 is the same as val2, and then return to end the function

```
if val1 == val2:
  print("Elements are the same - no swap needed")
  return
```

#### Completed function

```
import Node
import LinkedList

def swap_nodes(input_list, val1, val2):
  print(f'Swapping {val1} with {val2}')

  node1_prev = None
  node2_prev = None
  node1 = input_list.head_node
  node2 = input_list.head_node

  if val1 == val2:
    print("Elements are the same - no swap needed")
    return

  while node1 is not None:
    if node1.get_value() == val1:
      break
    node1_prev = node1
    node1 = node1.get_next_node()

  while node2 is not None:
    if node2.get_value() == val2:
      break
    node2_prev = node2
    node2 = node2.get_next_node()

  if (node1 is None or node2 is None):
    print("Swap not possible - one or more element is not in the list")
    return

  if node1_prev is None:
    input_list.head_node = node2
  else:
    node1_prev.set_next_node(node2)

  if node2_prev is None:
    input_list.head_node = node1
  else:
    node2_prev.set_next_node(node1)

  temp = node1.get_next_node()
  node1.set_next_node(node2.get_next_node())
  node2.set_next_node(temp)


ll = LinkedList.LinkedList()
for i in range(10):
  ll.insert_beginning(i)

print(ll.stringify_list())
swap_nodes(ll, 9, 5)
print(ll.stringify_list())


Output:

9
8
7
6
5
4
3
2
1
0

Swapping 0 with 5
9
8
7
6
0
4
3
2
1
5
```


#### Two Pointers Moving in Parallel

Consider the following problem:

Create a method that returns the nth last element of a singly linked list.

For example: given a linked list with the following elements 1 -> 2 -> 3 -> 4 -> 5, return the 2nd to last element. The answer would be element 4.

_Approaches_

Use a list to store a representation of the linked list, and then to obtain the nth to last element from this list. 
The approach use lots of memory maintaining a dual representation of the same data. 
An approach like this results in an extra O(n) space being allocated.
This means the method uses extra memory that grows with the size of the linked list. 
For example, if the list has 100 nodes, the approach will use space for 100 extra items. 
The space needed increases as the list gets longer, which is called O(n) space complexity.


```
def list_nth_last(linked_list, n):
  linked_list_as_list = []
  current_node = linked_list.head_node
  while current_node:
    linked_list_as_list.append(current_node)
    current_node = current_node.get_next_node()
  return linked_list_as_list[len(linked_list_as_list) - n]
```


```
def nth_last_node(linked_list, n):
  current = None
  tail_seeker = linked_list.head_node
  count = 1
  while tail_seeker:
    tail_seeker = tail_seeker.get_next_node()
    count += 1
    if count >= n + 1:
      if current is None:
        current = linked_list.head_node
      else:
        current = current.get_next_node()
  return current
```
