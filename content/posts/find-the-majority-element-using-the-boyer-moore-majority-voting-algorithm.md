---
title: "Find the Majority Element Using the Boyer-Moore Majority Voting Algorithm"
date: 2023-07-18T07:03:22+08:00
draft: true
---

# Introduction

Recently I encountered a leetcode problem called [Majority Element](https://leetcode.com/problems/majority-element/description/), there are multiple ways to solve it, the most efficient of them all is called **the Boyer-Moore Majority Voting Algorithm**, whose time complexity is $O(n)$ and space complexity is $O(1)$. There are many posts online talking about the algorithm, but most of them don't give concrete mathematical proof of it. So in this post, I try to explain the algorithm thoroughly, including not only its mechanism and intuition but also a mathematical proof.

# Problem

Given an array `nums` of size $n$, return the majority element.

The majority element is the element that appears more than `⌊n / 2⌋` times. You may assume that the majority element always exists in the array.

**Example 1:**

```text
Input: nums = [3,2,3]
Output: 3
```

**Example 2:**

```text
Input: nums = [2,2,1,1,1,2,2]
Output: 2
```

# The Boyer-Moore Majority Voting Algorithm

There are a lot of ways to solve the problem, but the method I’ll introduce today would be the most efficient one, its time complexity is $O(n)$, and space complexity is $O(1)$. It’s called **the Boyer-Moore Majority Voting Algorithm**. The code of the algorithm is pretty easy, although it’s not that easy to prove its correctness. Unlike before, I’ll show the code first, walk through the process and prove its correctness later. I think you will better understand the algorithm this way.

As promised, this is the code, written in Java

```java
class Solution {
    public int majorityElement(int[] nums) {
        int count = 0;
        int element = -1;
        for (int num : nums) {
            if (count == 0) {
                element = num;
                count = 1;
            } else if (element == num) {
                count++;
            } else {
                count--;
            }
        }
        return element;
    }
}
```

First, we create two variables `count` and `element`. The initial value of `count` is 0, and the initial value of `element` could be any, we choose -1 here. Then we iterate through the `nums` array. In each iteration, we decide our operation based on the current conditions, we have three choices:

1. If `count` is 0, then we assign `num` to `element` and reset `count` to 1.
2. If `element` is equal to `num`, then we increase `count` by one.
3. Otherwise we decrease `count` by one.

At the end of the method, we return `element`. That’s all.

To see how the algorithm works, let’s suppose the `nums` array is `[1, 3, 3, 2, 3]` and go through the process step by step.

1. At first, `count` is 0, so we set `element` to 1 and `count` to 1.
2. In the second iteration, the current number is 3, which is different from `element` 1, so decrease `count` to 0
3. In the third iteration, `count` is 0, so we set `element` to 3 and `count` to 1.
4. In the fourth iteration, the current number 2 is different from `element` 3, so we decrease `count` to 0.
5. In the last iteration, `count` is 0, so we set `element` to the current number 3 and set `count` to 1.

In the end, we return `element` 3, which is the correct majority number.

# Intuition

The intuition behind the algorithm is that `count` can be taken as a vote for `element`. When we encounter a different value from `element`, we decrease the vote, when we encounter the same value as `element`, we increase the vote, so in the end, the majority number will have the most votes and win the contest.

# Proof

The above intuition is just helping you understand the problem, to prove its correctness, you need mathematical induction.

1. First, we assume that the algorithm works when `nums` length is 1, which is obvious.
2. Second, we assume that the algorithm works when `nums` length is less than n, we are going to prove its correctness when `nums` length is n.

To prove the second statement, we need to discuss two conditions:

1. The first number is the majority
2. The first number is not the majority.

## When the first number is the majority

In the first iteration, `element` is the majority number, and `count` is 1. There are also two possibilities for the `count` value:

1. It never drops to 0.
2. it drops to 0 in some iteration.

For the former case, `element` will always be the majority number, and the return value is also the majority, so the algorithm works in this case. We will discuss the latter case in more detail. Before doing that, let's first define some variables to help illustrate the point:

1. $k$: `count` drops to 0 after the $k$-th iteration.
2. $n$: The length of `nums`.
3. $m$: The majority number in `nums`.
4. $c$: The number of $m$ in `nums`.

For example, when `nums = [2, 2, 3, 3, 5, 2, 2]`, the values of those variables are:

- $k = 4$
- $n = 7$
- $m = 2$
- $c = 4$

We need to prove that $m$ is also the majority number in the remaining $n - k$ numbers. To see the necessity of the proof you need to remember that we have an assumption that the algorithm works when `nums` length is less than $n$. So if $m$ is the majority number in the remaining $n - k$ numbers, the algorithm will correctly output the majority number $m$ after the remaining $n - k$ iterations, which means the algorithm will output $m$ after the whole $n$ iterations, which means the algorithm works when `nums` length is $n$.

But how to prove that? We can use the following logic: Since `count` drops to 0 in the $k$-th iteration and the first number is $m$, we know that the number of $m$ in the first $k$ numbers is exactly $\frac{k}{2}$. To prove $m$ is also the majority in the remaining $n - k$ numbers, we need to prove $(c - \frac{k}{2}) \cdot 2 > n - k$, which is equivalent to $2c - k > n - k$. After adding $k$ at both sides of the equation, we get $2c > n$, which is true by the definition of $m$, the proof is done. So we know that the algorithm works correctly when the first number is the majority.

## When the first number is not the majority

Suppose the first number is $j$. Since $j$ is not the majority number, there has to be an iteration where `count` for $j$ becomes 0 for the first time, let’s say it happens after the $k$-th iteration. As before, We define the following variables:

1. $n$: The length of `nums`.
2. $m$: The majority number in `nums`.
3. $c$: The number of $m$ in `nums`.
4. $a$: The number of $m$ in the first $k$ numbers.

As before, we need to prove that $m$ is also the majority number in the remaining $n - k$ numbers, if we can do that, we will know that algorithm works when the first number is not the majority. Proving it is equal to proving the following equation:

$$2 \cdot (c - a) > n - k$$

To prove the equation, we first need to know that $a \le \frac{k}{2}$, because if $a > \frac{k}{2}$, then `count` would be greater than 0 after the $k$-th iteration. Also, notice that we have $2c > n$ by the definition of $m$. Now we have two equations, let's write them here:

$$2a <= k$$

$$2c > n$$

Let the second equation minus the first one, we get

$$2c - 2a > n - k$$

That is equivalent to

$$2 \cdot (c - a) > n - k$$

$c - a$ is the number of $m$ in the remaining $n - k$ numbers, so $2 \cdot (c - a) > n - k$ means $m$ is also the majority number in the remaining $n - k$ numbers. So the algorithm works when the first number is not the majority. The proof is done.

## Put everything together

In conclusion, we know that the algorithm works when `nums` length is $n$. From the mathematical induction given before, we know that the algorithm works for any `nums` that have a majority. Q.E.D.