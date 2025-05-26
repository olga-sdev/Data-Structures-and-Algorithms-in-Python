#### Doubly Linked Lists Concept

_Doubly linked list_ consists of numbers of nodes.

Each node contains data and two references to the next and previous nodes in the list.

In a doubly linked list: set the node’s previous pointer and update the tail of the list if necessary.

_Adding to the head_

![Is there is a head in a list (1)](https://github.com/user-attachments/assets/b35e159d-0711-4608-ae80-ad2918e26a5b)


_Adding to the tail_

If the list is empty -> new node the head and tail of the list and set the pointers to null. 

If the list is not empty:
* Set the current tail’s next pointer to the new tail
* Set the new tail’s previous pointer to the current tail
* Set the new tail’s next pointer to null


_Removing from the list_

_Removing the head_
Updating the pointer at the beginning of the list -> set the previous pointer of the new head to null.

_Removing the tail_
Updating the pointer at the end of the list -> set the next pointer of the new tail to null.

_Removing from the middle of the list_:
* set the removed node’s preceding node’s next pointer to its following node.
* set the removed node’s following node’s previous pointer to its preceding node.


#### _Node Class and Constructor_

Doubly linked list -> the nodes have pointers to the previous node as well as the next node (head and tail):
* value;
* pointer to the previous node;
* pointer to the next node.

_Task_

1. Create an __init__() method (constructor) that only has self as a parameter, since each list will be empty when it’s created.
2. Inside your __init__() method create head_node and tail_node instance variables. The nodes have no value yet, so set them to None.

Doubly linked lists usecases:
* A music player with “next” and “previous” buttons;
* An app that shows you where your subway is on the train line;
* The “undo” and “redo” functionality in a web browser.

```
class Node:
  def __init__(self, value, next_node=None, prev_node=None):
    self.value = value
    self.next_node = next_node
    self.prev_node = prev_node
    
  def set_next_node(self, next_node):
    self.next_node = next_node
    
  def get_next_node(self):
    return self.next_node

  def set_prev_node(self, prev_node):
    self.prev_node = prev_node
    
  def get_prev_node(self):
    return self.prev_node
  
  def get_value(self):
    return self.value
    

class DoublyLinkedList:
  def __init__(self):
    self.head_node = None
    self.tail_node = None
```


_Adding to the Head_

_Task_
1. Define an .add_to_head() method that takes self and new_value as parameters.
Inside, create:
* A new_head Node that takes new_value as a parameter;
* A current_head Node that’s set to the list’s head.
2. If there is a current head to the list:
* Set current_head‘s previous node to new_head;
* Set new_head‘s next node to current_head.
Remember to use the Node class’s .set_prev_node() and .set_next_node() methods.
3. Outside of the if statement, set the list’s head to new_head.
4. Lastly, if the list doesn’t have a tail, set the list’s tail to the new head.

```
class Node:
  def __init__(self, value, next_node=None, prev_node=None):
    self.value = value
    self.next_node = next_node
    self.prev_node = prev_node
    
  def set_next_node(self, next_node):
    self.next_node = next_node
    
  def get_next_node(self):
    return self.next_node

  def set_prev_node(self, prev_node):
    self.prev_node = prev_node
    
  def get_prev_node(self):
    return self.prev_node
  
  def get_value(self):
    return self.value
    

class DoublyLinkedList:
  def __init__(self):
    self.head_node = None
    self.tail_node = None

  def add_to_head(self, new_value):
    new_head = Node(new_value)
    current_head = self.head_node

    if current_head != None:
      current_head.set_prev_node(new_head)
      new_head.set_next_node(current_head)
    
    self.head_node = new_head

    if self.tail_node is None:
      self.tail_node = new_head

```

_Adding to Tail_

Doubly linked have a tail property that avoid of iterating the list. In .add_to_head() method:

* Check the current tail in the list (list is _not empty_);
* If tail exists -> reset the pointers at the tail of the list:
- Set the current tail’s next node to the new tail
- Set the new tail’s previous node to the current tail
- Update the tail property to be the new tail
* If there isn’t a current head to the list (list is _empty_):
- Update the head property to be the new tail since that node will be both the head and tail

_Taks_
1. Define an .add_to_tail() method that takes self and new_value as parameters.
Inside, create:

* A new_tail Node that takes new_value as a parameter
* A current_tail Node that’s set to the list’s tail

2. If there is a current tail to the list:

* Set the current tail’s next node to new_tail
* Set new_tail‘s previous node to the current tail

3. Outside your if statement, set the list’s tail to the new_tail.

4. Lastly, if the list doesn’t have a head, set the list’s head to the new tail.

```python
class Node:
  def __init__(self, value, next_node=None, prev_node=None):
    self.value = value
    self.next_node = next_node
    self.prev_node = prev_node
    
  def set_next_node(self, next_node):
    self.next_node = next_node
    
  def get_next_node(self):
    return self.next_node

  def set_prev_node(self, prev_node):
    self.prev_node = prev_node
    
  def get_prev_node(self):
    return self.prev_node
  
  def get_value(self):
    return self.value
    

class DoublyLinkedList:
  def __init__(self):
    self.head_node = None
    self.tail_node = None
  
  def add_to_head(self, new_value):
    new_head = Node(new_value)
    current_head = self.head_node

    if current_head != None:
      current_head.set_prev_node(new_head)
      new_head.set_next_node(current_head)

    self.head_node = new_head

    if self.tail_node == None:
      self.tail_node = new_head

  def add_to_tail(self, new_value):
    new_tail = Node(new_value)
    current_tail = self.tail_node

    if current_tail != None:
      current_tail.set_next_node(new_tail)
      new_tail.set_prev_node(current_tail)

    self.tail_node = new_tail

    if self.head_node == None:
      self.head_node = new_tail

```


_Removing head_

Due to the added tail property, removing the head in a doubly linked list is different from a singly linked list:

* Check if there’s a current head to the list.
* If not (_list is empty_): method ends
* If yes (_list is not empty_): update the list’s head to be the _current head’s next node_
* If the updated head is not None (the list had > 1 element):
* Set the _head’s previous node_ -> None
* If the removed head == tail of the list (there was only 1 element in list):
* Call .remove_tail()
* Return the removed head’s value


_Taks_

1. Define a .remove_head() method that only takes self as a parameter. 
Inside, create a removed_head variable and set it to the list’s head node.
2. Check if removed_head has no value. 
If so, that means there’s nothing to remove, so return None to end the method.
3. Outside of if-statement, set the list’s head to removed_head‘s next node.
If the list still has a head, set its previous node to None, since the head of the list shouldn’t have a previous node.
4. Check if removed_head is equal to the list’s tail. 
If so, call the .remove_tail() method.
5. Return removed_head‘s value.

```python
class Node:
  def __init__(self, value, next_node=None, prev_node=None):
    self.value = value
    self.next_node = next_node
    self.prev_node = prev_node
    
  def set_next_node(self, next_node):
    self.next_node = next_node
    
  def get_next_node(self):
    return self.next_node

  def set_prev_node(self, prev_node):
    self.prev_node = prev_node
    
  def get_prev_node(self):
    return self.prev_node
  
  def get_value(self):
    return self.value
    

class DoublyLinkedList:
  def __init__(self):
    self.head_node = None
    self.tail_node = None
  
  def add_to_head(self, new_value):
    new_head = Node(new_value)
    current_head = self.head_node

    if current_head != None:
      current_head.set_prev_node(new_head)
      new_head.set_next_node(current_head)

    self.head_node = new_head

    if self.tail_node == None:
      self.tail_node = new_head

  def add_to_tail(self, new_value):
    new_tail = Node(new_value)
    current_tail = self.tail_node

    if current_tail != None:
      current_tail.set_next_node(new_tail)
      new_tail.set_prev_node(current_tail)

    self.tail_node = new_tail

    if self.head_node == None:
      self.head_node = new_tail

  def remove_head(self):
    removed_head = self.head_node

    if removed_head == None:
      return None

    self.head_node = removed_head.get_next_node()

    if self.head_node != None:
      self.head_node.set_prev_node(None)

    if removed_head == self.tail_node:
      self.remove_tail()

    return removed_head.get_value()
```


_Removing Tail_

Steps:

* Check current tail in the list.
* If Not (_list is empty_) -> method ends
* If Yes -> update the list’s tail -> current tail’s previous node
* If the updated tail is not None (the list had > 1 element):
* Set the tail’s next node -> None
* If the removed tail == head:
* Call .remove_head()
* Return the old tail’s data

1. Define a .remove_tail() method that only has self as a parameter. 
Inside, create a removed_tail variable and set it to the list’s tail.
2. Check if removed_tail has no value. If so, that means the list is empty and there’s nothing to remove, so return None to end the method.
3. Outside of your if, set the list’s tail to removed_tail‘s previous node.
If the list still has a tail (meaning that the list isn’t now empty), 
set the tail’s next node to None, since the tail of the list shouldn’t have a next node.
4. Check if removed_tail is equal to the list’s head. If so, call the .remove_head() method.
5. Finally, return removed_tail‘s value.

```python
class Node:
  def __init__(self, value, next_node=None, prev_node=None):
    self.value = value
    self.next_node = next_node
    self.prev_node = prev_node
    
  def set_next_node(self, next_node):
    self.next_node = next_node
    
  def get_next_node(self):
    return self.next_node

  def set_prev_node(self, prev_node):
    self.prev_node = prev_node
    
  def get_prev_node(self):
    return self.prev_node
  
  def get_value(self):
    return self.value
    

class DoublyLinkedList:
  def __init__(self):
    self.head_node = None
    self.tail_node = None
  
  def add_to_head(self, new_value):
    new_head = Node(new_value)
    current_head = self.head_node

    if current_head != None:
      current_head.set_prev_node(new_head)
      new_head.set_next_node(current_head)

    self.head_node = new_head

    if self.tail_node == None:
      self.tail_node = new_head

  def add_to_tail(self, new_value):
    new_tail = Node(new_value)
    current_tail = self.tail_node

    if current_tail != None:
      current_tail.set_next_node(new_tail)
      new_tail.set_prev_node(current_tail)

    self.tail_node = new_tail

    if self.head_node == None:
      self.head_node = new_tail

  def remove_head(self):
    removed_head = self.head_node

    if removed_head == None:
      return None

    self.head_node = removed_head.get_next_node()

    if self.head_node != None:
      self.head_node.set_prev_node(None)

    if removed_head == self.tail_node:
      self.remove_tail()

    return removed_head.get_value()

  def remove_tail(self):
    removed_tail = self.tail_node

    if removed_tail == None:
      return None

    self.tail_node = removed_tail.get_prev_node()

    if self.tail_node != None:
      self.tail_node.set_next_node(None)

    if removed_tail == self.head_node:
      self.remove_head()

    return removed_tail.get_value()
```
