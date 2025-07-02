### Graphs and Graph Search

Implementation of Graphs:
* _Vertex_ class -> storage of connecting vertices (tops) with dict and adjustment of their edges;
* _Graph_ class -> builds upon _Vertex_ methods and allows addition of vertices (tops) and edges 
(setting the direction of edges) and determining the existence of the path between 2 vertices (tops).


```python
class Vertex:
    """Key methods of Vertex class (draft)"""
    def __init__(self, value):
        pass
    
    def add_edge(self, vertex, weight = 0):
        pass

    def get_edges(self):
        pass


class Graph:
    """Key methods of Graph class (draft)"""
    def __init__(self, directed = False):
        pass

    def add_vertex(self, vertex):
        pass

    def add_edge(self, from_vertex, to_vertex, weight = 0):
        pass

    def find_path(self, start_vertex, end_vertex):
        pass

```
