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


#### Nodes Python Setters
Value is set when the Node is create.

Link_node is set and updated with setter.

_Task_
* Implement the .set_link_node() setter in the Node class.
```
  # Define your set_link_node method below:
  def set_link_node(self, link_node):
    self.link_node = link_node
```

#### Python Nodes Review
_Task_

1. Outside of Node, instantiate three nodes. None have an argument for link_node:
* the first has a value of "likes to yak" and be assigned to a variable yacko
* the second has a value of "has a penchant for hoarding snacks" and be assigned to wacko
* the third has a value of "enjoys spending time in movie lots" and be assigned to dot

```
class Node:
  def __init__(self, value, link_node=None):
    self.value = value
    self.link_node = link_node
    
  def set_link_node(self, link_node):
    self.link_node = link_node
    
  def get_link_node(self):
    return self.link_node
  
  def get_value(self):
    return self.value

# Add your code below:
yacko = Node("likes to yak")
wacko = Node("has a penchant for hoarding snacks")
dot = Node("enjoys spending time in movie lots")
```

2. Now let’s give these nodes some responsibilities!
yacko can keep track of dot and dot can keep up with wacko.
wacko can’t keep track of anything though.

Below the newly created nodes, use your .set_link_node() method to give:
* yacko a link_node of dot
* dot a link_node of wacko

```
class Node:
  def __init__(self, value, link_node=None):
    self.value = value
    self.link_node = link_node
    
  def set_link_node(self, link_node):
    self.link_node = link_node
    
  def get_link_node(self):
    return self.link_node
  
  def get_value(self):
    return self.value

# Add your code below:
yacko = Node("likes to yak")
wacko = Node("has a penchant for hoarding snacks")
dot = Node("enjoys spending time in movie lots")

yacko.set_link_node(dot)
dot.set_link_node(wacko)
```

3. Create two new variables, dots_data, and wackos_data.
Use both getter methods to get dot‘s value from yacko and get wacko‘s value from dot.
Print dots_data and wackos_data to the console to see the results.

```
class Node:
  def __init__(self, value, link_node=None):
    self.value = value
    self.link_node = link_node
    
  def set_link_node(self, link_node):
    self.link_node = link_node
    
  def get_link_node(self):
    return self.link_node
  
  def get_value(self):
    return self.value

# Add your code below:
yacko = Node("likes to yak")
wacko = Node("has a penchant for hoarding snacks")
dot = Node("enjoys spending time in movie lots")

yacko.set_link_node(dot)
dot.set_link_node(wacko)

dots_data = yacko.get_link_node().get_value()

wackos_data = dot.get_link_node().get_value()

print(dots_data) 
print(wackos_data)
```

Explanation yacko.get_link_node().get_value() order:

* yacko.get_link_node() -> gets the node that yacko is linked to, which is dot.
* .get_value() -> gets the value stored in the dot node.

