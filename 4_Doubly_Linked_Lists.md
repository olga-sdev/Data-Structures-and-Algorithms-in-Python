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
