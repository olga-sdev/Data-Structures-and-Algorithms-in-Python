### Pattern Searching

_Naive pattern_ -> iterates over the text checking for a match: 
* match found -> records the index
* match not found -> moves to next position

_Naive pattern search runtime_:
* best case (pattern found early) -> O(n);
* worst case (pattern appears at the end / not appear) -> O(n^2).

```python
def pattern_search(text, pattern):
    for index in range(len(text)):
        match_count = 0
        for char in range(len(pattern)):
            if pattern[char] == text[index + char]:
                match_count += 1
            else:
                break
        if match_count == len(pattern):
            print(pattern, "found at index", index)


def pattern_search(text, pattern):
    if pattern in text:
        print(pattern, "found at index", text.index(pattern))
    else:
        return


def test_pattern_search(benchmark):
    benchmark(pattern_search, text='My name is Olga', pattern='Olga')


def test_pattern_search_2(benchmark):
    benchmark(pattern_search_2, text='My name is Olga', pattern='Olga')

```


![image](https://github.com/user-attachments/assets/ae15d92a-a05b-416a-b405-a065a3ce51f0)
