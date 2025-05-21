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


