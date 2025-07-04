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


#### Modification of linear search function

A linear search can be modified so that all instances in which the target is found are returned.
This change can be made by not 'breaking' when the match is found.

_Linear search_

Linear search sequentially checks each element of a given list for the target value till match.

No match found -> perform the search on all the items in the list.

* _n_ - list length;
* _n-5_ - position of target;
* linear search checks totally _n-5_ items.


_Linear search as a part of complex searching problem_

#### Exceptions in Linear Search 

_Value Error_ -> target value is not found in a search list.


```python
def linear_search(records, match):
    for index in range(len(records)):
        if records[index] == match:
            return index
        else:
            raise ValueError(f"{match} not in a list of records")


data = [34, 25, 67, 97, 51]
item = 77

try:
    print(linear_search(data, item))
except ValueError as msg:
    print(f"{msg}")

```


_Linear Search Multiple Matches_

Linear search function may have more than 1 match from the input list.

In this case -> return list of indices (encountering every match in list).

In case of dis-match raise a ValueError.

```python
def linear_search(records, match):
    matches = []
    for index in range(len(records)):
        if records[index] == match:
            matches.append(index)
    if matches:
        return f"The matched values are stored at indexes: {matches}"
    else:
        raise ValueError(f"{match} not in list of records")


items = [0, 100, 10, 1000, 100]

print(linear_search(items, 100))

```


#### Brute Force Algorithms

Main idea -> go through all possible choices till solution is found.

Time of complexity is proportional to the input size -> algorithm is slow.


_Linear search cases_

_Best case_ (O(1)) -> matched item is at the beginning of the list;
_Worst case_ (O(N)) -> matched item is at the end of the list;
_Avg runtime_ -> Big-O runtime of O(N); halfway N/2.

Performance -> speed of performance decreases with the increasing the input size of data.
