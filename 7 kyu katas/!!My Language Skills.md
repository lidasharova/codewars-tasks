## Description:
You are given a dictionary/hash/object containing some languages and your test results in the given languages. Return the list of languages where your test score is at least 60, in descending order of the scores.

Note: the scores will always be unique (so no duplicate values)

## Examples
```
{"Java": 10, "Ruby": 80, "Python": 65}    -->  ["Ruby", "Python"]
{"Hindi": 60, "Dutch" : 93, "Greek": 71}  -->  ["Dutch", "Greek", "Hindi"]
{"C++": 50, "ASM": 10, "Haskell": 20}     -->  []
```


#### Алгоритм выполнения

- Создайте пустой массив result.
- Итерируйте по каждой паре ключ-значение в объекте.
- Если значение больше или равно 60, добавьте пару ключ-значение в массив result.
- Отсортируйте массив result в порядке убывания значений.
- Верните массив ключей из массива result.

## Solution:

```javascript
function myLanguages(results) {
  const result = [];

  for (const [language, score] of Object.entries(results)) {
    if (score >= 60) {
      result.push({ language, score });
    }
  }

  result.sort((a, b) => b.score - a.score);

  return result.map(({ language }) => language);
}


```
