### Brute Force Algorithm

_Searching for smallest or largest value with liner search_

Linear search can be used to search for the smallest or largest value in an unsorted list rather than searching for a match.

_Linear Search best case_ -> when the target value = 1st element in a list => O(1)

_Linear Search complexity_ -> O(N) with n length of the list.
Runtime increases with the size of the list.


_Linear Search expressed as a Function_

Function compares each item of the _passed_ dataset with a _target_ value till match.


_Return value of a linear search_

A function that performs a linear search can return in case of success:
* prints message of success and 
* returns the index of the matched value

In case of failure -> returns -1.
