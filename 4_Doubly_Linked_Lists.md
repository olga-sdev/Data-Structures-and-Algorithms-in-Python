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

_Removing by value_

Steps:

* Iterate through the list -> find the matching node
* If there is no matching element in the list:
* Return None
* If there is a matching node -> check if it is the head or tail of the list:
* If so -> call the corresponding .remove_head() or .remove_tail() method
* If not -> that means the node was somewhere in the middle of the list. In that case:
* Remove it by resetting the pointers of its previous and next nodes
* Return the node’s value property


_Task_
1. Define a .remove_by_value() method that takes self and value_to_remove as parameters.
Inside it, create a variable called node_to_remove. We don’t know what it is yet, so set it to None.
2. Create a current_node variable and set it equal to the list’s head. 
Then create a while loop that runs while current_node isn’t None.
Inside the loop, update current_node to be its next node. This is how we will iterate through the list as we look for the matching node.
3. Inside the while loop, but before you updated current_node to be its next node, 
create an if statement that checks if current_node‘s value matches the passed in value_to_remove. 
If it does, that means we have found the matching node.
Inside _if_:
Set node_to_remove to current_node
break to leave the while loop, since we don’t need to keep looking through the list
4. Outside your while loop, check if node_to_remove has any value. 
If it doesn’t, that means there was no matching node in the list, so return None to end the method.


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

    if current_head is not None:
      current_head.set_prev_node(new_head)
      new_head.set_next_node(current_head)

    self.head_node = new_head

    if self.tail_node is None:
      self.tail_node = new_head

  def add_to_tail(self, new_value):
    new_tail = Node(new_value)
    current_tail = self.tail_node

    if current_tail is not None:
      current_tail.set_next_node(new_tail)
      new_tail.set_prev_node(current_tail)

    self.tail_node = new_tail

    if self.head_node is None:
      self.head_node = new_tail

  def remove_head(self):
    removed_head = self.head_node

    if removed_head is None:
      return None

    self.head_node = removed_head.get_next_node()

    if self.head_node is not None:
      self.head_node.set_prev_node(None)

    if removed_head == self.tail_node:
      self.remove_tail()

    return removed_head.get_value()

  def remove_tail(self):
    removed_tail = self.tail_node

    if removed_tail is None:
      return None

    self.tail_node = removed_tail.get_prev_node()

    if self.tail_node is not None:
      self.tail_node.set_next_node(None)

    if removed_tail == self.head_node:
      self.remove_head()

    return removed_tail.get_value()
  
  def remove_by_value(self, value_to_remove):
    node_to_remove = None
    current_node = self.head_node

    while current_node is not None:
      if current_node.get_value == value_to_remove:
        node_to_remove = current_node
        break
      current_node = current_node.get_next_node()

    if node_to_remove is None:
      return None

```

_Resetting the pointers around the node_

There are three cases here:

* The node was the head of the list -> call .remove_head()
* The node was the tail of the list -> call .remove_tail()
* The node was somewhere in the middle of the list -> manually change the pointers for its previous and next nodes

1. Still in your .remove_by_value() method, check if node_to_remove is the list’s head. If so, call .remove_head().
2. Else if node_to_remove is the list’s tail, call .remove_tail().
3. Else, we know that the node is somewhere in the middle of the list. To remove it, we will need to reset the pointers for the nodes around it. 
In an else block, create:
* A next_node node that is equal to node_to_remove‘s next node
* A prev_node node that is equal to node_to_remove‘s previous node
4.Now that we have our nodes, we can remove the pointers to and from node_to_remove and have next_node and prev_node point to each other. 
Still in the else block:
* Set next_node‘s previous node to prev_node
* Set prev_node‘s next node to next_node
5. Finally, outside of the else block, return node_to_remove.

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

  def remove_by_value(self, value_to_remove):
    node_to_remove = None
    current_node = self.head_node

    while current_node is not None:
      if current_node.get_value() == value_to_remove:
        node_to_remove = current_node
        break

      current_node = current_node.get_next_node()

    if node_to_remove is None:
      return None

    if node_to_remove == self.head_node:
      self.remove_head()
    elif node_to_remove == self.tail_node:
      self.remove_tail()
    else:
      next_node = node_to_remove.get_next_node()
      prev_node = node_to_remove.get_prev_node()

      next_node.set_prev_node(prev_node)
      prev_node.set_next_node(next_node)
    
    return node_to_remove

```


_Use Cases_

1. We’re going to model a (fictional) subway line that will travel from Central Park to the Brooklyn Bridge.
At the bottom of script.py, outside the DoublyLinkedList class, create a new DoublyLinkedList named subway.
2. The subway starts at Central Park and winds its way downtown. In the following order:

Add "Times Square" to the head of the list
Add "Grand Central" to the head of the list
Add "Central Park" to the head of the list
Then print the list.

3.The subway continues from Times Square down to the Brooklyn Bridge. In the following order:

Add "Penn Station" to the tail of the list
Add "Wall Street" to the tail of the list
Add "Brooklyn Bridge" to the tail of the list
Then print the list again.

4. Oh no! There’s construction happening on the subway line: the Central Park and Brooklyn Bridge stops will temporarily be closed.
Remove them from your list without iterating through the entire list.
Then print the list again.

5. It turns out that the Times Square station is under construction as well. Remove it from the list, and then print the list for the last time.

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

  def remove_by_value(self, value_to_remove):
    node_to_remove = None
    current_node = self.head_node

    while current_node != None:
      if current_node.get_value() == value_to_remove:
        node_to_remove = current_node
        break

      current_node = current_node.get_next_node()

    if node_to_remove == None:
      return None

    if node_to_remove == self.head_node:
      self.remove_head()
    elif node_to_remove == self.tail_node:
      self.remove_tail()
    else:
      next_node = node_to_remove.get_next_node()
      prev_node = node_to_remove.get_prev_node()
      next_node.set_prev_node(prev_node)
      prev_node.set_next_node(next_node)

    return node_to_remove

  def stringify_list(self):
    string_list = ""
    current_node = self.head_node
    while current_node:
      if current_node.get_value() != None:
        string_list += str(current_node.get_value()) + "\n"
      current_node = current_node.get_next_node()
    return string_list

# Create your subway line here:
subway = DoublyLinkedList()
subway.add_to_head("Times Square")
subway.add_to_head("Grand Central")
subway.add_to_head("Central Park")

print(subway.stringify_list())

subway.add_to_tail("Penn Station")
subway.add_to_tail("Wall Street")
subway.add_to_tail("Brooklyn Bridge")

print(subway.stringify_list())

subway.remove_head()
subway.remove_tail()

print(subway.stringify_list())

subway.remove_by_value("Times Square")

print(subway.stringify_list())
```
