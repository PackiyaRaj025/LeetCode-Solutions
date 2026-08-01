# Pascal's Triangle (LeetCode 118)

## 📝 Problem Statement
🔗 **Problem Link:** https://leetcode.com/problems/pascals-triangle/

Given an integer `numRows`, return the first `numRows` of **Pascal's Triangle**.

In Pascal's Triangle:

* The first and last element of every row is `1`.
* Every other element is the sum of the two elements directly above it.

### Example

**Input**

```text
numRows = 5
```

**Output**

```text
[
     [1],
    [1,1],
   [1,2,1],
  [1,3,3,1],
 [1,4,6,4,1]
]
```

---

# 💡 Solution (Python)

```python
class Solution(object):
    def generate(self, numRows):
        """
        :type numRows: int
        :rtype: List[List[int]]
        """
        pascal = []

        for i in range(numRows):
            row = []

            for j in range(i + 1):
                if j == 0 or j == i:
                    row.append(1)
                else:
                    pre_row = pascal[i - 1]
                    value = pre_row[j] + pre_row[j - 1]
                    row.append(value)

            pascal.append(row)

        return pascal
```

---

# 🔍 Algorithm

1. Create an empty list called `pascal`.
2. Loop from `0` to `numRows - 1`.
3. Create a new empty row.
4. For each position in the current row:

   * If it is the first or last position, add `1`.
   * Otherwise:

     * Get the previous row.
     * Add the two values directly above the current position.
5. Add the completed row to `pascal`.
6. After all rows are generated, return `pascal`.

---

# 📖 Explanation

* We build Pascal's Triangle **one row at a time**.
* Every row always starts and ends with `1`.
* The middle values are calculated using the previous row.

Formula:

```text
Current Value = Previous Row[j-1] + Previous Row[j]
```

For example:

```text
Previous Row:
1 3 3 1

Next Row:
1 (1+3)=4 (3+3)=6 (3+1)=4 1

Result:
1 4 6 4 1
```

---

# ⏱️ Complexity Analysis

**Time Complexity:** `O(n²)`

* There are `numRows` rows.
* The total number of elements generated is:

```text
1 + 2 + 3 + ... + n = n(n + 1) / 2
```

Therefore, the time complexity is:

```text
O(n²)
```

**Space Complexity:** `O(n²)`

* We store all rows of Pascal's Triangle.
* The total number of stored elements is:

```text
1 + 2 + 3 + ... + n = n(n + 1) / 2
```

Hence, the space complexity is:

```text
O(n²)
```

---

# ✅ Key Takeaways

* Build the triangle row by row.
* First and last elements are always `1`.
* Middle elements are the sum of two values from the previous row.
* Uses the previously computed row to generate the next row efficiently.
