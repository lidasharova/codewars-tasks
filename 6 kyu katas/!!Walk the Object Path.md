## Description:

Implement the method find which takes in an two parameters object and path. The path will be a period-delimited string of properties that we will use to traverse through our object to find our target value.

### Edge Cases And Further Consideration

Be sure to handle passing array indices. For example, if we have an object:

```
 { people: ['John', 'Dave', 'Lisa'] }
```

and the path is 'people.1', the target value is 'Dave' which is the string at position 1 inside of the people array.
Also this method should handle invalid paths.
If we have an object

```
 { user: { name: 'Dan' } }
```

and the path is 'user.wallet.money', we should return undefined.
Valid paths are exclusive to properties on the object which are not inherited, in other words it is specific to this object and does not need to look up the prototype chain.

#### Алгоритм выполнения

- Разбить путь на отдельные свойства и сохранить их в массиве.
- Итерироваться по массиву свойств и проверять, что каждое следующее свойство является свойством текущего объекта. Если свойство не существует, вернуть undefined.
- Если свойство существует, перейти к следующему свойству и продолжить итерацию до тех пор, пока не будет найдено последнее свойство пути.
- Если последнее свойство существует и является массивом, то взять элемент массива с индексом, указанным в пути, и вернуть его значение.
- Если последнее свойство существует и не является массивом, то вернуть его значение.

## Solution:

```javascript
function find(object, path) {
  const properties = path.split('.');
  let currentObj = object;

  for (let i = 0; i < properties.length; i++) {
    const prop = properties[i];

    if (currentObj.hasOwnProperty(prop)) {
      currentObj = currentObj[prop];
    } else {
      return undefined;
    }
  }

  return currentObj;
}
```
