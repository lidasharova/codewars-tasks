
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

- Длина отсутствующего массива всегда будет между длинами существующих массивов!!!.


- Проверяем, не пустой ли переданный массив. Если да, то возвращаем 0.

- Проверяем, нет ли пустых подмассивов. Если содержит, то возвращаем 0.

- Сортируем входной массив по возрастанию длины подмассивов.
```

индекс     0      1         2             3
       [  [1], [1, 2], [4, 5, 1, 1],[5, 6, 7, 8, 9] ]

длина      1       2       4               5
```

- Получаем длину первого (наименьшего) подмассива из отсортированного массива и присваиваем ее переменной(искомая длина)

- Проходимся по отсортированному массиву. Если длина текущего элемента НЕ равна! искомой длине, то возвращаем эту переменную.

- Если искомая длина РАВНА длине текущего подмассива, то  мы увеличиваем "искомую длину" на единицу и продолжаем проходиться по массиву до конца;

- Если пропущенный подмассив находится !в конце! то "искомая длина" все равно увеличится на 1 и вернется
тк длина цикла равна длине массива, а индекс последнего элемента меньше длины на 1;

- Если не была найдена "искомая длина", то возвращаем 0.

Таким образом, находим пропущенную длину в массиве путем проверки всех длин подмассивов с переменной "искомой длины".


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

  //отсортируем массив по длинне подмассивов
  const sortedArr = arr.sort((a, b) => a.length - b.length);

   // [  [1], [1, 2], [4, 5, 1] ,[6, 7, 8, 9] ]

//создадим переменную, в которой будет ожидаемая длина пропущенного подмассива (самая меньшая длинна массива)
  let length = sortedArr[0].length;

  for (let i = 0; i <= sortedArr.length; i++) {
    if (sortedArr[i].length !== length) {
      return length;      //если искомая длина НЕ равна длине текущего подмассива - то вернем найденную длину(это ответ)
    }else {
    length ++;         //если равен, то идем дальше - увеличив искомую длинну на 1
    }
  }
  return 0; //если ничего не нашли вернем 0
}

```