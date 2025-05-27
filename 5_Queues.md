Concept of Queues: Conceptual

Queue -> data structure with ordered set of data.

3 methods for interaction:

* Enqueue - adds data to end of set;
* Dequeue - provides and removes data from the beginning of set;
* Peek - reveals data from the “front” of set without removal.

Queues are a First In, First Out -> _FIFO_ structure.

Queues can be implemented with linked list. 
The front of the queue -> head node of a linked list;
The back of the queue -> tail node.


_Bounded queue_ -> queue with limit on the amount of data that can be placed into it.

_Queue overflow_ -> attempting to enqueue data onto an already full queue.

_Queue underflow_ -> attempting to dequeue data from an empty queue.
