# Python Skill

## When to use this skill
Use this skill whenever the user asks for Python code to be written, explained,
debugged, or optimized — including algorithms, data structures, and general
scripting tasks.

## Guidelines for writing Python code
- Write clean, readable code with meaningful variable names.
- Include a short docstring explaining what the function does.
- Add type hints where helpful.
- Prefer built-in library solutions over external dependencies for simple tasks.
- Explain time and space complexity for algorithm questions.

## Example: Binary Search
```python
def binary_search(arr: list[int], target: int) -> int:
    """Return the index of target in sorted arr, or -1 if not found."""
    low, high = 0, len(arr) - 1
    while low <= high:
        mid = (low + high) // 2
        if arr[mid] == target:
            return mid
        elif arr[mid] < target:
            low = mid + 1
        else:
            high = mid - 1
    return -1
```
Time complexity: O(log n). Space complexity: O(1).
