# DSA Practise

## Recursion
Its a technique in JS that a function calls itself until a specific base condition is met. This approach is particularly useful for solving problems that can be naturally broken down into smaller, similar sub-problems. 


### Recursion Fibonacci

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

//Big 0 Time Complexity - 0(n)
```

