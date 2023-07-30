## Description:
You probably know about Function.prototype.bind method in JavaScript. It returns a copy of the original function but this function will always be called in the specified context. The problem is that you can't rebind another context any more.


```javascript
var func = function () {
  return this.prop;
};
var obj1 = {prop: 1},
    obj2 = {prop: 2};

func = func.bind(obj1);
func(); // Will produce 1

func = func.bind(obj2);
func(); // Will also produce 1 :(

```

Your task is override the native Function.prototype.bind method by a new one that will allow you to rebind context multiple times. In this kata you don't need to worry about currying, testing function will never get params.

#### Алгоритм выполнения
- Создайте новую функцию rebind() для объекта Function.prototype, которая принимает контекст и возвращает новую функцию с этим контекстом.

- Функция rebind() должна сохранять исходную функцию и все ранее привязанные контексты в массиве.

- При вызове новой функции с помощью rebind(), она должна вызывать исходную функцию в последнем привязанном контексте.

- Если при вызове новой функции с помощью rebind() передан новый контекст, он должен быть добавлен в массив привязанных контекстов.

- Переопределить Function.prototype.bind на созданную rebind() функцию

https://stackoverflow.com/questions/75743566/power-bind-codewars-task

## Solution:

```javascript


```
