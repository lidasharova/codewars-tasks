## Description:

You are writing a function that takes two sets of arguments of arbitrary length. The return value will be the sum of the values of all of the arguments.

The function should contain at least 1 argument per set.

## Examples

```
calculate(1)(1) // should return 2
calculate(1,1)(1) // should return 3
calculate(1,1)(1,-1) // should return 2
calculate(2,4)(3,7,1) // should return 17
```

#### Алгоритм выполнения

- Создаем функцию calculate, которая принимает первый набор аргументов args1
- Функция calculate возвращает функцию, которая принимает второй набор аргументов args2
- Вторая функция возвращает сумму всех аргументов из args1 и args2

## Solution:

```javascript
function calculate(...args1) {
  return function (...args2) {
    return [...args1, ...args2].reduce((acc, cur) => acc + cur, 0);
  };
}
```
