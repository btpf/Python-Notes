# Python Notes (For Competitive Programming)
[toc]





https://www.bigocheatsheet.com/

https://wiki.python.org/moin/TimeComplexity

TODO:

- [ ] Add string formatting. As well as "%" for decimal formatting.

---



### Comprehensions

#### Dictionary Comprehension

https://www.programiz.com/python-programming/dictionary-comprehension

```python
dictionary = {key: value for variable in variables}
```

or

```python
dictionary = {key: value for (item, value) in dictionary.items()}
```

#### List Comprehension

https://www.w3schools.com/python/python_lists_comprehension.asp



```python
newlist = [(Expression) for x in range(5) [Condition]]

newlist = [x for x in range(5)]
# [0, 1, 2, 3, 4]
newlist = [x*2 for x in range(5)]
# [0, 2, 4, 6, 8]

newlist = [x*2 for x in range(5) if x < 3]
# [0, 2, 4]

# It is common to also see ternaries 

newlist = [x*2 if x != 2 else 10 for x in range(10) if x < 5]

#[0, 2, 10, 6, 8]

# Multiple If's can be used, which gets treated as the and operator
newlist = [(x*2 if x != 2 else 10) for x in range(10) if x < 5 if x*2 < 7]

#equivalent to
newArray = []
for x in range(10):
    if(x < 5 and x*2 < 7):
        if(x != 2):
            newArray.append(x*2)
        else:
            newArray.append(10)

#[0, 2, 10, 6]

```

### Helper Classes

#### Enumarate

Adds Index to every item in a list

Usage:

```python
seasons = ["Spring", "Summer", "Fall", "Winter"]
newList = enumerate(seasons)
print(list(newList))
// [(0, 'Spring'), (1, 'Summer'), (2, 'Fall'), (3, 'Winter')]
```



#### Counter

https://stackoverflow.com/a/3496860

https://docs.python.org/3/library/collections.html#collections.Counter

```python
from collections import Counter

# Use a string or array as an argument
Counter("mississippi")
Counter({'i': 4, 's': 4, 'p': 2, 'm': 1})
```

This can be converted to a dict directecly



### Iteratools (Combination & Permutation)

https://realpython.com/python-itertools



##### Permutation

```python

# A Python program to print all
# permutations of given length
from itertools import permutations
 
# Get all permutations of length 2
# and length 2
perm = permutations([1, 2, 3], 2)

# Print the obtained permutations
for i in list(perm):
    print (i)
  
'''
(1, 2, 3)
(1, 3, 2)
(2, 1, 3)
(2, 3, 1)
(3, 1, 2)
(3, 2, 1)
'''
```

##### Combination

```python

# A Python program to print all
# combinations of given length
from itertools import combinations
 
# Get all combinations of [1, 2, 3]
# and length 2
comb = combinations([1, 2, 3], 2)
 
# Print the obtained combinations
for i in list(comb):
    print (i)
'''
(1, 2)
(1, 3)
(2, 3)
'''
```





### String Manipulation

##### find

`str.find(sub[, start[, end]] )`

The `find()` method returns an integer value:

- If the substring exists inside the string, it returns the index of the first occurence of the substring.
- If a substring doesn't exist inside the string, it returns **-1**.

##### Substring

```python
str = "Hello World"
print(str[0:5])
# "Hello"

# Implicitely equivalent
print(str[:5])
# "Hello"

#Also the other way
print(str[6:])
# "World"
```

##### Remove Last Character using Substrings

```python
str = "Hello World"
print(str[:-1])
"Hello Worl"
```



##### Reverse Strings

```python
str = "Hello World"
print(str[::-1])
# "dlroW olleH"
```



##### Strip

.Strip() will remove any leading and trailing characters that are defined.
If none are defined, it will default to a single space

```python
" Hello World  ".strip()
# "Hello World"

"dd  fd Hello World df  ".strip("df ")
# "Hello World"
```

##### Convert Array To String

```python
''.join([1,2,3])
# "123"
```



#### String Format

https://thepythonguru.com/python-string-formatting/

https://realpython.com/python-string-formatting/#1-old-style-string-formatting-operator



### Map

The map function returns an iterator type

```python
print(list(map(lambda x: str(x), [7,10,7])))
# ['7', '10', '7']


numbers1 = [1, 2, 3]
numbers2 = [4, 5, 6]
  
result = map(lambda x, y: x + y, numbers1, numbers2)
print(list(result))
# [5, 7, 9]
```

### Zip

https://www.programiz.com/python-programming/methods/built-in/zip

