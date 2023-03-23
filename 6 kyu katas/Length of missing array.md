
## Description:

You get an array of arrays.
If you sort the arrays by their length, you will see, that their length-values are consecutive.
But one array is missing!

You have to write a method, that return the length of the missing array.

### Examples (input --> output):

```
Example:
[[1, 2], [4, 5, 1, 1], [1], [5, 6, 7, 8, 9]] --> 3
```

If the array of arrays is null/nil or empty, the method should return 0.

When an array in the array is null or empty, the method should return 0 too!
There will always be a missing element and its length will be always between the given arrays.

Have fun coding it and please don't forget to vote and rank this kata!

I have created other katas. Have a look if you like coding and challenges.

#### Алгоритм выполнения

- Длина отсутствующего массива всегда будет между длинами существующих массивов.


- Проверяем, не пустой ли переданный массив arr. Если да, то возвращаем 0.

- Проверяем, не содержит ли arr пустых подмассивов. Если содержит, то возвращаем 0.

- Сортируем arr по возрастанию длины подмассивов.

- Получаем длину первого (наименьшего) подмассива из отсортированного массива arr и присваиваем ее переменной expectedLength.

- Проходимся по отсортированному массиву arr. Если длина текущего элемента не равна expectedLength, то возвращаем expectedLength.

- Если в предыдущем шаге не был возвращен результат, то увеличиваем expectedLength на единицу и продолжаем проходиться по массиву arr до конца.

- Если не был найден ни один пропущенный элемент, то возвращаем 0.

Таким образом, находим пропущенную длину в массиве arr путем проверки последовательности длин подмассивов.
Если есть пропущенная длина, то алгоритм возвращает ее, иначе возвращает 0.


## Solution:
```javascript
function getLengthOfMissingArray(arr) {

  if (!arr || arr.length === 0) {     //является ли переданный массив - null / пустым.
    return 0;
  }

  for (let i = 0; i < arr.length; i++) {
    if (!arr[i] || arr[i].length === 0) {  //является ли  подмассив - null / пустым.
      return 0;
    }
  }

  const sortedArr = arr.sort((a, b) => a.length - b.length); //отсортируем массив по длинне подмассивов

  let expectedLength = sortedArr[0].length; //создадим переменную, в которой будет ожидаемая (самая меньшая длинна массива)

  for (let i = 0; i < sortedArr.length; i++) {
    if (sortedArr[i].length !== expectedLength) {
      return expectedLength;
    }
    expectedLength++;
  }

  return 0;
}


```