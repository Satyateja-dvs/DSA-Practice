# DSA Practise
 - An algorithm is the set of well-defined instructions to solve a particular problem

## Space Complexity
![Space Complexity](assets/space-complexity.png)

## Big O Trend
![Big O Trend](assets/big-o-trend.png)

## Big O Guide - Cheat Sheet
![Big O Guide](assets/big-o-guide.png)

## Few points to note
 - Multiple algorithms exist for the same problem and there is no one right solution. Different algorithms work well under different constraints.
 - The same algorithm with the same programming language can be implemented in different ways.

# Math Algorithms
 - Fibonacci sequence
 - Factorial of a number
 - Prime number
 - Power of two
 - Recursion

## Recursion
Its a technique in JS that a function calls itself until a specific base condition is met. This approach is particularly useful for solving problems that can be naturally broken down into smaller, similar sub-problems. 


### 1. Recursion Fibonacci

The Fibonacci sequence is a series of numbers where each number is the sum of the two preceding ones, typically starting with 0 and 1.

In general, lets say ``F(n) = F(n-1) + F(n-2)`` with the base condition of F(0) = 0 and F(1) = 1

``` jsx
function recursiveFibonacci(n) {
  if (n < 2) {
    return n;
  }
  return recursiveFibonacci(n - 1) + recursiveFibonacci(n - 2);
}

console.log(recursiveFibonacci(0)); // 0
console.log(recursiveFibonacci(1)); // 1
console.log(recursiveFibonacci(2)); // 1
console.log(recursiveFibonacci(3)); // 2
console.log(recursiveFibonacci(4)); // 3
console.log(recursiveFibonacci(5)); // 5
console.log(recursiveFibonacci(6)); // 8

//Big 0 Time Complexity - 0(n^2)
```
#### Explanation for Time Complexity for Recursion Fibonacci
![Fibonacci](assets/recursive-fibonacci.png)

- With the above screenshot, the each number has 2 preceeding values and The recursive time complexity for each iteration is 2^n. So, the time complexity for the Big O notation is ***0(n^2)**

### 2. Recursion Factorial
The factorial of a non-negative integer 'n' (denoted as n!) is the product of all positive integers less than or equal to 'n'.

For Example, 
```jsx
  5! = 5 * 4 * 3 * 2 * 1 = 120
  4! = 4 * 3 * 2 * 1 = 24
  3! = 3 * 2 * 1 = 6
  2! = 2 * 1 = 2
  1! = 1
  0! = 1 // as per the math algorithm
```

To generalise the recursion for the factorial,

```jsx
5! = 5 * 4!
4! = 4 * 3!
3! = 3 * 2!
2! = 2 * 1!
```

So, now we can prepare the formulae i.e., **n! = n * (n-1)!**

```jsx
function recursiveFactorial(n) {
  if (n === 0) return 1;

  return n * recursiveFactorial(n - 1);
}

console.log(recursiveFactorial(0)); // 0
console.log(recursiveFactorial(1)); // 1
console.log(recursiveFactorial(2)); // 1
console.log(recursiveFactorial(3)); // 2
console.log(recursiveFactorial(5));

//Big 0 Time Complexity - 0(n)
```

#### Explanation for Time Complexity for Recursion Factorial
- Each number executes 5 times. i.e., 5 executes 5 times, 5x4x3x2x1. Then 4 executes 4 times, ie., 4x3x2x1. As n increases the no.of instructions increases at the same pace. So, Big O is Linear Time complexity in the case of Recursive Factorial of a number. So, it is **0(n)**



# Search Algorithm
1. Linear Search
2. Binary Search
3. Recursive Binary Search

> Note: The approach remains the same as Math Algorithms

## 1. Linear Search Psuedo Code - Finding the index of a given number
**Problem** - Given a array of 'n' elements and a target element 't', find the index of 't' in the array. Return -1 if the target element is not found.

> Problem: arr = [-5, 2, 10, 4, 6]; // Should return 2

- Start at the first element in the array and move towards the last.
- At each element though, check if the element is equal to the target element.
- If element found, return the index of the element If element not found, return -1

**Solution: 1**
``` jsx
function linearSearch (arr, target) {
  for (let i = 0; i ‹ arr.length; i++) {
    if (arr[i] === target） {
      return i
    }
  }
  return -1
}
console.log(linearSearch ([-5, 2, 10, 4, 6], 10)) // 2 console. log(linearSearch([-5, 2, 10,4, 61, 6)) // 4
console.log(linearSearch([-5, 2, 10,4, 61, 20)) // -1
```

