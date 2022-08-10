## Useful

*   **Python ord() function** returns the Unicode code from a given character. This function accepts a string of unit length as an argument and returns the Unicode equivalence of the passed argument.
*   For division
    *   Truncate toward zero: `int()`
    *   Round: `round()`
    *   Round up: `math.ceil()`
    *   Round down: `math.floor() or //`



## List tricks

*   ```python
    pair = [(p, s) for p, s in zip(position, speed)]
    pair.sort(reverse=True)
    # or 
    pair.sort(reverse=True)
    ```

*    [`list.sort()`](https://docs.python.org/3/library/stdtypes.html#list.sort) modifies the list in-place (and returns `None` to avoid confusion). Usually it’s less convenient than [`sorted()`](https://docs.python.org/3/library/functions.html#sorted) - **but if you don’t need the original list, it’s slightly more efficient.**

*   Another difference is that the [`list.sort()`](https://docs.python.org/3/library/stdtypes.html#list.sort) method is only defined for lists. In contrast, the [`sorted()`](https://docs.python.org/3/library/functions.html#sorted) function accepts any iterable.

    *   ```python
        >>> sorted({1: 'D', 2: 'B', 3: 'B', 4: 'E', 5: 'A'})
        [1, 2, 3, 4, 5]
        ```

*   Key:

    *   ```python
        >>> sorted("This is a test string from Andrew".split(), key=str.lower)
        ['a', 'Andrew', 'from', 'is', 'string', 'test', 'This']
        
        # Lambda
        >>> sorted(student_tuples, key=lambda student: student[2])   # sort by age
        [('dave', 'B', 10), ('jane', 'B', 12), ('john', 'A', 15)]
        ```

*   -

## Priority Queue

`from queue import PriorityQueue`

>   [queue — A synchronized queue class — Python 3.10.6 documentation](https://docs.python.org/3/library/queue.html#queue.PriorityQueue)

*   Insert: `.put(item, ...)`; $O(\log n)$
    *   just make a tuple of `(priority, thing)`
*   Pop: `.get()`;  $O(\log n)$
*   While end condition: `.empty()`

## Hash

### Hashmap / dict()

>   As of Python version 3.7, dictionaries are *ordered*. In Python 3.6 and earlier, dictionaries are *unordered*.
>
>   [Python - Dictionary Methods (w3schools.com)](https://www.w3schools.com/python/python_dictionaries_methods.asp)

*   Key, value: `.items()`

*   Key: `.keys()`

*   Value: `.values()`

*   **Insert:**

    *   `hashmap[key] = 1 + hashmap.get(key, 0)`
    *   `.get(key)`

*   Remove:

    *    `pop(key)`
    *   The `popitem()` method removes the last inserted item (in versions before 3.7, a random item is removed instead)
    *   The `del` keyword removes the item with the specified key name:

*   Sorting a Dictionary: `{k: incomes[k] for k in sorted(incomes)}`

*   Map:

    *   ```python
        def discount(current_price):
            return (current_price[0], round(current_price[1] * 0.95, 2))
        
        new_prices = dict(map(discount, prices.items()))
        ```

*   Filter:

    *   ```python
        def has_low_price(price):
            return prices[price] < 0.4
        
        low_price = list(filter(has_low_price, prices.keys()))
        ```

### Hashset / set()

>   A set is a collection which is *unordered*, **unchangeable**, and *unindexed*.
>
>   [Python - Set Methods (w3schools.com)](https://www.w3schools.com/python/python_sets_methods.asp)

*   Insert: `add(item)`
*   Remove:
    *   If the item to remove does not exist, `remove(item)` will raise an error.
    *   If the item to remove does not exist, `discard(item)` will **NOT** raise an error.
    *   You can also use the `pop()` method to remove an item, but this method will remove the *last* item. Remember that sets are unordered, so you will not know what item that gets removed.



## [`collections`](https://docs.python.org/3/library/collections.html#module-collections) — Container datatypes

### `defaultdict` ///

*   ```python
    s = [('yellow', 1), ('blue', 2), ('yellow', 3), ('blue', 4), ('red', 1)]
    d = defaultdict(list)
    for k, v in s:
        d[k].append(v)
        
    ######################
    
    d = {}
    for k, v in s:
        d.setdefault(k, []).append(v)
    
    sorted(d.items())
    
    ```

    *   When each key is encountered for the first time, it is not already in the mapping; so an entry is automatically created using the [`default_factory`](https://docs.python.org/3/library/collections.html#collections.defaultdict.default_factory) function which returns an empty [`list`](https://docs.python.org/3/library/stdtypes.html#list).

*   ```python
    s = 'mississippi'
    d = defaultdict(int)
    for k in s:
        d[k] += 1
    
    sorted(d.items())
    # [('i', 4), ('m', 1), ('p', 2), ('s', 4)]
    ```

*   