## Description:

An isogram is a word that has no repeating letters, consecutive or non-consecutive. Implement a function that determines whether a string that contains only letters is an isogram. Assume the empty string is an isogram. Ignore letter case.

### Examples (input --> output):

```javascript
isIsogram "Dermatoglyphics" = true
isIsogram "moose" = false
isIsogram "aba" = false
```

## Solution:

#### Алгоритм выполнения
- нам нужно проверить повторяются ли буквы в слове (не важно в каком регистре)
- приведем строку к одному регистру
- создадим из нее коллекцию НЕ повторяющихся символов (Set)
- сравним длину Set и длину входной строки

```javascript
function isIsogram(str) {
  if (str === '') {
    return true;
  } else {
    let newStr = str.toLowerCase();
    let setStr = new Set(newStr);
    return setStr.size === str.length;
  }
}


//2 способ проверки повторяющейся буквы в оставшейся части слова
if (str.indexOf(str[i], i + 1) !== -1) {
      return false;
    }
```
