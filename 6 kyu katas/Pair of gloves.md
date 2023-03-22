
## Description:
Pair of gloves
Winter is coming, you must prepare your ski holidays. The objective of this kata is to determine the number of pair of gloves you can constitute from the gloves you have in your drawer.

Given an array describing the color of each glove, return the number of pairs you can constitute, assuming that only gloves of the same color can form pairs.

### Examples (input --> output):
```
input = ["red", "green", "red", "blue", "blue"]
result = 2 (1 red pair + 1 blue pair)

input = ["red", "red", "red", "red", "red", "red"]
result = 3 (3 red pairs)
```

#### Алгоритм выполнения
- создаем пустой объект для хранения количества перчаток каждого цвета ;
- пробегаем по массиву forEach и в этот обьект добавляем ключи-цвет: а значение - их количество;
{red: 5, green: 1}
- считаем количество пар перчаток каждого цветa, проходя по полученному обьекту циклом
- каждую итерацию делим значение каждого ключа на 2 и увеличиваем счетчик пар
- округляем значение до меньшего целого



## Solution:


```javascript
function numberOfPairs(gloves) {
  // создаем объект для хранения количества перчаток каждого цвета
  const colorCounts = {};
let pairsCount = 0;

  // считаем количество перчаток каждого цвета
  gloves.forEach(color => {
    if (color in colorCounts) {
      colorCounts[color]++;
    } else {
      colorCounts[color] = 1;
    }
  });


  // считаем количество пар перчаток каждого цвета

  for (let color in colorCounts) {
     pairsCount += Math.floor(colorCounts[color] / 2);
  }

  return pairsCount;
}
```