Usage:

```python
zip(*iterables)
```

`iterables` can be built-in iterables (like: list, string, dict), or user-defined iterables

Example:

```python
languages = ['Java', 'Python', 'JavaScript']
versions = [14, 3, 6]

zip(languages, versions)

# Output: [('Java', 14), ('Python', 3), ('JavaScript', 6)]

zip('abc', '123', 'xyz00000')
# [('a', '1', 'x'), ('b', '2', 'y'), ('c', '3', 'z')]
#Note 'xyz00000' has more characters than the others, so they are removed
```



### Data Structure



#### Python Sets

A set in python is implemented as a hash table.

https://stackoverflow.com/a/44080017

https://docs.python.org/2/library/sets.html

https://wiki.python.org/moin/BitwiseOperators

##### Creating Set

```python
mySet = set()
myset = set({"item1","item2"})
```
##### Methods:

The `_update` methods will update the original set that the method is called on.

| Method                           | Big O        | Description                                               |
| -------------------------------- | ------------ | --------------------------------------------------------- |
| .add(`x`)                        | O(1)         | adds element `x` to set                                   |
| .update(`t`)                     | O(t)         | adds set `t` to the set                                   |
| .discard(`x`)                    | O(1)         | removes `x` from set if present                           |
| .intersection_update(t, t2, ...) | O(min(n, m)) | modifies set *s* keeping only elements also found in `t`  |
| .difference_update(t)            |              | return set *s* after removing elements found in `t`       |
| .symmetric_difference_update(t)  |              | return set *s* with elements from *s* or *t* but not both |

##### Example

```python
set1 = {1,2,3,4}
set2 = {2,3,4,5}

# Both of these are equivalent
# They return the intersection of two sets as a new set
# This uses bitwise AND
print(set1.intersection(set2)) # {2,3,4}
print(set1 & set2) # {2,3,4}

print(set2 - set1) # {5}
print(set1-set2) # {1}
# Same as above but updates set1
set1.difference_update(set2)
print(set1)

# Or/difference between set1 and set 2
# Using Bitwise Exclusive OR
print(set1 ^ set2) # {1,5}
# This is equivalent to the above, except it modified set1
set1.symmetric_difference_update(set2)
print(set1)

# Union set1 and set2
# Using Bitwise OR
print(set1 | set2) # {1, 2, 3, 4, 5}

for item in set1:
    print(item)

```

#### Python Tuples

Tuples are ordered and immutable lists

##### Creating Tuples

```python
myTuple = tuple()
myTuple = tuple((1,))
myTuple = tuple((1,2,3))
```

##### Example

```python
# Quirk of tuples
# If it is of size 1, it must contain a comma to disambiguate from a normal number in parentheses
myTuple = tuple((1,))


myTuple = tuple("Apple", "Cheese", "Pie")
print(myTuple[1]) # "Cheese"
```

#### Python List



##### Creating List

```python
mylist = [1,2,3]
mylist = list((1,2,3))
```

##### Spread (Called Splat) operator

https://stackoverflow.com/questions/2322355/proper-name-for-python-operator

```python
f = [1,2,3]
s = [4,5,6]
print([*f, *s])
# [1, 2, 3, 4, 5, 6]
```



##### Slicing Array

```python
A = [1,2,3,4,5,6]
C = A[2:4]
# [3,4]
```



##### Sorting Array

```python
nums = [1, 2, 3]
# Ascending by default

# reverse=True sorts in descending
nums.sort(reverse=True)

# [3, 2, 1]
print(nums)

```



##### Sorting With Key

```python
nums = [[1,4],[4,5]]

nums.sort(key = lambda i: i[0])
```





##### Bisect Array

```python
A = [1,2,3,4,5,6]
B = A[:len(A)//2]
C = A[len(A)//2:]
print(B)
print(C)
'''
[1, 2, 3]
[4, 5, 6]
'''
```



##### Example

```python
myList = ["Apple", "Cheese", "Pie"]

# Loop through using Key value enumerator
for num, name in enumerate(myList):
    print("{}: {}".format(num, name))
    
for index in range(0, len(myList)):
    print("{}: {}".format(index, myList[index]))

for item in myList:
	print(item)
```





#### Python Dictionaries

##### Example

```python
Employee = {
  "age": 28,
  "name": 'abc',
  "designation": 'developer'
}

for (key, value) in Employee.items():
    print('{} :  {}'.format(key, value))

dictOfNames = {
   7 : 'sam',
   8: 'john',
   9: 'mathew',
   10: 'riti',
   11 : 'aadi',
   12 : 'sachin'
}
# Filter all elements that dont have a value with an 'a' in it
newDict = dict(filter(lambda elem: elem[1].count('a') > 0, dictOfNames.items()))
print(newDict)
```

