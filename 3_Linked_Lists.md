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
