# leet-day-57

# Combination Sum IV

## Problem Description

Given an array of distinct positive integers `nums` and a target integer `target`, you need to return the number of possible combinations that add up to the `target`.

You can use the numbers in `nums` as many times as you want to form combinations. The test cases are generated in such a way that the answer will fit in a 32-bit integer.

## Example

### Input

```cpp
nums = [1,2,3]
target = 4
```

### Output

```cpp
7
```

### Explanation

The possible combination ways to reach the target (4) are as follows:

- (1, 1, 1, 1)
- (1, 1, 2)
- (1, 2, 1)
- (1, 3)
- (2, 1, 1)
- (2, 2)
- (3, 1)

## Constraints

- 1 <= `nums.length` <= 200
- 1 <= `nums[i]` <= 1000
- All elements of `nums` are unique.
- 1 <= `target` <= 1000

## Approach

To solve this problem, we can use dynamic programming. We'll create an array `dp`, where `dp[i]` represents the number of combinations to reach the target `i`. We'll initialize `dp[0]` to 1 because there's one way to make a sum of 0, which is by not choosing any number.

Then, we'll iterate through the `dp` array from `1` to `target`. For each `i`, we'll iterate through the numbers in `nums` and update `dp[i]` by adding `dp[i - num]` for each `num` in `nums` if `i - num` is a valid index.

To handle potential overflow, we'll use an `unsigned long long` data type for the `dp` array. We'll also check for potential overflow before each addition to ensure that the result stays within the range of `unsigned long long`. Finally, we'll return `dp[target]` if it's within the range of `int`, or `0` otherwise.

## Complexity Analysis

The time complexity for this solution is O(target * nums.length), and the space complexity is O(target) to store the `dp` array.

This solution effectively handles potential overflow issues and provides the correct answer for the problem.

