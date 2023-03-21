## Description:

You will be given a list of objects. Each object has type, material, and possibly secondMaterial. The existing materials are: paper, glass, organic, and plastic.

Your job is to sort these objects across the 4 recycling bins according to their material (and secondMaterial if it's present), by listing the type's of objects that should go into those bins.

Notes

- The bins should come in the same order as the materials listed above
- All bins should be listed in the output, even if some of them are empty
- If an object is made of two materials, its type should be listed in both of the respective bins
- The order of the type's in each bin should be the same as the order of their respective objects was in the input list

### Examples (input --> output):

```
input = [
  {"type": "rotten apples", "material": "organic"},
  {"type": "out of date yogurt", "material": "organic", "secondMaterial": "plastic"},
  {"type": "wine bottle", "material": "glass", "secondMaterial": "paper"},
  {"type": "amazon box", "material": "paper"},
  {"type": "beer bottle", "material": "glass", "secondMaterial": "paper"}
]

output = [
  ["wine bottle", "amazon box", "beer bottle"],
  ["wine bottle", "beer bottle"],
  ["rotten apples", "out of date yogurt"],
  ["out of date yogurt"]
]

```

#### Алгоритм выполнения

- создадим объект с корзинами - в который будем сортировать(4 ключа и пустые массивы);
- пробежимся по массиву с объектами методом forEach
- на каждом цикле сделаем деструктуризацию объекта на переменные type, material, secondMaterial
- напишем 4 условия для сортировки - и добавления type в определенный массив(корзину) по значению material и secondMaterial;
- создадим пустой массив, в  который поместим все значения из объекта(корзины)методом forEach и получим массив с подмассивами.



## Solution:

```javascript
function recycle(array) {
  const result = [];
  const bins = {
    paper: [],
    glass: [],
    organic: [],
    plastic: [],
  };

  array.forEach((item) => {
    const { type, material, secondMaterial } = item;
    if (material === 'paper') {
      bins.paper.push(type);
      if (secondMaterial === 'paper') {
        bins.paper.push(type);
      }
    } else if (material === 'glass') {
      bins.glass.push(type);
      if (secondMaterial === 'paper') {
        bins.paper.push(type);
      } else if (secondMaterial === 'glass') {
        bins.glass.push(type);
      }
    } else if (material === 'organic') {
      bins.organic.push(type);
      if (secondMaterial === 'plastic') {
        bins.plastic.push(type);
      }
    } else if (material === 'plastic') {
      bins.plastic.push(type);
      if (secondMaterial === 'organic') {
        bins.organic.push(type);
      }
    }
  });

  Object.values(bins).forEach((bin) => result.push(bin));
  return result;
}
```
