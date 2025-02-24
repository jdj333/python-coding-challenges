# Python Functions Comparison

This document provides a comparison of common Python functions, their brute force implementations, and custom efficient alternatives. It also specifies the data structures these functions operate on.

## Part 1: Frequently Used Functions

| Standard Function | Brute Force Function | Custom Efficient Function | Data Structure | Description |
|-------------------|----------------------|---------------------------|----------------|-------------|
| `sort()`          | ``` def brute_sort(lst): n = len(lst); for i in range(n): for j in range(0, n-i-1): if lst[j] > lst[j+1]: lst[j], lst[j+1] = lst[j+1], lst[j]; return lst``` | ``` def custom_sort(lst): if len(lst) <= 1: return lst; pivot = lst[len(lst) // 2]; left = [x for x in lst if x < pivot]; middle = [x for x in lst if x == pivot]; right = [x for x in lst if x > pivot]; return custom_sort(left) + middle + custom_sort(right)``` | List | Sorts a list in ascending order. |
| `len()`           | ``` def brute_len(lst): count = 0; for _ in lst: count += 1; return count``` | ``` def custom_len(lst): return sum(1 for _ in lst)``` | List, String | Returns the number of items in a list or characters in a string. |
| `sum()`           | ``` def brute_sum(lst): total = 0; for num in lst: total += num; return total``` | ``` def custom_sum(lst): return reduce(lambda x, y: x + y, lst)``` | List | Calculates the sum of elements in a list. |
| `max()`           | ``` def brute_max(lst): max_val = lst[0]; for num in lst: if num > max_val: max_val = num; return max_val``` | ``` def custom_max(lst): return reduce(lambda x, y: x if x > y else y, lst)``` | List | Returns the largest element in a list. |
| `min()`           | ``` def brute_min(lst): min_val = lst[0]; for num in lst: if num < min_val: min_val = num; return min_val``` | ``` def custom_min(lst): return reduce(lambda x, y: x if x < y else y, lst)``` | List | Returns the smallest element in a list. |
| `reversed()`      | ``` def brute_reversed(lst): return [lst[i] for i in range(len(lst)-1, -1, -1)]``` | ``` def custom_reversed(lst): return lst[::-1]``` | List | Reverses the order of elements in a list. |
| `enumerate()`     | ``` def brute_enumerate(lst): return [(i, lst[i]) for i in range(len(lst))]``` | ``` def custom_enumerate(lst): return zip(range(len(lst)), lst)``` | List | Adds a counter to an iterable, returning pairs of index and item. |
| `zip()`           | ``` def brute_zip(lst1, lst2): return [(lst1[i], lst2[i]) for i in range(min(len(lst1), len(lst2)))]``` | ``` def custom_zip(lst1, lst2): iter1, iter2 = iter(lst1), iter(lst2); while True: try: yield (next(iter1), next(iter2)); except StopIteration: return``` | List | Combines two lists into a list of tuples, pairing elements by index. |
| `map()`           | ``` def brute_map(func, lst): return [func(x) for x in lst]``` | ``` def custom_map(func, lst): return (func(x) for x in lst)``` | List | Applies a function to every item in an iterable. |
| `filter()`        | ``` def brute_filter(func, lst): return [x for x in lst if func(x)]``` | ``` def custom_filter(func, lst): return (x for x in lst if func(x))``` | List | Filters elements from a list that satisfy a condition. |
| `all()`           | ``` def brute_all(lst): for elem in lst: if not elem: return False; return True``` | ``` def custom_all(lst): return not any(not x for x in lst)``` | List | Returns True if all elements in an iterable are true. |
| `any()`           | ``` def brute_any(lst): for elem in lst: if elem: return True; return False``` | ``` def custom_any(lst): return not all(not x for x in lst)``` | List | Returns True if any element in an iterable is true. |
| `set()`           | ``` def brute_set(lst): result = []; [result.append(x) for x in lst if x not in result]; return result``` | ``` def custom_set(lst): seen = set(); return [x for x in lst if x not in seen and not seen.add(x)]``` | List | Removes duplicate elements from a list. |



## Part 2: Additional Functions

