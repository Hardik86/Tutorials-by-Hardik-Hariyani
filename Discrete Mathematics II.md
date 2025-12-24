# Discrete Mathematics II  
## Complete Beginner-to-Advanced Tutorial  
**Created by Hardik Hariyani**

---

## Table of Contents

1. [Foundations Rebuilt from Zero](#foundations-rebuilt-from-zero)
2. [Searching Algorithms](#searching-algorithms)
3. [Sorting Algorithms](#sorting-algorithms)
4. [Big-O, Theta, and Omega Notation](#big-o-theta-and-omega-notation)
5. [Number Theory](#number-theory)
6. [Cryptography](#cryptography)
7. [Recursion](#recursion)
8. [Mathematical Induction](#mathematical-induction)
9. [Counting Techniques](#counting-techniques)
10. [Advanced Counting Techniques](#advanced-counting-techniques)
11. [Discrete Probability](#discrete-probability)
12. [Modeling Computation](#modeling-computation)

---

## Foundations Rebuilt from Zero

### What This Section Does

Before we tackle complex algorithms, we need rock-solid fundamentals. This section rebuilds discrete math from scratch—no assumptions about what you know. 

### Sets:  The Building Block of Everything

**What is a set?**

A set is a collection of distinct objects.  Think of it like a bucket containing specific items, where each item appears exactly once.

**Plain-English Example:**

- Set of prime numbers less than 10: {2, 3, 5, 7}
- Set of vowels:  {a, e, i, o, u}
- Set of your favorite foods: {pizza, tacos, sushi}

**Math Notation Decoder:**

| Symbol | Means | How to Read It | Example |
|--------|-------|----------------|---------|
| {} | A set | "Set containing" | {1, 2, 3} = set containing 1, 2, and 3 |
| ∈ | "is in" or "is a member of" | "is in" | 2 ∈ {1, 2, 3} means "2 is in the set" |
| ∉ | "is not in" | "is not in" | 4 ∉ {1, 2, 3} means "4 is not in the set" |
| ⊆ | "is a subset of" or "is contained in" | "is a subset of" | {1, 2} ⊆ {1, 2, 3} means "all items in first set are in second set" |
| ∪ | Union; combine sets | "union" | {1, 2} ∪ {2, 3} = {1, 2, 3} |
| ∩ | Intersection; overlap | "intersection" | {1, 2} ∩ {2, 3} = {2} (only items in both) |
| \| or # | Cardinality; count | "cardinality of" or "size of" | \|{1, 2, 3}\| = 3 |

**Key Idea:**

Sets are unordered.  {1, 2, 3} is identical to {3, 1, 2}. Order does not matter.

**Common Mistakes:**

- Mistake:  Thinking {1, 1, 2} is a valid set.  Reality:  Duplicates are automatically removed.  {1, 1, 2} = {1, 2}. 
- Mistake: Thinking ⊆ and ∈ mean the same thing. Reality: ∈ is for items; ⊆ is for sets inside sets.

**Memory Shortcut:**

- ∈ looks like the letter "e" in "element." An element is in a set. 
- ∪ looks like a "U" for "union"—put everything together.
- ∩ looks like an upside-down "U"—the overlap in the middle.

**Real-World IT Application:**

In databases, a set represents all valid users, all products, or all transactions. When you query "Find users WHO ARE IN region X AND WHO ARE IN age_group Y," you're computing A ∩ B. 

### Functions: Input → Output

**What is a function? **

A function is a rule that takes an input and produces exactly one output. 

**Plain-English Example:**

- Input: a number.  Output: that number squared.  f(x) = x²
- Input: a person's name. Output: their age. 
- Input: a URL. Output: the HTML of that page.

**Math Notation Decoder:**

| Symbol | Means | How to Read It | Example |
|--------|-------|----------------|---------|
| f(x) | f is a function; x is the input | "f of x" | f(3) = 9 (if f(x) = x²) |
| f:  A → B | Function f maps from set A to set B | "f maps from A to B" | f:  {1,2} → {1,2,3,4} |
| Domain | All possible inputs | N/A | For f(x) = √x, domain is x ≥ 0 |
| Range or Codomain | All possible outputs | N/A | For f(x) = x², range is y ≥ 0 |

**Key Idea:**

A function produces one output per input. If an input produces two different outputs, it's not a function—it's a relation.

**Common Mistakes:**

- Mistake: Thinking f(x) is multiplication. Reality: f(x) means "apply function f to x."
- Mistake: Thinking every input must be used.  Reality: That's fine.  But every used input must produce exactly one output.

**Memory Shortcut:**

Think of a function as a vending machine: 
- Input: money + selection code
- Output: one snack

You can't get two different snacks from the same input.

**Real-World IT Application:**

Every function in code (Python, JavaScript, etc.) is a mathematical function: 

```python
def double(x):
    return 2 * x
```

Input: x.  Output: 2 * x.  If x = 5, output = 10. Always.

### Logic: True and False

**What is logic?**

Logic is the study of statements that are either true or false, and how we combine them. 

**Basic Operators:**

| Symbol | Name | Means | Reads As | Example |
|--------|------|-------|----------|---------|
| ∧ | AND | Both must be true | "and" | P ∧ Q = true only if P is true AND Q is true |
| ∨ | OR | At least one must be true | "or" | P ∨ Q = true if P is true OR Q is true OR both |
| ¬ | NOT | Flips true to false | "not" | ¬P = opposite of P |
| → | Implies | If first is true, second must be true | "implies" or "if...then" | P → Q = if P then Q |

**Truth Table Example (AND):**

| P | Q | P ∧ Q |
|---|---|-------|
| T | T | T |
| T | F | F |
| F | T | F |
| F | F | F |

**Plain-English:**

"It's raining AND it's cold" is true only if both statements are true.  If it's raining but warm, the AND statement is false.

**Real-World IT Application:**

Every if-statement in code uses logic:

```python
if (user_logged_in AND has_permission):
    show_admin_panel()
```

---

## Searching Algorithms

### Why Searching Matters

Searching is finding an item in a collection. In IT, you do this constantly:
- Finding a username in a database
- Locating a word in a document
- Checking if an email exists in a list

We'll learn two main approaches:  Linear Search and Binary Search.

### Linear Search:  Check Every Item

**Plain-English Intuition:**

Imagine looking for your friend in a crowd. You check each person one by one:  "Is this Sarah?  No.  Is this Sarah? No. Yes—found her!"

**Formal Definition:**

Given a list of n items and a target value, check each item in order until you find the target or reach the end.

**Algorithm Walkthrough:**

```
ALGORITHM LinearSearch(list, target)
  FOR i = 0 TO length(list) - 1
    IF list[i] == target
      RETURN i (found at position i)
    END IF
  END FOR
  RETURN -1 (not found)
END ALGORITHM
```

**Worked Example:**

List: [10, 25, 17, 44, 8]
Target: 17

- Step 1: Check position 0. list[0] = 10. Is it 17? No.
- Step 2: Check position 1. list[1] = 25. Is it 17? No. 
- Step 3: Check position 2. list[2] = 17. Is it 17? Yes! Return 2.

Result: 17 is at position 2. (Positions start at 0.)

**Python Implementation:**

```python
def linear_search(arr, target):
    for i in range(len(arr)):
        if arr[i] == target: 
            return i
    return -1

# Test
numbers = [10, 25, 17, 44, 8]
print(linear_search(numbers, 17))  # Output: 2
print(linear_search(numbers, 99))  # Output: -1 (not found)
```

**Common Mistakes:**

- Mistake:  Thinking linear search is always slow. Reality: For small lists (< 100 items) it's often faster than alternatives because it's simple. 
- Mistake: Returning the value instead of the position. Reality: Always return the index (position).

**Memory Shortcut:**

Linear = "line." Walk down a line, checking each person. 

**Why This Matters in IT:**

Used when data is unsorted or unstructured. Also used when you need all occurrences, not just the first.

### Binary Search: Divide and Conquer

**Plain-English Intuition:**

Imagine guessing a number between 1 and 100. Your friend says "higher" or "lower." Smart strategy: guess 50. If they say "higher," forget 1–50.  Guess 75. This cuts the search space in half each time.

**Key Requirement:**

The list **must be sorted** in order (smallest to largest, or largest to smallest).

**Formal Definition:**

Given a sorted list of n items and a target value, repeatedly divide the search space in half until you find the target or determine it's not there.

**Algorithm Walkthrough:**

```
ALGORITHM BinarySearch(sorted_list, target)
  left = 0
  right = length(sorted_list) - 1

  WHILE left <= right
    mid = (left + right) / 2 (integer division)
    IF sorted_list[mid] == target
      RETURN mid
    ELSE IF sorted_list[mid] < target
      left = mid + 1 (target is in right half)
    ELSE
      right = mid - 1 (target is in left half)
    END IF
  END WHILE

  RETURN -1 (not found)
END ALGORITHM
```

**Worked Example:**

Sorted List: [5, 12, 17, 22, 31, 44, 58]
Target: 22

- Step 1: left = 0, right = 6. mid = 3. list[3] = 22. Is it 22? Yes! Return 3.

Another example with more steps: 

Sorted List: [5, 12, 17, 22, 31, 44, 58]
Target: 31

- Step 1: left = 0, right = 6. mid = 3. list[3] = 22. Is 22 == 31? No.  Is 22 < 31? Yes. So target is in right half. left = 4.
- Step 2: left = 4, right = 6. mid = 5. list[5] = 44. Is 44 == 31? No. Is 44 < 31? No. So target is in left half. right = 4.
- Step 3: left = 4, right = 4. mid = 4. list[4] = 31. Is 31 == 31? Yes! Return 4.

**Python Implementation:**

```python
def binary_search(sorted_arr, target):
    left, right = 0, len(sorted_arr) - 1

    while left <= right:
        mid = (left + right) // 2
        if sorted_arr[mid] == target:
            return mid
        elif sorted_arr[mid] < target:
            left = mid + 1
        else:
            right = mid - 1

    return -1

# Test
numbers = [5, 12, 17, 22, 31, 44, 58]
print(binary_search(numbers, 22))  # Output: 3
print(binary_search(numbers, 31))  # Output: 4
print(binary_search(numbers, 99))  # Output: -1 (not found)
```

**Common Mistakes:**

- Mistake: Using binary search on an unsorted list. Reality: It breaks completely.  Always sort first.
- Mistake: Computing mid as (left + right) / 2 and forgetting integer division. Reality: Use // in Python to ensure an integer position. 
- Mistake: Updating left or right incorrectly. Reality: If target is higher, left = mid + 1. If lower, right = mid - 1.

**Memory Shortcut:**

Binary = "two." You're dividing into two halves repeatedly.  Half, half, half... 

**Real-World IT Application:**

Phone directories, dictionaries, database indexes.  Anywhere data is sorted.  Google Search results, autocomplete dropdowns.  Any time you need speed on large sorted datasets.

---

## Sorting Algorithms

### Why Sorting Matters

Sorting is arranging items in order (ascending or descending). Nearly every computer system sorts: 
- Email by date
- Search results by relevance
- Contacts alphabetically
- Products by price

We'll learn five foundational algorithms: Bubble Sort, Selection Sort, Insertion Sort, Merge Sort, and Quick Sort.

### Bubble Sort: The Easiest (But Slowest)

**Plain-English Intuition:**

Imagine bubbles rising in water.  Heavier items "sink," lighter items "rise." Bubble sort repeatedly compares adjacent items and swaps them if they're in the wrong order. 

**Formal Definition:**

Repeatedly walk through the list, compare adjacent pairs, and swap them if they're in the wrong order.  Repeat until no more swaps are needed.

**Algorithm Walkthrough:**

```
ALGORITHM BubbleSort(list)
  n = length(list)
  FOR i = 0 TO n-1
    FOR j = 0 TO n-i-2
      IF list[j] > list[j+1]
        SWAP list[j] and list[j+1]
      END IF
    END FOR
  END FOR
END ALGORITHM
```

**Worked Example:**

Original: [5, 2, 8, 1, 9]

Pass 1:
- Compare 5 and 2: 5 > 2. Swap. [2, 5, 8, 1, 9]
- Compare 5 and 8: 5 < 8. No swap.  [2, 5, 8, 1, 9]
- Compare 8 and 1: 8 > 1. Swap. [2, 5, 1, 8, 9]
- Compare 8 and 9: 8 < 9. No swap. [2, 5, 1, 8, 9]

Pass 2:
- Compare 2 and 5: 2 < 5. No swap. [2, 5, 1, 8, 9]
- Compare 5 and 1: 5 > 1. Swap. [2, 1, 5, 8, 9]
- Compare 5 and 8: 5 < 8. No swap. [2, 1, 5, 8, 9]

Pass 3:
- Compare 2 and 1: 2 > 1. Swap.  [1, 2, 5, 8, 9]
- Compare 2 and 5: 2 < 5. No swap. [1, 2, 5, 8, 9]

Pass 4:
- Compare 1 and 2: 1 < 2. No swap.  [1, 2, 5, 8, 9]

Final: [1, 2, 5, 8, 9] ✓

**Python Implementation:**

```python
def bubble_sort(arr):
    n = len(arr)
    for i in range(n):
        for j in range(0, n - i - 1):
            if arr[j] > arr[j + 1]:
                arr[j], arr[j + 1] = arr[j + 1], arr[j]
    return arr

# Test
numbers = [5, 2, 8, 1, 9]
print(bubble_sort(numbers))  # Output: [1, 2, 5, 8, 9]
```

**Common Mistakes:**

- Mistake:  Thinking bubble sort is ever fast. Reality: It's slow for large lists.  Use it only for learning or tiny lists (< 50 items).
- Mistake: Forgetting the outer loop. Reality: You need both loops—the outer determines passes, the inner does comparisons. 

**Memory Shortcut:**

Bubbles float up. Large values "bubble" to the end. 

**Real-World IT Application:**

Rarely used in production.  Educational purposes.  Very small datasets. 

### Selection Sort: Find and Place

**Plain-English Intuition:**

Imagine arranging cards.  Repeatedly find the smallest card and place it at the front. 

**Formal Definition:**

Divide the list into a sorted portion (on the left) and unsorted portion (on the right). Repeatedly find the minimum in the unsorted portion and move it to the end of the sorted portion.

**Algorithm Walkthrough:**

```
ALGORITHM SelectionSort(list)
  n = length(list)
  FOR i = 0 TO n-1
    min_index = i
    FOR j = i+1 TO n-1
      IF list[j] < list[min_index]
        min_index = j
      END IF
    END FOR
    SWAP list[i] and list[min_index]
  END FOR
END ALGORITHM
```

**Worked Example:**

Original:  [5, 2, 8, 1, 9]

Iteration 1: Find min in entire list. Min = 1 (index 3). Swap with position 0. [1, 2, 8, 5, 9]

Iteration 2: Find min in [2, 8, 5, 9]. Min = 2 (index 1). Swap with position 1. [1, 2, 8, 5, 9] (no change)

Iteration 3: Find min in [8, 5, 9]. Min = 5 (index 3). Swap with position 2. [1, 2, 5, 8, 9]

Iteration 4: Find min in [8, 9]. Min = 8 (index 3). Swap with position 3. [1, 2, 5, 8, 9] (no change)

Final: [1, 2, 5, 8, 9] ✓

**Python Implementation:**

```python
def selection_sort(arr):
    n = len(arr)
    for i in range(n):
        min_index = i
        for j in range(i + 1, n):
            if arr[j] < arr[min_index]:
                min_index = j
        arr[i], arr[min_index] = arr[min_index], arr[i]
    return arr

# Test
numbers = [5, 2, 8, 1, 9]
print(selection_sort(numbers))  # Output: [1, 2, 5, 8, 9]
```

**Common Mistakes:**

- Mistake: Searching the entire unsorted portion but starting from index 0. Reality: Start from i+1 to avoid rechecking the sorted part.
- Mistake: Not swapping even when min_index = i. Reality: Swapping is still correct; it just doesn't change anything.

**Memory Shortcut:**

Select the smallest.  Place it.  Repeat.

**Real-World IT Application:**

When memory writes are expensive but reads are cheap. Useful in embedded systems with limited resources.  Not ideal for large datasets.

### Insertion Sort: Build a Sorted Sequence

**Plain-English Intuition:**

Imagine sorting playing cards as you draw them. You hold sorted cards in your hand. For each new card, insert it in the correct position.

**Formal Definition:**

Build a sorted portion of the list from left to right. For each unsorted item, insert it into its correct position in the sorted portion. 

**Algorithm Walkthrough:**

```
ALGORITHM InsertionSort(list)
  FOR i = 1 TO length(list) - 1
    key = list[i]
    j = i - 1
    WHILE j >= 0 AND list[j] > key
      list[j + 1] = list[j]
      j = j - 1
    END WHILE
    list[j + 1] = key
  END FOR
END ALGORITHM
```

**Worked Example:**

Original:  [5, 2, 8, 1, 9]

Start:  Sorted = [5].  Unsorted = [2, 8, 1, 9]

Insert 2: Compare 2 to 5. 2 < 5. Shift 5 right. Insert 2. Sorted = [2, 5]. Unsorted = [8, 1, 9]

Insert 8: Compare 8 to 5. 8 > 5. Insert 8. Sorted = [2, 5, 8].  Unsorted = [1, 9]

Insert 1: Compare 1 to 8. 1 < 8. Shift 8. Compare 1 to 5. 1 < 5. Shift 5. Compare 1 to 2. 1 < 2. Shift 2. Insert 1. Sorted = [1, 2, 5, 8]. Unsorted = [9]

Insert 9: Compare 9 to 8. 9 > 8. Insert 9. Sorted = [1, 2, 5, 8, 9]. 

Final: [1, 2, 5, 8, 9] ✓

**Python Implementation:**

```python
def insertion_sort(arr):
    for i in range(1, len(arr)):
        key = arr[i]
        j = i - 1
        while j >= 0 and arr[j] > key:
            arr[j + 1] = arr[j]
            j -= 1
        arr[j + 1] = key
    return arr

# Test
numbers = [5, 2, 8, 1, 9]
print(insertion_sort(numbers))  # Output: [1, 2, 5, 8, 9]
```

**Common Mistakes:**

- Mistake: Forgetting to insert the key at the end of the while loop. Reality: Always insert after the while loop ends.
- Mistake: Comparing the key to items beyond the sorted portion. Reality: The key is list[i]; only compare to items before index i.

**Memory Shortcut:**

Insert each card into the right position in your sorted hand.

**Real-World IT Application:**

Insertion sort is excellent for: 
- Nearly sorted data (very fast)
- Small lists (< 50 items)
- Real-time systems where you're receiving data incrementally

Great for online sorting where you get data one item at a time.

### Merge Sort: Divide and Conquer (Fast)

**Plain-English Intuition:**

Imagine two people sorting cards. Person A sorts the left half.  Person B sorts the right half. Then they merge the two sorted halves into one sorted deck.  This is efficient because merging two sorted lists is fast.

**Formal Definition:**

Recursively divide the list in half until each half is size 1 (a single item is trivially sorted). Then merge adjacent pairs back together, maintaining sorted order.

**Key Concept:**

Merging two sorted lists of size n₁ and n₂ takes n₁ + n₂ comparisons (linear time).

**Algorithm Walkthrough:**

```
ALGORITHM MergeSort(list, left, right)
  IF left < right
    mid = (left + right) / 2
    MergeSort(list, left, mid)
    MergeSort(list, mid + 1, right)
    Merge(list, left, mid, right)
  END IF
END ALGORITHM

ALGORITHM Merge(list, left, mid, right)
  Create temp arrays
  Copy left half:  list[left...mid] into temp_left
  Copy right half: list[mid+1...right] into temp_right

  i = 0, j = 0, k = left

  WHILE i < length(temp_left) AND j < length(temp_right)
    IF temp_left[i] <= temp_right[j]
      list[k] = temp_left[i]
      i = i + 1
    ELSE
      list[k] = temp_right[j]
      j = j + 1
    END IF
    k = k + 1
  END WHILE

  Copy remaining elements from temp_left (if any)
  Copy remaining elements from temp_right (if any)
END ALGORITHM
```

**Worked Example:**

Original: [38, 27, 43, 3, 9, 82, 10]

Divide: 
```
[38, 27, 43, 3, 9, 82, 10]
          |
[38, 27, 43] | [3, 9, 82, 10]
   |       |    |    |
[38] [27, 43] [3, 9] [82, 10]
     |       |  |   |  |    |
    [38] [27] [43] [3] [9] [82] [10]
```

Merge:
```
[38] [27] → [27, 38]
[43] → [43]
[27, 38] [43] → [27, 38, 43]

[3] [9] → [3, 9]
[82] [10] → [10, 82]
[3, 9] [10, 82] → [3, 9, 10, 82]

[27, 38, 43] [3, 9, 10, 82] → [3, 9, 10, 27, 38, 43, 82]
```

Final: [3, 9, 10, 27, 38, 43, 82] ✓

**Python Implementation:**

```python
def merge_sort(arr):
    if len(arr) <= 1:
        return arr

    mid = len(arr) // 2
    left = merge_sort(arr[:mid])
    right = merge_sort(arr[mid:])

    return merge(left, right)

def merge(left, right):
    result = []
    i = j = 0

    while i < len(left) and j < len(right):
        if left[i] <= right[j]:
            result.append(left[i])
            i += 1
        else:
            result.append(right[j])
            j += 1

    result.extend(left[i:])
    result.extend(right[j:])
    return result

# Test
numbers = [38, 27, 43, 3, 9, 82, 10]
print(merge_sort(numbers))  # Output: [3, 9, 10, 27, 38, 43, 82]
```

**Common Mistakes:**

- Mistake: Forgetting the base case (len(arr) <= 1). Reality: Without it, recursion never stops.
- Mistake: Not handling remaining elements after one list is exhausted. Reality: Use extend() to append all remaining items. 
- Mistake: Thinking merge sort doesn't use extra space. Reality: It uses O(n) extra memory for temporary arrays.  That's a tradeoff.

**Memory Shortcut:**

Divide until size 1. Merge back up.  Always works. 

**Real-World IT Application:**

External sorting (when data doesn't fit in RAM). Stable sort (preserves order of equal items). Databases, large file sorting, any scenario where you need guaranteed O(n log n) performance.

### Quick Sort: Faster Average Case

**Plain-English Intuition:**

Imagine dividing a list into two piles:  smaller than X and larger than X (where X is a chosen "pivot"). Recursively sort each pile. Most of the time, this is faster than merge sort because you don't need to merge.

**Formal Definition:**

Choose a pivot element. Partition the list into items smaller than the pivot and items larger than the pivot.  Recursively sort each partition. 

**Algorithm Walkthrough:**

```
ALGORITHM QuickSort(list, low, high)
  IF low < high
    pivot_index = Partition(list, low, high)
    QuickSort(list, low, pivot_index - 1)
    QuickSort(list, pivot_index + 1, high)
  END IF
END ALGORITHM

ALGORITHM Partition(list, low, high)
  pivot = list[high]
  i = low - 1

  FOR j = low TO high - 1
    IF list[j] < pivot
      i = i + 1
      SWAP list[i] and list[j]
    END IF
  END FOR

  SWAP list[i + 1] and list[high]
  RETURN i + 1
END ALGORITHM
```

**Worked Example:**

Original: [10, 7, 8, 9, 1, 5]

Choose pivot = 5 (last element).

Partition:
- i = -1
- j = 0: list[0] = 10.  10 < 5? No.
- j = 1: list[1] = 7. 7 < 5? No.
- j = 2: list[2] = 8. 8 < 5? No.
- j = 3: list[3] = 9. 9 < 5? No.
- j = 4: list[4] = 1. 1 < 5? Yes. i = 0. Swap list[0] and list[4].  [1, 7, 8, 9, 10, 5]
- Swap list[1] and list[5] (pivot). [1, 5, 8, 9, 10, 7]

Pivot is now at position 1.  Left partition: [1].  Right partition: [8, 9, 10, 7]. 

Recursively sort right partition [8, 9, 10, 7]:
- Pivot = 7.
- Partition: [8, 9, 10, 7] becomes [7, 8, 9, 10]
- Left partition: [].  Right partition: [8, 9, 10]. 

Recursively sort [8, 9, 10]: 
- Pivot = 10.
- Already sorted:  [8, 9, 10].

Final: [1, 5, 7, 8, 9, 10] ✓

**Python Implementation:**

```python
def quick_sort(arr, low=0, high=None):
    if high is None: 
        high = len(arr) - 1

    if low < high:
        pivot_index = partition(arr, low, high)
        quick_sort(arr, low, pivot_index - 1)
        quick_sort(arr, pivot_index + 1, high)

    return arr

def partition(arr, low, high):
    pivot = arr[high]
    i = low - 1

    for j in range(low, high):
        if arr[j] < pivot:
            i += 1
            arr[i], arr[j] = arr[j], arr[i]

    arr[i + 1], arr[high] = arr[high], arr[i + 1]
    return i + 1

# Test
numbers = [10, 7, 8, 9, 1, 5]
print(quick_sort(numbers))  # Output: [1, 5, 7, 8, 9, 10]
```

**Common Mistakes:**

- Mistake:  Choosing a bad pivot (e.g., always the smallest or largest). Reality: This makes Quick Sort O(n²) in worst case.  Use random pivot or median-of-three heuristic.
- Mistake: Off-by-one errors in partition.  Reality: Be careful with loop bounds and swap positions. 

**Memory Shortcut:**

Pick a pivot. Split smaller and larger. Recurse.

**Real-World IT Application:**

Default sorting algorithm in most programming languages (with randomized pivot). Fast average case. Used in Timsort (Python), IntroSort (C++), and others.

---

## Big-O, Theta, and Omega Notation

### Why We Need Runtime Analysis

Different algorithms take different amounts of time.  We need a way to compare them objectively.  Big-O notation describes how an algorithm's runtime grows as input size grows.

**Key Question:**

If I double the input size, does the runtime double?  Triple? Stay the same? 

### Understanding Growth Rates

**Concept:  Input Size vs. Runtime**

Let's say an algorithm takes the following time (in milliseconds) for different input sizes:

| Input Size (n) | Bubble Sort | Insertion Sort | Merge Sort |
|---|---|---|---|
| 10 | 0.1 ms | 0.05 ms | 0.05 ms |
| 100 | 10 ms | 5 ms | 0.5 ms |
| 1000 | 1000 ms | 500 ms | 5 ms |
| 10000 | 100,000 ms | 50,000 ms | 50 ms |

Notice: 
- Bubble Sort: When n increases 10x, time increases 100x.  This is O(n²).
- Insertion Sort: When n increases 10x, time increases 100x. This is O(n²).
- Merge Sort: When n increases 10x, time increases ~10x. This is O(n log n).

### Big-O Notation:  Upper Bound

**What It Means:**

Big-O describes the worst-case scenario. "This algorithm will never take more than O(n²) time, no matter the input."

**Math Notation Decoder:**

| Symbol | Name | Means | How to Read It | Example |
|--------|------|-------|----------------|---------|
| O(1) | Constant | Time doesn't depend on input size | "Big-O of 1" or "constant time" | Accessing arr[5] always takes the same time |
| O(log n) | Logarithmic | Time grows slowly, proportional to log of input | "Big-O of log n" | Binary search |
| O(n) | Linear | Time grows proportionally with input | "Big-O of n" or "linear time" | Linear search, printing each element |
| O(n log n) | Linearithmic | Time grows a bit faster than linear | "Big-O of n log n" | Merge sort, Quick sort |
| O(n²) | Quadratic | Time grows with square of input | "Big-O of n squared" | Bubble sort, Selection sort |
| O(2ⁿ) | Exponential | Time doubles with each input increase | "Big-O of 2 to the n" | Recursive Fibonacci |
| O(n!) | Factorial | Extremely fast growth | "Big-O of n factorial" | Generating all permutations |

**Visualization:**

```
Runtime
  |
  |                                    O(2^n)
  |                                   /
  |                              O(n!)
  |                           /
  |                       O(n^2)
  |                   /
  |               O(n log n)
  |            /
  |         O(n)
  |       /
  |    O(log n)
  | /
  |________________________
          Input Size (n)
```

### Big-O Rules:  Simplifying Notation

**Rule 1: Drop Constants**

O(2n) = O(n). Whether you loop twice or once per item, it's still linear.

O(100n) = O(n).

O(3n²) = O(n²).

**Rule 2: Drop Lower-Order Terms**

O(n² + n) = O(n²). The n² term dominates.

O(n³ + n² + n) = O(n³).

O(n log n + n) = O(n log n).

**Rule 3: Nested Loops Multiply**

If you have a loop inside a loop: 
- Outer loop:  n times
- Inner loop: n times
- Total: n × n = O(n²)

**Plain Example:**

```python
for i in range(n):          # runs n times
    for j in range(n):      # runs n times
        print(i, j)         # O(1)
# Total: O(n * n) = O(n²)
```

### Analyzing Common Code Patterns

**Pattern:  Single Loop**

```python
for i in range(n):
    do_something()  # O(1)
# Time complexity: O(n)
```

**Pattern:  Nested Loops**

```python
for i in range(n):
    for j in range(n):
        do_something()  # O(1)
# Time complexity: O(n²)
```

**Pattern: Sequential Operations**

```python
# O(n)
for i in range(n):
    print(i)

# O(n²)
for i in range(n):
    for j in range(n):
        print(i, j)

# Total: O(n) + O(n²) = O(n²) (drop the lower term)
```

**Pattern: Logarithmic (Divide in Half)**

```python
n = 100
while n > 1:
    n = n // 2
    print(n)
# How many times does this run? 
# 100 → 50 → 25 → 12 → 6 → 3 → 1
# About log₂(100) ≈ 7 times
# Time complexity: O(log n)
```

**Pattern: Recursive Halving (Merge Sort)**

```python
def merge_sort(arr):
    if len(arr) <= 1:
        return arr
    mid = len(arr) // 2
    left = merge_sort(arr[:mid])        # O(n log n)
    right = merge_sort(arr[mid:])       # O(n log n)
    return merge(left, right)           # O(n)
# Time complexity: O(n log n)
```

### Space Complexity:  Memory Usage

Big-O also applies to space (memory).

**Examples:**

- O(1): Creating a few variables.  Space doesn't grow with input size.
- O(n): Creating a list of size n. Array uses space proportional to input. 
- O(n²): Creating a 2D grid of size n × n. 

**Common Tradeoff:**

Quick Sort uses O(1) extra space but is harder to implement correctly.
Merge Sort uses O(n) extra space but is easier to understand.

### Theta (Θ) Notation: Tight Bound

**What It Means:**

Theta describes both the upper and lower bounds.  The algorithm will take approximately this long—no better, no worse.

**Math Notation:**

| Symbol | Means | How to Read It |
|--------|-------|----------------|
| Θ(n) | Tight bound | "Big-Theta of n" or "the runtime is approximately n times the constant time" |

**Example:**

If an algorithm runs in exactly 5n + 3 operations (measured), we say Θ(n).

We don't say O(n⁵) or O(n²). We say Θ(n) because we know the exact behavior.

**When You Use It:**

In academic or formal analysis.  In practice, Big-O is more common.

### Omega (Ω) Notation: Lower Bound

**What It Means:**

Omega describes the best-case scenario. "This algorithm will take at least Ω(n) time."

**Math Notation:**

| Symbol | Means | How to Read It |
|--------|-------|----------------|
| Ω(n) | Lower bound | "Big-Omega of n" or "the runtime is at least n times the constant time" |

**Example:**

Linear Search on an unsorted list: 
- Best case: Target is at position 0. Ω(1).
- Worst case: Target is at the end (or missing). O(n).
- Average case:  Θ(n).

**When You Use It:**

Rarely in practice.  Mostly theoretical analysis.

### Key Idea: Three Perspectives

| Notation | Perspective | Meaning | When Used |
|----------|-------------|---------|-----------|
| O(n) | Upper bound (Worst case) | "Never worse than this" | Most common; practical analysis |
| Θ(n) | Tight bound | "Exactly this (approximately)" | Formal analysis; when best = worst |
| Ω(n) | Lower bound (Best case) | "Never better than this" | Theoretical proofs |

### Memory Shortcut

- **O** = **O**ver (upper bound; worst case)
- **Ω** = **O**mega sounds like "oh" (lower; minimum guaranteed)
- **Θ** = **T**ight (both bounds; exact behavior)

### Sorting Algorithm Complexity Summary

| Algorithm | Best Case | Average Case | Worst Case | Space |
|-----------|-----------|--------------|-----------|-------|
| Bubble Sort | O(n) | Θ(n²) | O(n²) | O(1) |
| Selection Sort | Θ(n²) | Θ(n²) | Θ(n²) | O(1) |
| Insertion Sort | O(n) | Θ(n²) | O(n²) | O(1) |
| Merge Sort | Θ(n log n) | Θ(n log n) | O(n log n) | O(n) |
| Quick Sort | Θ(n log n) | Θ(n log n) | O(n²) | O(log n) |

**Key Takeaway:**

For most real-world scenarios, use Merge Sort (guaranteed O(n log n)) or Quick Sort (average O(n log n), worst O(n²) but rarely happens with good pivot selection).

---

## Number Theory

### Why Number Theory Matters in CS

Number theory is the study of integers and their properties. It's foundational for:
- Cryptography (RSA, encryption keys)
- Hashing (distributing data uniformly)
- Optimization (finding factors, GCD)
- Network protocols (checksums)

### Divisibility and Factors

**What It Means:**

"a divides b" (written a | b) means b is a multiple of a.  In other words, b ÷ a has no remainder.

**Math Notation Decoder:**

| Symbol | Means | How to Read It | Example |
|--------|-------|----------------|---------|
| a \| b | a divides b | "a divides b" | 3 \| 9 means "3 divides 9" (because 9 = 3 × 3) |
| a ∤ b | a does not divide b | "a does not divide b" | 3 ∤ 10 (because 10 ÷ 3 = 3 remainder 1) |

**Plain-English:**

"3 divides 9" means 9 is a multiple of 3.
"3 does not divide 10" means 10 is not a multiple of 3.

**Formal Definition:**

a | b if and only if there exists an integer k such that b = a × k.

**Examples:**

- 2 | 8 (because 8 = 2 × 4)
- 5 | 25 (because 25 = 5 × 5)
- 7 ∤ 20 (because 20 ÷ 7 = 2 remainder 6)

### Prime Numbers and Factorization

**What is a Prime Number?**

A prime number is a natural number greater than 1 that has exactly two factors: 1 and itself. 

**Examples:**

- 2 is prime (factors: 1, 2)
- 3 is prime (factors: 1, 3)
- 5 is prime (factors: 1, 5)
- 4 is not prime (factors: 1, 2, 4)
- 1 is not prime (has only one factor:  itself)

**Plain-English Intuition:**

Imagine dividing a room.  If a group of 7 people can't split equally into smaller groups (except as a whole), 7 is prime.  If 6 people can split into groups of 2 or 3, 6 is not prime.

**Prime Factorization:**

Breaking a number into its prime factors.

**Example:**

- 12 = 2 × 2 × 3 = 2² × 3
- 60 = 2 × 2 × 3 × 5 = 2² × 3 × 5
- 7 = 7 (already prime)

**Python Implementation (Check if Prime):**

```python
def is_prime(n):
    if n < 2:
        return False
    if n == 2:
        return True
    if n % 2 == 0:
        return False

    # Check odd divisors up to sqrt(n)
    for i in range(3, int(n**0.5) + 1, 2):
        if n % i == 0:
            return False
    return True

# Test
print(is_prime(17))   # True
print(is_prime(20))   # False
print(is_prime(2))    # True
```

**Key Insight:**

To check if n is prime, you only need to test divisors up to √n. Why? If n = a × b and a > √n, then b < √n.  So you'll find b first. 

### Greatest Common Divisor (GCD)

**What It Means:**

The GCD of two numbers is the largest positive integer that divides both. 

**Plain-English:**

The greatest common divisor of 12 and 8 is 4 (because 4 divides both 12 and 8, and no number larger than 4 does).

**Examples:**

- GCD(12, 8) = 4
- GCD(17, 5) = 1
- GCD(24, 36) = 12

**Euclidean Algorithm:**

The fastest way to compute GCD is the Euclidean Algorithm. 

```
ALGORITHM GCD(a, b)
  IF b == 0
    RETURN a
  ELSE
    RETURN GCD(b, a mod b)
  END IF
END ALGORITHM
```

**Intuition:**

GCD(a, b) = GCD(b, remainder of a ÷ b). Repeat until remainder is 0.

**Worked Example:**

GCD(48, 18):
- GCD(48, 18) = GCD(18, 48 mod 18) = GCD(18, 12)
- GCD(18, 12) = GCD(12, 18 mod 12) = GCD(12, 6)
- GCD(12, 6) = GCD(6, 12 mod 6) = GCD(6, 0)
- GCD(6, 0) = 6

Result: GCD(48, 18) = 6 ✓

**Python Implementation:**

```python
def gcd(a, b):
    while b != 0:
        a, b = b, a % b
    return a

# Test
print(gcd(48, 18))  # Output: 6
print(gcd(17, 5))   # Output: 1
print(gcd(100, 50)) # Output: 50
```

**Common Mistakes:**

- Mistake:  Testing all numbers from 1 to min(a, b). Reality:  Euclidean algorithm is much faster.
- Mistake: Computing GCD by listing all factors manually. Reality: Use the algorithm. 

**Memory Shortcut:**

Euclidean algorithm:  Keep dividing by the remainder until remainder is 0.

**Real-World IT Application:**

- Reducing fractions (GCD finds the denominator)
- Cryptography (RSA encryption uses GCD checks)
- Cache optimization (choosing array sizes)
- Scheduling tasks at regular intervals

### Modular Arithmetic

**What It Means:**

Modular arithmetic is arithmetic with remainders. The modulo operation (mod) returns the remainder after division.

**Math Notation Decoder:**

| Symbol | Means | How to Read It | Example |
|--------|-------|----------------|---------|
| a mod b | Remainder of a ÷ b | "a modulo b" | 17 mod 5 = 2 (because 17 ÷ 5 = 3 remainder 2) |
| a ≡ b (mod m) | a and b have the same remainder when divided by m | "a is congruent to b modulo m" | 17 ≡ 2 (mod 5) (both have remainder 2 when divided by 5) |

**Plain-English:**

If you have 17 apples and you want to divide them into groups of 5, you get 3 complete groups and 2 apples left over.  17 mod 5 = 2.

**Examples:**

- 17 mod 5 = 2 (17 = 5 × 3 + 2)
- 20 mod 7 = 6 (20 = 7 × 2 + 6)
- 13 mod 4 = 1 (13 = 4 × 3 + 1)
- 10 mod 3 = 1 (10 = 3 × 3 + 1)

**Python Implementation:**

```python
# mod operator in Python is %
print(17 % 5)   # Output: 2
print(20 % 7)   # Output: 6
print(13 % 4)   # Output: 1

# Checking divisibility
if n % 2 == 0:
    print("n is even")
else:
    print("n is odd")
```

**Properties of Modular Arithmetic:**

1. (a + b) mod m = ((a mod m) + (b mod m)) mod m
2. (a × b) mod m = ((a mod m) × (b mod m)) mod m
3. (a - b) mod m = ((a mod m) - (b mod m)) mod m

**Example:**

(15 + 12) mod 7: 
- Direct: 27 mod 7 = 6
- Using properties: ((15 mod 7) + (12 mod 7)) mod 7 = (1 + 5) mod 7 = 6 mod 7 = 6 ✓

**Real-World IT Application:**

- Hashing:  Distributing keys evenly across hash table buckets
- Checksums: Detecting errors in transmission
- Clock arithmetic: Time wraps at 12 or 24 hours
- Cryptography: Foundation of encryption
- Load balancing: Round-robin server assignment

### Fermat's Little Theorem

**What It Says:**

If p is prime and a is not divisible by p, then: 

a^(p-1) ≡ 1 (mod p)

**Plain-English:**

If you take any number a, raise it to the power (p-1), and compute the result modulo a prime p, you get 1.

**Example:**

p = 7 (prime), a = 3: 
- 3^(7-1) = 3^6 = 729
- 729 mod 7 = 729 - (104 × 7) = 729 - 728 = 1 ✓

**Why It Matters:**

This theorem is the foundation of RSA encryption and primality testing.

**Python Example:**

```python
def fermat_check(p, a):
    """Check if a^(p-1) mod p = 1"""
    result = pow(a, p - 1, p)  # Efficient modular exponentiation
    return result == 1

print(fermat_check(7, 3))    # True (7 is prime, 3 is not divisible by 7)
print(fermat_check(7, 5))    # True
print(fermat_check(11, 2))   # True (11 is prime)
```

**Note on pow(a, b, m):**

In Python, `pow(a, b, m)` computes a^b mod m efficiently.  Much better than computing a^b first, then taking mod, because a^b can be astronomically large.

---

## Cryptography

### Why Cryptography Matters

Cryptography protects data.  Every HTTPS connection, digital signature, password storage, and blockchain uses cryptographic concepts.

**Three Goals:**

1. **Confidentiality:** Only authorized parties read the message. 
2. **Integrity:** The message hasn't been tampered with. 
3. **Authentication:** The sender is who they claim to be. 

### Symmetric Encryption:  Same Key to Lock and Unlock

**Plain-English Intuition:**

Imagine a locked box. You and your friend both have the same key.  You put a secret inside, lock it, send it.  They unlock it with their copy of the key. 

**How It Works:**

- Plaintext (original message) + Key → Ciphertext (encrypted message)
- Ciphertext + Key → Plaintext (decrypted message)

**Math Notation Decoder:**

| Symbol | Means | How to Read It | Example |
|--------|-------|----------------|---------|
| E(K, M) | Encrypt message M with key K | "Encrypt M with key K" | E(key, "hello") = "x7f2q" |
| D(K, C) | Decrypt ciphertext C with key K | "Decrypt C with key K" | D(key, "x7f2q") = "hello" |

**Examples of Symmetric Encryption:**

- AES (Advanced Encryption Standard)
- DES (Data Encryption Standard, now considered weak)
- RC4

**Why Symmetric Encryption is Fast:**

The algorithm is simple and runs quickly. Used for bulk data encryption. 

**The Key Distribution Problem:**

How do you securely share the key with your friend? If you send it over the internet and it's intercepted, security is broken.

This is where asymmetric encryption comes in. 

### Asymmetric Encryption: Public and Private Keys

**Plain-English Intuition:**

Imagine every person has two keys: 
- **Public Key:** Like a mailbox. Anyone can put letters in. 
- **Private Key:** Like the key to that mailbox. Only the owner has it.

If someone encrypts a message with your public key, only you (with your private key) can decrypt it.

**How It Works:**

1. Person A generates a public key and a private key.
2. Person A shares the public key with everyone.
3. Person B encrypts a message using Person A's public key.
4. Person A decrypts the message using their private key. 
5. Only Person A can decrypt it.

**Math Notation:**

| Symbol | Means |
|--------|-------|
| PK | Public Key (shared with everyone) |
| SK | Private Key (kept secret) |

**Example of Asymmetric Encryption:**

RSA (Rivest-Shamir-Adleman) is the most famous asymmetric encryption algorithm.

### RSA Encryption:  Intuition

**Plain-English Intuition:**

RSA relies on a mathematical fact: multiplying two large primes is easy, but factoring their product back into the original primes is extremely hard.

**Example (Simple Numbers for Illustration):**

- Choose two primes:  p = 61, q = 53
- Compute n = p × q = 3233
- Public key: n = 3233 (shared with everyone)
- Private key: knowing p and q (kept secret)

**Why It's Secure:**

If someone knows n = 3233 and tries to factor it back to p and q, they'd need to try dividing 3233 by every number up to √3233 ≈ 57. For real RSA, n is 2048 bits (a number with ~600 digits). Factoring that would take longer than the age of the universe. 

**High-Level RSA Process:**

1. **Key Generation:**
   - Choose two large primes:  p and q
   - Compute n = p × q
   - Compute φ(n) = (p-1)(q-1) (Euler's totient function)
   - Choose e such that 1 < e < φ(n) and gcd(e, φ(n)) = 1
   - Compute d such that (e × d) ≡ 1 (mod φ(n))
   - Public key: (e, n)
   - Private key: (d, n)

2. **Encryption:**
   - Plaintext:  M
   - Ciphertext: C = M^e mod n

3. **Decryption:**
   - Ciphertext:  C
   - Plaintext:  M = C^d mod n

**Worked Example (Simplified):**

Let's use small primes for illustration (insecure in reality):
- p = 61, q = 53
- n = 61 × 53 = 3233
- φ(n) = 60 × 52 = 3120
- e = 17 (chosen such that gcd(17, 3120) = 1)
- d = 2753 (computed such that 17 × 2753 ≡ 1 (mod 3120), which means 17 × 2753 = 46801 = 15 × 3120 + 1)
- Public key: (e=17, n=3233)
- Private key: (d=2753, n=3233)

To encrypt message M = 123:
- C = 123^17 mod 3233 = 855

To decrypt ciphertext C = 855:
- M = 855^2753 mod 3233 = 123 ✓

**Python Implementation (Simplified for Education):**

```python
# For real use, use cryptography libraries! 
def gcd(a, b):
    while b:
        a, b = b, a % b
    return a

def extended_gcd(a, b):
    if a == 0:
        return b, 0, 1
    gcd_val, x1, y1 = extended_gcd(b % a, a)
    x = y1 - (b // a) * x1
    y = x1
    return gcd_val, x, y

def mod_inverse(e, phi):
    """Find d such that (e * d) % phi == 1"""
    _, x, _ = extended_gcd(e, phi)
    return (x % phi + phi) % phi

def rsa_encrypt(m, e, n):
    return pow(m, e, n)

def rsa_decrypt(c, d, n):
    return pow(c, d, n)

# Simple example (insecure; for education only)
p, q = 61, 53
n = p * q
phi = (p - 1) * (q - 1)
e = 17
d = mod_inverse(e, phi)

print(f"Public key: ({e}, {n})")
print(f"Private key: ({d}, {n})")

m = 123
c = rsa_encrypt(m, e, n)
m_decrypted = rsa_decrypt(c, d, n)

print(f"Original:  {m}")
print(f"Encrypted: {c}")
print(f"Decrypted: {m_decrypted}")
```

### Hash Functions: Fingerprints of Data

**What It Means:**

A hash function takes any input and produces a fixed-size output called a hash or digest. 

**Plain-English Intuition:**

Imagine scanning a document and creating a unique fingerprint. No two documents (with different content) produce the same fingerprint.  Any tiny change in the document changes the fingerprint completely.

**Properties of Good Hash Functions:**

1. **Deterministic:** Same input always produces same output. 
2. **Fast:** Computing the hash is quick.
3. **Fixed Output Size:** No matter the input size, output is the same length.
4. **Pre-image Resistant:** Given a hash, you can't find the original input. 
5. **Collision Resistant:** Two different inputs should never produce the same hash.

**Examples of Hash Functions:**

- MD5 (now broken; don't use)
- SHA-1 (weakening; migrate away)
- SHA-256 (secure; widely used)
- SHA-3 (latest standard)

**Python Example:**

```python
import hashlib

message = "hello world"

# SHA-256 hash
sha256_hash = hashlib.sha256(message.encode()).hexdigest()
print(f"SHA-256: {sha256_hash}")
# Output: b94d27b9934d3e08a52e52d7da7dabfac484efe37a5380ee9088f7ace2efcde9

# Change one character
message2 = "hello world!"
sha256_hash2 = hashlib.sha256(message2.encode()).hexdigest()
print(f"SHA-256: {sha256_hash2}")
# Output: 7509e7b6571d2a7326bada745a97e4e6e32f96577c2d96c7e2df6e6eb9e6a59
# Completely different! 
```

**Common Use Cases:**

1. **Password Storage:**
   - Don't store passwords.  Hash them.
   - When user logs in, hash their input and compare to stored hash.

2. **Data Integrity:**
   - Compute hash of file before transmission.
   - Receiver recomputes hash and verifies match. 
   - If hash differs, data was corrupted or tampered with.

3. **Blockchain:**
   - Each block contains hash of previous block.
   - Changing one block invalidates all subsequent blocks.

### Digital Signatures: Proving Authorship

**Plain-English Intuition:**

A digital signature proves you created a message (authentication and non-repudiation). It's like signing a document with a signature that can't be forged.

**How It Works:**

1. Person A computes the hash of a message.
2. Person A encrypts the hash with their private key (signing).
3. Person A sends the message + signature to Person B.
4. Person B decrypts the signature with Person A's public key.
5. Person B computes the hash of the message. 
6. If the decrypted hash matches the computed hash, the signature is valid.  The message is authentic and unchanged.

**Process:**

```
Message → Hash Function → Hash
           ↓
          Sign with private key
           ↓
         Signature

Receiver: 
Message → Hash Function → Hash_computed
Signature + Public Key → Decrypt → Hash_received

Compare Hash_computed == Hash_received? 
If yes:  Authentic and unchanged
If no: Tampered or fake signature
```

**Python Example (Simplified):**

```python
from hashlib import sha256

# Simulate signing and verification
def simple_sign(message, private_key):
    """Simplified:  hash the message and 'sign' it"""
    h = sha256(message.encode()).hexdigest()
    # In reality, encrypt with private key
    signature = int(h, 16) ^ private_key  # XOR with private key (simplified)
    return signature

def simple_verify(message, signature, public_key):
    """Simplified: verify the signature"""
    h = sha256(message.encode()).hexdigest()
    computed_hash = int(h, 16) ^ public_key  # XOR with public key (simplified)
    # In reality, this is much