**Solution: 2**

```jsx
function linearSearch(n) {
  const arr = [-5, 2, 10, 4, 6];
  return arr.findIndex((ele) => ele === n);
}

console.log(linearSearch(10)); // Should return 2
console.log(linearSearch(6)); // Should return 4
console.log(linearSearch(20)); // Should return -1
```

#### Time Complexity

 - Our Function contains only 1 for loop and by our cheat sheet(attached in the top of the Readme), for loop the Big O is Linear Time Complexity. The number of values increases the number of execution also increases.
 - So, Big O is  ***0(n)***


## 2. Binary Seach
**Problem** - Given a sorted array of 'n' elements and a target element 't', find the index of 't' in the array. Return -1 if the target element is not found.

```jsx
arr = [1-5, 2, 4, 6, 10], t = 10 -> Should return 4
arr = [-5, 2, 4, 6, 10], t = 6 -> Should return 3
```

> NOTEℹ️: Binary Search only works on sorted arrays. We can also do a linear search by sorting an array first and then apply Binary Search.


### Binary Search Psuedo Code - Finding the index of a given number
![Binary Search](assets/binary-search-psudo-code.png)

- If the array is empty, return -1 as the element cannot be found.
- If the array has elements, find the middle element in the array. If target is equal to the middle element, return the middle element index.
- If target is less than the middle element, binary search left half of the array.
- If target is greater than middle element, binary search right half of the array.

```jsx
function binarySearch(array, target) {
  let LeftIndex = 0;
  let RightIndex = array.length - 1

  while(LeftIndex <= RightIndex) {
    let middleIndex = Math.floor((LeftIndex + RightIndex) / 2);
    if (target < array[middleIndex]) {
      RightIndex = middleIndex - 1;
    }
    else
      if (target > array[middleIndex])
        LeftIndex = middleIndex + 1;
      else
        if (target === array[middleIndex])
          return middleIndex
  }
  return -1;
}

console.log(binarySearch([-3, -2, 1, 2, 3, 5], 2)); // Should return 3
```
#### Time Complexity

The function reduces by half when the iteration continues, as per the cheat sheet if it reduces by half then the Big O is also logarithmic **O(log n)**

## 3. Recursive Binary Search

``` jsx
function recursiveBinarySearch(array, target) {
  let LeftIndex = 0;
  let rightIndex = array.length - 1;
  return search(array, target, LeftIndex, rightIndex)
}

function search(array, target, LeftIndex, rightIndex) {
  while (LeftIndex <= rightIndex) {
    let middleIndex = Math.floor((LeftIndex + rightIndex) / 2);
    if (target === array[middleIndex]) {
        return middleIndex;
    }
    if (target < array[middleIndex])
        return search(array, target, LeftIndex, middleIndex - 1)
    else
        return search(array, target, middleIndex + 1, rightIndex)
  }
  return -1
}

console.log(recursiveBinarySearch([-3, -2, 1, 2, 3, 5], 5)); // Should return 5
```
#### Time Complexity

The function reduces by half when the iteration continues, as per the cheat sheet if it reduces by half then the Big O is also logarithmic **O(log n)**


# Sort Algorithm
- Bubble Sort
- Insertion Sort
- Quick Sort
- Merge Sort

> The approach remains the same as Math and Search Algorithms

## Bubble sort
### Problem - Given an array of integers, sort the array.
const arr = [-6, 20, 8, -2, 4]
bubbleSort(arr) => Should return [-6, -2, 4, 8, 20]

### Solution
  - We know that we start the first element in the array and compare it wih the adjacent element till we reach the last element and that ***sounds like a loop***

```jsx
  function bubbleSort(arr) {
    let swapped;
    do {
      swapped = false;
      for(let i=0; i<arr.length - 1; i++) {
        if(arr[i] > arr[i+1]) {
            let temp = arr[i];
            arr[i] = arr[i+1]
            arr[i+1] = temp;
            swapped= true
        }
      }
    }
    while(swapped)
    
    return arr
  }

  console.log(bubbleSort([-6, 20, 8, -2, 4])) // [-6, -2, 4, 8, 20]
```

#### Time Complexity
Our code has 2 loops, for loop is nested inside do-while loop. From our sheet its pretty evident that it is quadratic time complexity