## Description:
We want to create a function, which returns an array of functions, which return their index in the array. For better understanding, here an example.

## Examples
```
var callbacks = createFunctions(5); // create an array, containing 5 functions

callbacks[0](); // must return 0
callbacks[3](); // must return 3
```
We already implemented that function, but when we actually run the code, the result doesn't look like what we expected. Can you spot, what's wrong with it? A test fixture is also available

#### Алгоритм выполнения

- Задача заключается в создании функции, которая возвращает массив из функций, каждая из которых возвращает свой индекс в этом массиве.
Например, если мы вызываем createFunctions(5), то получаем массив из 5 функций, каждая из которых возвращает свой индекс в этом массиве.

- Нам нужно исправить реализацию функции createFunctions, чтобы она возвращала массив функций с правильными индексами.
- Способ решения этой задачи заключается в использовании замыканий. Мы можем создать функцию, которая возвращает функцию, которая сохраняет индекс в замыкании.


## Solution:

```javascript

function createFunctions(n) {
  var callbacks = [];
  for (var i = 0; i < n; i++) {
    callbacks.push(function(index) {
      return function() {
        return index;
      };
    }(i));
  }
  return callbacks;
}


```