##### .get(key [, Default Value])



```python
dict[key] = dict.get(key[, value]) +1
```



https://www.programiz.com/python-programming/methods/dictionary/get

Safely increment a value without knowing if key exists

```python
counts = dict()
for i in items:
  counts[i] = counts.get(i, 0) + 1
```



#### Default Dictionary

A default dictionary is a dictionary where each key corresponds to a predefined type. This can be a primal or an object

```python
import collections
dds = collections.defaultdict(set)
dds[4].add("hi") # Using the fact that it is already a set.
```

https://stackoverflow.com/questions/5900578/how-does-collections-defaultdict-work

The defaultDict can also take a function to set the value

#### Ordered Dictionary

https://www.geeksforgeeks.org/ordereddict-in-python/

A default dictionary will not keep the order of the elements. However, an ordered will.

```python
from collections import OrderedDict
od = OrderedDict()
od['a'] = 1
od['b'] = 2
# Or use the following syntax for instantiation
od = OrderedDict({
    "a": 1,
    "b": 2
})
```

##### Example

This compares the normal dict to the ordered

```python
from collections import OrderedDict
 
d = {'a': 1, 'b': 2, 'c': 3, 'd': 4}

print("This is a Dict:\n")
for key, value in d.items():
    print(key, value)
"""
This is a Dict:
a 1
c 3
b 2
d 4
"""

od = OrderedDict({'a': 1, 'b': 2, 'c': 3, 'd': 4})

print("\nThis is an Ordered Dict:\n") 
for key, value in od.items():
    print(key, value)
  
"""
This is an Ordered Dict:
a 1
b 2
c 3
d 4
"""

```





#### Heapq (Priority Queue)

https://docs.python.org/3/library/heapq.html
Underneath, this is a min-binary heap. In order to make this priority queue use the max priority instead of the minimum, multiply each priority by `-1`

Note:

- s_roll[0] will be the smallest element
- Arrays and tuples work and will be sorted on indice 0

##### Methods

Runtime: https://stackoverflow.com/a/38833175

The `_update` methods will update the original set that the method is called on.

