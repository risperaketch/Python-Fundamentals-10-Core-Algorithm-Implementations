# Python Fundamentals — 10 Core Algorithm Implementations

> 10 Python utility functions built from scratch using core language features only — no external libraries. Covers number theory, string analysis, list processing, data cleaning, and statistics.

---

## Overview

This project implements 10 foundational Python algorithms that form the building blocks of data analytics and software engineering. Each function is written from first principles, fully documented with NumPy-style docstrings, annotated with time complexity, and demonstrated with a professional visualization.

---

## Functions

| # | Function | Category | Algorithm | Complexity |
|---|---|---|---|---|
| 1 | `is_even` | Number Theory | Modulo operator `% 2` | O(1) |
| 2 | `sum_even` | List Processing | Filter + `sum()` | O(n) |
| 3 | `get_largest_odd` | Mixed-Type Filtering | `isinstance()` + `max()` | O(n) |
| 4 | `get_vowels` | String Analysis | Generator expression + `sum()` | O(n·m) |
| 5 | `get_words_with_a` | String Filtering | Substring membership `'a' in word` | O(n·m) |
| 6 | `remove_dups` | Data Cleaning | `set` for O(1) lookup · `.lower()` normalization | O(n) avg |
| 7 | `is_prime` | Number Theory | Trial division up to √n | O(√n) |
| 8 | `get_factorial` | Combinatorics | Iterative multiplication | O(n) |
| 9 | `reverse_string` | String Manipulation | Extended slice `[::-1]` | O(n) |
| 10 | `get_mode` | Statistics | Frequency dict + max-count check | O(n) |

---

## Function Reference

### `is_even(num)` → `bool`
Returns `True` if `num` is even, `False` otherwise. Uses the modulo operator: a number is even when `num % 2 == 0`. O(1) — constant time regardless of input magnitude.

```python
is_even(4)   # True
is_even(7)   # False
is_even(0)   # True  (zero is even by definition)
```
<img width="1198" height="319" alt="image" src="https://github.com/user-attachments/assets/20b3b566-b392-446e-9004-b9e0be73264e" />
Numbers 1–12 colour-coded Even/Odd

### `sum_even(list_nums)` → `int`
Sums all even integers in a list. Collects even values into a buffer list, then returns `sum()`. Returns `0` if no even numbers are present.

```python
sum_even([2, 3, 5, 8])              # 10  (2 + 8)
sum_even([5, 4, 3, 2, 10, 8, 25, 30])  # 54  (4 + 2 + 10 + 8 + 30)
```
<img width="978" height="373" alt="image" src="https://github.com/user-attachments/assets/829e55ee-1faf-4c85-854f-2128d485be1f" />
Bar chart of even (summed) vs. odd (skipped) values


### `get_largest_odd(list_num_str)` → `int | None`
Finds the largest odd integer in a mixed list of integers and strings. Uses `isinstance(item, int)` to safely skip string entries without raising `TypeError`. Returns `None` if no odd integers are found.

```python
get_largest_odd([3, 101, 'NJ', 5, 8, 10, 'marina'])  # 101
get_largest_odd([2, 4, 'hello'])                       # None
```
<img width="1088" height="373" alt="image" src="https://github.com/user-attachments/assets/b436ab25-6084-4634-ba51-d3728baec1b2" />
Mixed list — odd integers, even integers, and strings shown separately


### `get_vowels(list_str)` → `dict`
Counts vowels (`aeiouAEIOU`) in each string and returns a dictionary mapping each string to its count. Case-insensitive — both uppercase and lowercase vowels are counted.

```python
get_vowels(['apple', 'MONTCLAIR'])   # {'apple': 2, 'MONTCLAIR': 3}
get_vowels(['Taylor Swift', 'Hayat'])  # {'Taylor Swift': 3, 'Hayat': 2}
```

<img width="1088" height="429" alt="image" src="https://github.com/user-attachments/assets/b39da463-74e4-481e-8d3a-9809e4efe9cc" />
Vowel count per word with vowel letters annotated above each bar


### `get_words_with_a(list_str)` → `list[str]`
Filters a list to return only strings containing the lowercase letter `'a'`. Case-sensitive by design — `'Taylor'` matches (contains `'a'`) but `'APPLE'` does not.

