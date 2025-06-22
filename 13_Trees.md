### Trees

_TreeNode_ - data structure that represents one entry of a tree, which is composed of multiple of such nodes.

The topmost node of tree is _root_.

Each node is associated with 1 parent node and may have numbers of sub-elements.


```python
class TreeNode:
    def __init__(self, val):
        self.val = val  # data
        self.sub_elements = []  # references to other nodes

    def add_sub_element(self, sub_element):
        print("Appending ", sub_element, " to ", self.val, " node")
        self.sub_elements.append(sub_element)

    def remove_sub_element(self, sub_element):
        print("Removing ", sub_element, " from ", self.val, " node")
        self.sub_elements = [sub for sub in self.sub_elements if sub is not sub_element]


tree_node = TreeNode(5)

tree_node.add_sub_element(8)
tree_node.add_sub_element(18)

print(tree_node.sub_elements)
print(tree_node.val)

tree_node.remove_sub_element(18)
print(tree_node.sub_elements)

"""
Appending  8 to 5  node
Appending  18 to 5  node
[8, 18]
5
Removing  18  from  5  node
[8]
"""

```

#### Wide and deep trees

_Wide_ tree -> plenty of sub-elements.

_Deep_ tree -> plenty of connections between elements and sub-elements with few siblings per node.

Tree can be wide and deep at the same time.


Each tree node stores a value and references to its child(ren) (sub-element(s)) node.

_Root_ is a not a child of any other node. Tree has only one root.


### Tree Traversal: Breadth-First Search and Depth-First Search

[Article](https://www.datacamp.com/tutorial/depth-first-search-in-python)

_Breadth-First Search_ - explores all nodes at the current depth level before changing to next level.

_DFS_(Depth-First Search) has time and space complexity of O(n) - used for problems where it's required to explore every possible solution.
Example: finding routes on map, which require exhaustive searches.


![dfs](https://github.com/user-attachments/assets/4f94ff1c-2cba-4525-ac4e-7840e66504b6)


[resources](https://media.datacamp.com/cms/google/ad_4nxdqny2bjweno0lenhhrcmnyy4l9bjmakduuls2jeo8vwkuskabdx40x2ws_s6ya8ntavuifypgnnunyh5xc5cfrqy2yuuhdmlgdjdpiumencenisogtlklljankmea4i-qgu61k5ibksdp5pixor3_tgfu.png)



#### DFS recursive implementation

DFS calls each node and sub-nodes till there are no more to visit.

```python
# Define the decision tree as a dictionary
tree = {
    'A': ['B', 'C'],
    'B': ['D', 'E', 'F'],
    'C': [],
    'D': [],
    'E': [],
    'F': []
}


def dfs_recursive(tree, node, visited=None):
    if visited is None:
        visited = set()  # init visited set
    
    visited.add(node)  # mark node with 'visited'
    print(node)
    
    for sub_element in tree[node]:
        if sub_element not in visited:
            dfs_recursive(tree, sub_element, visited)
            

dfs_recursive(tree, 'A')

"""
A
B
D
E
F
C
"""

```

#### Iterative DFS

For large decision trees, Python recursion depth limit can cause issues.

That is why it's better to implement DFS iteratively, using manually handling stack.

```python
tree = {
    'A': ['B', 'C'],
    'B': ['D', 'E', 'F'],
    'C': [],
    'D': [],
    'E': [],
    'F': []
}


def dfs_iterative(tree, start):
    visited = set()  # tracking the visited nodes
    stack = [start]  # stack for DFS

    while stack:  # while stack is full
        node = stack.pop()  # remove node from stack
        if node not in visited:
            visited.add(node)  # mark node with 'visited'
            print(node)
            stack.extend(reversed(tree[node]))  # add sub-elements to stack

dfs_iterative(tree, 'A')

"""
A
B
D
E
F
C
"""

```


#### Recursive DFS 

Pros:
* Simplicity: compact code
* Readability: comprehensive 
Cons:
* Recursion depth limit: for large graphs

#### Iterative DFS

Pros:
* No Recursion Limit: because of managing the stack manually 
Cons:
* More code: less intuitive, more configs
* Readability: the code is often more verbose


_Time complexity for DFS_

O(V+E):
* V - number of nodes;
* E - number of connections ('edges').

_Space complexity_

The space used in DFS depends on numbers of nodes the algorithm keeping track at any given moment.