| Method                                | Big O    | Description                                                  |
| ------------------------------------- | -------- | ------------------------------------------------------------ |
| heapq.heappush(`array`, `tuple item`) | O(log n) | Push the value *item* onto the *heap*, maintaining the heap invariant. |
| heapq.heappop(`array`)                | O(log n) | Pop and return the smallest item from the *heap*,  <br />maintaining the heap invariant. <br />If the heap is empty, [`IndexError`](https://docs.python.org/3/library/exceptions.html#IndexError) is raised. <br />To access the smallest item without popping it, use `heap[0]`. |
| heapq.heapify(`x`)                    | O(n)     | Transform list *x* into a heap, in-place, in linear time.    |
|                                       |          |                                                              |

##### Basic Example

```python
import heapq
qlist = [[2,"earth"],[3,"world"], [1,"hello"]]
heapq.heapify(qlist)
# Pop 'hello'
print(heapq.heappop(qlist))
# peek "earth"
print(qlist[0])

heapq.heappush(qlist, [5, "Welcome"])
```

##### Example

```python
# Python code to find 3 largest and 4 smallest
# elements of a list.
import heapq
  
grades = [110, 25, 38, 49, 20, 95, 33, 87, 80, 90]
print(heapq.nlargest(3, grades))
print(heapq.nsmallest(4, grades))
```



##### Example

```python
import heapq

s_roll = []
# priority + name
dictOfNames = {
   7 : 'sam',
   8: 'john',
   9: 'mathew',
   10: 'riti',
   11 : 'aadi',
   12 : 'sachin'
}

# Add each of the dictionary items in (Priority, value)
for (key, item) in dictOfNames.items():
    heapq.heappush(s_roll, (key,item))
# HeapPop Them
while s_roll:
    deque_r = heapq.heappop(s_roll)
    print(deque_r)

# Example with max number first
s_roll = []
# priority + name
dictOfNames = {
   7 : 'sam',
   8: 'john',
   9: 'mathew',
   10: 'riti',
   11 : 'aadi',
   12 : 'sachin'
}

# Add each of the dictionary items in (Priority, value)
for (key, item) in dictOfNames.items():
    heapq.heappush(s_roll, (-1 * key,item))
# HeapPop Them
while s_roll:
    deque_r = heapq.heappop(s_roll)
    print((-1 * deque_r[0], deque_r[1]))
```

#### PriorityQueue

https://docs.python.org/3/library/queue.html

```python
#Initialize
from queue import PriorityQueue
q = PriorityQueue()
# Add item to queue
q.put((1, '1'))
# Peek item
print(q.queue[0])
# Pop top item
print(q.get())
# Check if empty
print(q.empty())
```



#### Deque

https://docs.python.org/3/library/collections.html#collections.deque

Deque = Stack + Queue

##### Creating Deque

```python
from collections import deque
queue = deque([iterable[, maxlen]])
```

##### Methods:

| Method        | Big O | Description                                                  |
| ------------- | ----- | ------------------------------------------------------------ |
| append(x)     | O(1)  | Add x to the right side of the deque.                        |
| appendleft(x) | O(1)  | Add x to the left side of the deque.                         |
| pop()         | O(1)  | Remove and return an element from the right side of the deque. <br />If no elements are present, raises an `IndexError`. |
| popleft()     | O(1)  | Remove and return an element from the right side of the deque.<br /> If no elements are present, raises an `IndexError`. |
| rotate(`n=1`) | O(2n) | Rotate the deque n steps to the right. If n is negative, rotate to the left.<br />When the deque is not empty, rotating one step to the right is equivalent to `d.appendleft(d.pop())`, and rotating one step to the left is equivalent to `d.append(d.popleft())`. |



```python
from collections import deque
d = deque()
d.append(1) # [1]
d.append(2) # [1,2]
d.append(3) # [1,2,3]
print(list(d)) # [1,2,3]
d.pop() # 3
d.popLeft() # 1
print(len(d)) # 1

```

---

#### Sorted Containers

This is a 3rd party module. Although my python installation seemed to have it (I don't remember installing it), I do not think it is included with the standard python install.

Documentation: https://grantjenks.com/docs/sortedcontainers/

Leetcode allowing it: https://leetcode.com/discuss/general-discussion/351534/python-sortedcontainers
Leetcode Discussion: https://leetcode.com/discuss/general-discussion/617447/can-i-use-python-sortedcontainers-in-interviews

Geeks for Geeks Tutorial: https://www.geeksforgeeks.org/python-sorted-containers-an-introduction/

##### SortedList

https://grantjenks.com/docs/sortedcontainers/sortedlist.html

###### Usage:

| Function                                | Description                                                  | Runtime                    |
| --------------------------------------- | ------------------------------------------------------------ | -------------------------- |
| `__init__`(*iterable=None*, *key=None*) | Initialize sorted list instance.                             | *O(n\*log(n))*             |
| `add`(*value*)                          | Add value to sorted list.                                    | O(log(n)) – approximate.   |
| `update`(*iterable*)                    | Update sorted list by adding all values from iterable.       | O(k*log(n)) – approximate. |
| `clear`()                               | Remove all values from sorted list.                          | *O(n)*                     |
| `discard`(*value*)                      | Remove value from sorted list if it is a member.             | O(log(n)) – approximate.   |
| `pop`(*index=- 1*)                      | Remove and return value at index in sorted list.<br />Raise `IndexError` if the sorted list is empty or index is out of range.<br />Negative indices are supported. | O(log(n)) – approximate.   |
| `bisect_left`(*value*)                  | Return an index to insert value in the sorted list.<br />If the value is already present, the insertion point will be before (to the left of) any existing values. | O(log(n)) – approximate.   |
| `bisect_right`(*value*)                 | Return an index to insert value in the sorted list.<br />Similar to bisect_left, but if value is already present, the insertion point will be after (to the right of) any existing values. | O(log(n)) – approximate.   |
| `count`(*value*)                        | Return number of occurrences of value in the sorted list.    | O(log(n)) – approximate.   |

###### Example

```python
from sortedcontainers import SortedList
sl = SortedList([3, 1, 2, 5, 4])
print(sl)
#>> SortedList([1, 2, 3, 4, 5])

```

##### SortedDict

Sorted dict is a sorted mutable mapping.

Sorted dict keys are maintained in sorted order. The design of sorted dict is simple: sorted dict inherits from dict to store items and maintains a sorted list of keys.

Sorted dict keys must be hashable and comparable. The hash and total ordering of keys must not change while they are stored in the sorted dict.



###### Example

```python
from sortedcontainers import SortedDict
sd = SortedDict()
SortedDict({'b': 2, 'e': 5})
sd.update({'d': 4, 'c': 3})
```

##### SortedSet

https://grantjenks.com/docs/sortedcontainers/sortedset.html

###### Usage:

| Function                                | Description                                      | Runtime                  |
| --------------------------------------- | ------------------------------------------------ | ------------------------ |
| `__init__`(*iterable=None*, *key=None*) | Initialize sorted set instance.                  | *O(n\*log(n))*           |
| `__contains__`(*value*)                 | Used as `if item in sortedSet`                   | *O(1)*                   |
| `add`(*value*)                          | Add value to sorted set.                         | O(log(n)) – approximate. |
| `discard`(*value*)                      | Remove value from sorted list if it is a member. | O(log(n)) – approximate. |
| `__getitem__`(*index*)                  | Used as `sortedSet[2]` or `sortedSet[2:5]`       | O(log(n)) – approximate. |

###### Example

```python
from sortedcontainers import SortedSet
ss = SortedSet()
ss.add(3)
ss.add(1)
ss.add(2)
print(ss)
#>> SortedSet([1, 2, 3])
```



### Bisect

https://docs.python.org/3/library/bisect.html

Taken from: https://xwu64.github.io/2020/04/24/Most-Commonly-Used-Python-Data-Structures-that-are-NOT-built-in/

```python
a = list
x = num
import bisect
bisect.bisect_left(a, x, lo=0, hi=len(a))  # Return the insertion point for x in a to maintain sorted order. If x is already present in a, return the left most position
bisect.bisect_right(a, x, lo=0, hi=len(a))  # Return the insertion point for x in a to maintain sorted order. If x is already present in a, return the right most position
bisect.bisect(a, x, lo=0, hi=len(a))  # same as bisect_right
bisect.insort_left(a, x, lo=0, hi=len(a))  # Insert x in a in sorted order
bisect.insort_right(a, x, lo=0, hi=len(a)) 
bisect.insort(a, x, lo=0, hi=len(a))  # same as insort_right
```



### Formulas

#### Array

##### Allocating 2D Array

How to generate the array properly:

```python
a = [[0 for x in range(columns)] for y in range(rows)]
```



**DO NOT** do this

```python
newMatrix = [[0] * 3] * 3
print(newMatrix)
newMatrix[0][1] = 5
print(newMatrix)

```

```
[[0, 0, 0], [0, 0, 0], [0, 0, 0]]
[[0, 5, 0], [0, 5, 0], [0, 5, 0]]
```

https://stackoverflow.com/a/44382900

##### Transpose Array

```python
transposed = [[row[i] for row in T] for i in range(len(T[0]))]
```

#### String

##### Get all rotations of string

```python
for i in range(1, len(word) + 1):
    seenSet.add(word[i:] + word[:i])
```

#### Dictionary

##### Dictionary Updating (Safely)

```python
dict[key] = dict.get(key[, value]) +1
```





#### Misc Shortcuts

##### Quick Comparison

In python 2, There used to be a function called cmp(a,b) (Compare)

cmp(a,b)

Returns:
-1 if a<b

0 if a=b

1 if a>b

To implement this in python 3, we can use the following

```python
(a > b) - (a < b)
```

#### Swapping Values

Typically when swapping variables in other languages, you would use a temp variable as so

```python
temp = root.left
root.left = root.right
root.right = temp
```

But in python, you could do this swap in one operation

```python
root.left, root.right = root.right,root.left
```



## Resources

https://xwu64.github.io/2020/04/24/Most-Commonly-Used-Python-Data-Structures-that-are-NOT-built-in/

Big O - https://leetcode.com/discuss/study-guide/2122306/python-cheat-sheet-for-leetcode

From: https://leetcode.com/discuss/general-discussion/459791/Special-data-structures-in-Python

### `enumerate`



[Documentation](https://docs.python.org/3/library/functions.html#enumerate) You want to track both the index and element when iterating through the array.



```
arr = [3,1,4,1,5,9,2,6,5,3,5,9]
for i in range(len(arr)):
  arr[i] = arr[i] + i

arr # [3, 2, 6, 4, 9, 14, 8, 13, 13, 12, 15, 20]
```



You can use `enumerate` instead



```
arr = [3,1,4,1,5,9,2,6,5,3,5,9]
for i,ar in enumerate(arr):
  arr[i] = ar + i

arr # [3, 2, 6, 4, 9, 14, 8, 13, 13, 12, 15, 20]
```



The benefit is to avoid the use of awkward `range(len())`. Moreover, without the need to use `arr[i]` in the loop you can reduce the nesting and make the code clearer.
