## Description:

You are given an array. Complete the function that returns the number of ALL elements within an array, including any nested arrays.

### Examples (input --> output):

```
 []                  -->  0
[1, 2, 3]            -->  3
["x", "y", ["z"]]    -->  4
[1, 2, [3, 4, [5]]]  -->  7
```

The input will always be an array.

#### Алгоритм выполнения

- для подсчета всех элементов массива (в том числе вложенных) мы применим [рекурсию](https://learn.javascript.ru/recursion)
  (вызов ф-ции самой себя т.к. действия будут повторяться при наличии вложенных массивов)

- и метод [Array.isArray()](https://developer.mozilla.org/ru/docs/Web/JavaScript/Reference/Global_Objects/Array/isArray)

- нужно учитывать, что вложенный массив является элементом родительского массива а значит его тоже нужно прибавлять к счетчику прежде чем повторно вызвать ф-цию (count += 1 + deepCount(a[i]))

```javascript
function deepCount(a) {
  let count = 0;
  for (let i = 0; i < a.length; i++) {
    if (Array.isArray(a[i])) {
      count += 1 + deepCount(a[i]); // рекурсивный вызов
    } else {
      count++;
    }
  }
  return count;
}
```
