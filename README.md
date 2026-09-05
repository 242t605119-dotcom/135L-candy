# LeetCode 135 – Candy

## Problem

There are `n` children standing in a line. Each child has a rating represented by the integer array `ratings`.

You need to distribute candies according to these rules:

* Every child must receive at least one candy.
* A child with a higher rating than an adjacent child must receive more candies than that neighbor.

Return the **minimum number of candies** required.

## Example 1

**Input:**

```text
ratings = [1,0,2]
```

**Output:**

```text
5
```

A valid distribution is:

```text
[2,1,2]
```

Total candies:

```text
2 + 1 + 2 = 5
```

## Example 2

**Input:**

```text
ratings = [1,2,2]
```

**Output:**

```text
4
```

A valid distribution is:

```text
[1,2,1]
```

The third child does not have a higher rating than the second child, so one candy is enough.

## Approach

A useful way to solve this problem is to consider the ratings from **left to right** and then from **right to left**.

### Left-to-Right Pass

If a child has a higher rating than the child immediately before them, they must receive more candies.

For example:

```text
ratings = [1,2,3]
candies = [1,2,3]
```

### Right-to-Left Pass

We also need to satisfy the condition with the child on the right.

During the second pass, update the candy count whenever a child has a higher rating than the child to their right.

The final answer is the sum of the required candy counts.

## Algorithm

1. Create an array where every child initially receives `1` candy.
2. Traverse from left to right.
3. If `ratings[i] > ratings[i-1]`, give the current child one more candy than the previous child.
4. Traverse from right to left.
5. If `ratings[i] > ratings[i+1]`, update the current child's candies to satisfy the right-side condition.
6. Add all candy counts.
7. Return the total.

## Complexity

* **Time Complexity:** `O(n)`
* **Space Complexity:** `O(n)`

The ratings are traversed twice, and an additional array is used to store candy counts.

## Key Learning

This problem demonstrates how a **Greedy Algorithm** can be applied from two directions.

A single left-to-right pass cannot handle both neighboring conditions, so combining two passes ensures that every child satisfies the required rating relationships.

## LeetCode Details

* **Problem Number:** 135
* **Problem Name:** Candy
* **Difficulty:** Hard
* **Language:** Python 3
* **File:** `solution.py`

## Topics

* Array
* Greedy

## Author

T.Nandhini
