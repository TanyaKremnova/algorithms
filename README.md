# 📘 1. Searching Algorithms
- Find the position of a target value within a collection.
- Common types: Linear Search, Binary Search.
- Use case: Quickly finding data in arrays or lists.

## Linear Search

**What:** Check each element in an array one by one until the target is found.  

**When:** For small or unsorted arrays.  

**Complexity:**  
- Time: O(n)
- Space: O(1)

**Example in C:**
```bash
int linear_search(int *arr, int size, int target)
{
	int	i = 0;

	while (i < size)
	{
		if (arr[i] == target)
			return (i); // found at index i
		i++;
	}
	return (-1); // not found
}
```

## Binary Search

**What:** Repeatedly divide a sorted array in half until the target is found.

**When:** Sorted arrays only.

**Complexity:**

- Time: O(log n)
- Space: O(1)

**Example in C:**
```bash
int binary_search(int *arr, int size, int target)
{
	int	low = 0;
	int	high = size - 1;
	int	mid;

	while (low <= high)
	{
		mid = (low + high) / 2;
		if (arr[mid] == target)
			return (mid);
		else if (arr[mid] > target)
			high = mid - 1;
		else
			low = mid + 1;
	}
	return (-1);
}
```
___

# 📘 2. Sorting Algorithms
- Arrange data in a specific order (e.g., ascending or descending).
- Common types: Bubble Sort, Insertion Sort, Merge Sort, Quick Sort.
- Use case: Organizing lists, databases, and optimizing search operations.

## Bubble Sort

**What:** Repeatedly swap adjacent elements if out of order.

**When:** Educational; inefficient in real use.

**Complexity:**

- Time: O(n²)
- Space: O(1)

**Example in C:**
```bash
void bubble_sort(int *arr, int size)
{
	int	i;
	int	temp;
	int	swapped;

	swapped = 1;
	while (swapped)
	{
		swapped = 0;
		i = 0;
		while (i < size - 1)
		{
			if (arr[i] > arr[i + 1])
			{
				temp = arr[i];
				arr[i] = arr[i + 1];
				arr[i + 1] = temp;
				swapped = 1;
			}
			i++;
		}
	}
}
```

## Insertion Sort

**What:** Insert each element into its correct position in a sorted subarray.

**When:** Small or nearly sorted data.

**Complexity:**

- Time: O(n²) (best: O(n) if nearly sorted)
- Space: O(1)

**Example in C:**
```bash
void insertion_sort(int *arr, int size)
{
	int i;
	int j;
	int key;

	i = 1;
	while (i < size)
	{
		key = arr[i];
		j = i - 1;
		while (j >= 0 && arr[j] > key)
		{
			arr[j + 1] = arr[j];
			j--;
		}
		arr[j + 1] = key;
		i++;
	}
}
```

## Merge Sort (Divide and Conquer)

**What:** Recursively split the array, sort halves, merge.

**When:** Large datasets, stable sort.

**Complexity:**

- Time: O(n log n)
- Space: O(n) (extra array for merging)

## Quick Sort

**What:** Pick a pivot, partition, recursively sort.

**When:** Fast for most cases; widely used.

**Complexity:**

- Time: Best/Average: O(n log n); Worst: O(n²)
- Space: O(log n) (recursion stack)

___

# 📘 3. Recursion Basics

## Factorial

**What:** n! = n * (n-1)!

**Complexity:**

- Time: O(n)
- Space: O(n) (recursion)

**Example in C:**
```bash
int factorial(int n)
{
	if (n <= 1)
		return (1);
	return (n * factorial(n - 1));
}
```

## Fibonacci (Recursive)

**What:** Each term = sum of previous two.

**Complexity:**

- Naive recursion: O(2^n)
- With memoization: O(n)

___

# 📘 4. String Algorithms
- Efficiently find substrings or patterns within text.

- Examples:

  - Knuth-Morris-Pratt (KMP): Skips unnecessary comparisons.
  - Rabin-Karp: Uses hashing for multiple pattern searches.
  - Boyer-Moore: Skips sections of text when mismatches occur.

- Use case: Search engines, DNA analysis, plagiarism detection, spam filters.

## Naive Substring Search (strstr)

**What:** Compare the pattern with every possible position in the text.

**Complexity:** O(n * m) where n = text length, m = pattern length.

**Use when:** Small strings or simplicity matters.

## Knuth-Morris-Pratt (KMP)

**What:** Preprocess pattern to build a partial match (LPS) table; skips unnecessary comparisons.

**Complexity:** O(n + m)

**Use when:** Large text and pattern, need consistent performance.

## Rabin-Karp

**What:** Uses hashing to quickly compare substring hashes instead of characters one by one.

**Complexity:** Average O(n + m), worst O(n * m).

**Use when:** Multiple pattern searches or rolling hash scenarios.

## Boyer-Moore

**What:** Starts comparing from the end of the pattern and uses heuristics to skip big chunks of text when mismatch occurs.

**Complexity:** Best: sublinear time in practice, worst O(n * m).

**Use when:** Large alphabets and large text, very fast in real life.

## Palindrome Check

**What:** Reads same forward and backward.

**When:** Interview basics.

**Example in C:**
```bash
int is_palindrome(char *s)
{
	int	left = 0;
	int	right;

	right = 0;
	while (s[right])
		right++;
	right--;
	while (left < right)
	{
		if (s[left] != s[right])
			return (0);
		left++;
		right--;
	}
	return (1);
}
```

___

# Tree Algorithms

- Operate on hierarchical data structures.

- Examples:

  - Binary Search Tree (BST): Organizes data for quick search and insertion.
  - AVL Tree: Self-balancing BST.
  - Trie (Prefix Tree): Efficient for searching strings, used in autocomplete.

- Use case: Dictionaries, autocomplete, hierarchical data representations

___

# Graph Algorithms

- Solve problems related to graph theory, such as finding shortest paths or spanning trees.

- Examples:
  - Dijkstra's Algorithm: Finds shortest path from one node to others. Used in navigation and routing systems.
  - Kruskal’s/Prim’s Algorithm: Finds minimum spanning tree, used in network design.
  - Topological Sort: Orders tasks with dependencies, used in scheduling.

- Use case: Network optimization, task scheduling, mapping systems.

___

# Depth-First Search (DFS) & Breadth-First Search (BFS)

- Algorithms for traversing or searching trees or graphs.

- DFS explores as far as possible down each branch before backtracking.

- BFS explores all neighbors at the current depth before moving deeper.

- Use case: Maze solving, networking, topology analysis.

___

# Dynamic Programming

- Breaks problems into subproblems and solves each once, storing solutions.

- Examples: Longest Common Subsequence, 0-1 Knapsack Problem.

- Use case: Optimization problems, resource allocation.
