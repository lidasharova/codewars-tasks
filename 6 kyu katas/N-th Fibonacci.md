## Description:

I love Fibonacci numbers in general, but I must admit I love some more than others.

I would like for you to write me a function that, when given a number n (n >= 1 ), returns the nth number in the Fibonacci Sequence.

Because 2 is the 4th number in the Fibonacci Sequence.
For reference, the first two numbers in the Fibonacci sequence are 0 and 1, and each subsequent number is the sum of the previous two.

### Examples (input --> output):

```
   nthFibo(4) == 2

```

## Solution:

#### Алгоритм выполнения
Числа Фибоначчи
0, 1, 1, 2, 3, 5, 8, 13, 21, 34, 55, 89, 144, 233, 377, 610, 987, 1597, 2584, 4181, 6765, 10946, 17711, …

! мы должны вернуть число заданного индекса(n) !

[1]  [2]  [3]  [4]   [5]   [6]   [7]  [8]  …

0   0+1   0+1  1+1   2+1   3+2   5+3  8+5  …

0    1     1    2     3     5     8    13  …

https://learn.javascript.ru/task/fibonacci-numbers



### через рекурсию (при больших значениях n такое решение будет работать очень долго.)
```javascript
function nthFibo(n) {
  if (n === 1) return 0;
  if (n === 2) return 1;
  return nthFibo(n - 1) + nthFibo(n - 2);
}

```
```javascript
function nthFibo(n) {
return n < 2 ? 0 : n === 2 ? 1 : nthFibo(n - 1) + nthFibo(n - 2);
}
```


### через динамическое программирование снизу вверх.
напишем цикл, который начнёт с 1 и 1, затем из них получит fib(4) = 2
как их сумму,
затем fib(5 )как сумму предыдущих значений, затем fib(6) и так далее,
до финального результата.
На каждом шаге нам нужно помнить только значения двух предыдущих чисел последовательности,которые мы поместим в переменные a и b.

```javascript
function nthFibo(n) {
  if (n === 1) return 0;
  if (n === 2) return 1;
  if (n === 3) return 1;

  let a = 1;
  let b = 1;
  for (let i = 4; i <= n; i++) {
    let c = a + b;
    a = b;
    b = c;
  }
  return b;
}
```