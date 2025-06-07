#### Stacks

_Stack_ -> data structure following the protocoal _LIFO_ (last in first out).

_Stack size_ -> hosting numbers of nodes.

_Stack overflow_ -> pushing the node in a full stack which leads to crash.


Methods in stack:
* push() -> adds node to top of stack;
* pop() -> removes node from top of stack;
* peek() -> returns value of top node (without removal).

#### Implementation with Node class

- Store node -> top;
- Update it (node) with push()/pop().

```python
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


class Stack:
  def __init__(self, limit=1000):
    self.top_item = None
    self.size = 0
    self.limit = limit

  def has_space(self):
    return self.limit > self.size

  def push(self, value):
    if self.has_space():
      item = Node(value)
      item.set_next_node(self.top_item)
      self.top_item = item
      self.size += 1
    else:
      print("Out of space!")

  def pop(self):
    """
    assign to item_to_remove the top item;
    then, assign to top item the next value into the stack, because current is set to be removed;
    reduce the size of stack by 1 item;
    return the value of the removed item
    """

    if self.size > 0:
      item_to_remove = self.top_item
      self.top_item = item_to_remove.get_next_node()
      self.size = -1
      return item_to_remove.get_value()
    else:
      print("This stack is totally empty.")

  def peek(self):
    if self.size > 0:
      return self.top_item.get_value()
    print("The stack is empty.")

```