| Standard Function | Brute Force Function | Custom Efficient Function | Data Structure | Description |
|-------------------|----------------------|---------------------------|----------------|-------------|
| `range()`         | ``` def brute_range(start, end): return [i for i in range(start, end)]``` | ``` def custom_range(start, end): while start < end: yield start; start += 1``` | List | Generates a sequence of numbers within a given range. |
| `list()`          | ``` def brute_list(iterable): return [x for x in iterable]``` | ``` def custom_list(iterable): return list(iterable)``` | Iterable | Converts an iterable to a list. |
| `sorted()`        | ``` def brute_sorted(lst): return brute_sort(lst)``` | ``` def custom_sorted(lst): return sorted(lst)``` | List | Returns a sorted list from the elements of any iterable. |
| `unique()`        | ``` def brute_unique(lst): unique_list = []; for item in lst: if item not in unique_list: unique_list.append(item); return unique_list``` | ``` def custom_unique(lst): return list(set(lst))``` | List | Returns a list of unique elements. |
| `flatten()`       | ``` def brute_flatten(lst): flat_list = []; for sublist in lst: for item in sublist: flat_list.append(item); return flat_list``` | ``` def custom_flatten(lst): return [item for sublist in lst for item in sublist]``` | List | Flattens a list of lists into a single list. |
| `is_palindrome()` | ``` def brute_is_palindrome(s): return s == s[::-1]``` | ``` def custom_is_palindrome(s): return all(s[i] == s[~i] for i in range(len(s)//2))``` | String | Checks if a string reads the same forward and backward. |
| `fibonacci()`     | ``` def brute_fibonacci(n): a, b = 0, 1; fib = [a]; while b <= n: fib.append(b); a, b = b, a + b; return fib``` | ``` def custom_fibonacci(n): fib = [0, 1]; [fib.append(fib[-1] + fib[-2]) for _ in range(2, n)]; return fib[:n]``` | List | Generates Fibonacci sequence up to the nth number. |
| `gcd()`           | ``` def brute_gcd(a, b): while b: a, b = b, a % b; return a``` | ``` def custom_gcd(a, b): return a if b == 0 else custom_gcd(b, a % b)``` | Int | Calculates the greatest common divisor of two numbers. |
| `copy()`          | ``` def brute_copy(d): new_d = {}; for k, v in d.items(): new_d[k] = v; return new_d``` | ``` def custom_copy(d): return {k: v for k, v in d.items()}``` | Dict | Creates a shallow copy of a dictionary. |
| `find()`          | ``` def brute_find(s, sub): for i in range(len(s) - len(sub) + 1): if s[i:i+len(sub)] == sub: return i; return -1``` | ``` def custom_find(s, sub): return s.index(sub) if sub in s else -1``` | String | Finds the first occurrence of a substring in a string. |
| `count()`         | ``` def brute_count(s, sub): count = 0; for i in range(len(s) - len(sub) + 1): if s[i:i+len(sub)] == sub: count += 1; return count``` | ``` def custom_count(s, sub): return sum(1 for i in range(len(s) - len(sub) + 1) if s[i:i+len(sub)] == sub)``` | String | Counts the occurrences of a substring in a string. |
| `reverse()`       | ``` def brute_reverse(s): return s[::-1]``` | ``` def custom_reverse(s): return ''.join(reversed(s))``` | String | Reverses a string. |
| `split()`         | ``` def brute_split(s, sep): lst, word = [], ''; for char in s: if char == sep: lst.append(word); word = ''; else: word += char; lst.append(word); return lst``` | ``` def custom_split(s, sep): return s.split(sep)``` | String | Splits a string into a list using a separator. |
| `join()`          | ``` def brute_join(lst, sep): result = ''; for i, word in enumerate(lst): result += word; if i < len(lst) - 1: result += sep; return result``` | ``` def custom_join(lst, sep): return sep.join(lst)``` | List, String | Concatenates a list of strings into a single string with a separator. |


# Dictionary Functions

This document provides a comparison of common dictionary-related Python functions, their brute force implementations, and custom efficient alternatives. It also specifies the data structure these functions operate on.

## Dictionary Functions

| Standard Function | Brute Force Function | Custom Efficient Function | Data Structure | Description |
|-------------------|----------------------|---------------------------|----------------|-------------|
| `get()`           | ``` def brute_get(d, key, default=None): return d[key] if key in d else default``` | ``` def custom_get(d, key, default=None): try: return d[key] except KeyError: return default``` | Dict | Retrieves a value for a given key, returning a default value if the key is not present. |
| `keys()`          | ``` def brute_keys(d): return [key for key in d]``` | ``` def custom_keys(d): return list(d.keys())``` | Dict | Returns a list of all keys in a dictionary. |
| `values()`        | ``` def brute_values(d): return [d[key] for key in d]``` | ``` def custom_values(d): return list(d.values())``` | Dict | Returns a list of all values in a dictionary. |
| `items()`         | ``` def brute_items(d): return [(key, d[key]) for key in d]``` | ``` def custom_items(d): return list(d.items())``` | Dict | Returns a list of key-value pairs in a dictionary. |
| `update()`        | ``` def brute_update(d1, d2): for key, value in d2.items(): d1[key] = value``` | ``` def custom_update(d1, d2): d1.update(d2)``` | Dict | Updates a dictionary with key-value pairs from another dictionary. |
| `pop()`           | ``` def brute_pop(d, key, default=None): if key in d: value = d[key]; del d[key]; return value else: return default``` | ``` def custom_pop(d, key, default=None): return d.pop(key, default)``` | Dict | Removes a key from a dictionary and returns its value, or a default value if the key is not found. |