```python
get_words_with_a(['Taylor', 'Swift', 'Hayat', 'Beyonce'])  # ['Taylor', 'Hayat']
```
<img width="1088" height="319" alt="image" src="https://github.com/user-attachments/assets/adb7287b-d1b6-4136-95a7-b65e24cc5be5" />
Horizontal bar — matched (green) vs. filtered (grey) words


### `remove_dups(lst)` → `list`
Removes duplicate items from a mixed list of numbers and strings. Strings are normalized to lowercase for case-insensitive comparison — `'New Jersey'` and `'new jersey'` are treated as the same item. Insertion order is preserved.

```python
remove_dups(['new jersey', 'apple', 6, 9, 'Decision', 'New jersey', 6, 'decision'])
# ['new jersey', 'apple', 6, 9, 'decision']
```
<img width="1308" height="394" alt="image" src="https://github.com/user-attachments/assets/3843f974-9238-461a-a8cf-3cde5c168d1c" />
Before/after side-by-side showing removed duplicates


### `is_prime(num)` → `bool`
Tests primality using trial division up to √n. **Why √n?** If `n = a × b` and both factors are > √n, then `a × b > n` — a contradiction. So at least one factor must be ≤ √n. This gives O(√n) performance vs. O(n) for naive divisor checking.

```python
is_prime(11)   # True
is_prime(49)   # False  (49 = 7 × 7)
is_prime(1)    # False  (1 is not prime by definition)
```
<img width="1418" height="319" alt="image" src="https://github.com/user-attachments/assets/3401a894-62e8-4d0e-8a26-2dbc19fe6171" />
Grid of integers 2–60, primes highlighted in green


### `get_factorial(num)` → `int | None`
Computes n! iteratively. Initializes `factorial = 1` and multiplies from 2 to n. Handles `0! = 1` and `1! = 1` naturally (the loop body does not execute). Returns `None` for negative inputs. Iterative implementation avoids Python's recursion limit for large values.

```python
get_factorial(5)   # 120   (5 × 4 × 3 × 2 × 1)
get_factorial(6)   # 720
get_factorial(0)   # 1
```
<img width="1198" height="429" alt="image" src="https://github.com/user-attachments/assets/e3f5fb93-8d32-410a-8dfd-6f522c8e95e5" />
Bar chart of 0! through 10! showing exponential growth


### `reverse_string(string)` → `str`
Reverses a string using Python's extended slice notation `[::-1]` — start at the end, stop at the beginning, step –1. Creates a new string; the original is unchanged.

```python
reverse_string('marina')     # 'aniram'
reverse_string('I love NYC') # 'CYN evol I'
reverse_string('racecar')    # 'racecar'  (palindrome)
```
<img width="1097" height="429" alt="image" src="https://github.com/user-attachments/assets/4de1c15b-2145-4e28-8608-4ca1a8ad17b5" />
Table: original · reversed · palindrome check


### `get_mode(lst_numbers)` → `int | float | None`
Returns the most frequently occurring value. Returns `None` when: the list is empty, all values appear once, or two or more values tie for the highest frequency. A **unique** mode requires one value to appear strictly more than all others.

```python
get_mode([1, 100, 3, 5, 3, 4, 4, 3])   # 3  (appears 3×)
get_mode([1, 2, 3, 4, 5])               # None  (all unique)
get_mode([1, 1, 2, 2])                  # None  (tie)
```
<img width="1088" height="429" alt="image" src="https://github.com/user-attachments/assets/a44d8d99-e3f2-42ff-81d5-b9f4167e0e4f" />
 Frequency chart with mode highlighted in red 

---

## How to Run

**Google Colab (recommended)**
```
Runtime → Run all
```

**Local Jupyter**
```bash
pip install matplotlib
jupyter notebook Python Fundamentals — 10 Core Algorithm Implementations.ipynb
```

No other dependencies. All 10 functions use only built-in Python.

---

## Skills Demonstrated

`Python Functions` `Algorithm Design` `Time Complexity Analysis` `NumPy Docstrings` `Loop Logic` `Conditionals` `Dictionaries` `Sets` `String Manipulation` `Type Safety` `Data Cleaning` `Statistics` `matplotlib` `Data Visualization`

---

## Author

**Aketch Adhiambo Okoth**  
MS Business Analytics — Montclair State University   
[LinkedIn](https://linkedin.com/in/your-profile) · [Portfolio](https://your-portfolio-url.com)
