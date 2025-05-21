#### Nodes

_Nodes_ -> fundamental building blocks in data structures (linked lists / graphs / trees) which contains:
* _data_ (head);
* _reference_ to the _next node_ in the structure.

_Node’s data_ is specified when creating the node and immutable (can’t be updated).

_Reference_ is optional at initialization and can be updated.

_At the end of a node_ path, the _reference_ to the next node is _null_ (None) because there are no more nodes left.



_Task_
* Begin by creating a new class, Node. 
* Add an .__init__() method in the Node class that takes a value and an optional link_node (default should be None). 
* These should be saved to the corresponding self properties (self.value and self.link_node).

```
# Create the Node class below:
class Node:
  def __init__(self, value, link_node=None):
    self.value = value
    self.link_node = link_node
```


#### Nodes Python Getters
To access the data and link within the node with getters:
* .get_value()
* .get_link_node().

These should each return their corresponding value on the self object.

_Task_
* Implement the .get_value() getter in the Node class.

```
# Define your get_value and get_link_node methods below:
  def get_value(self):
    return self.value
```

* Implement the .get_link_node() getter in the Node class
```
 def get_link_node(self):
    return self.link_node
```
