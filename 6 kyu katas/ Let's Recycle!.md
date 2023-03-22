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

- создадим массив с корзинами(подмассивами) - в которые будем сортировать(4 подмассива - paper, glass,organic , plastic);
- пробежимся по входному массиву с объектами циклом for и на каждой  итерации для обьекта создадим условие;
- условие по значению двух св-в  -  material и secondMaterial;
- в зависимости от значения этих св-в будем добавлять type каждого объекта в определенный из 4х подмассивов;


## Solution:

```javascript
function recycle(array) {
   let bins = [
    [], // paper
    [], // glass
    [], // organic
    []  // plastic
  ];

  for (let item of array) {
    if (item.material === "paper") {
      bins[0].push(item.type);
    } else if (item.material === "glass") {
      bins[1].push(item.type);
    } else if (item.material === "organic") {
      bins[2].push(item.type);
    } else if (item.material === "plastic") {
      bins[3].push(item.type);
    }


    if (item.secondMaterial) {
      if (item.secondMaterial === "paper") {
        bins[0].push(item.type);
      } else if (item.secondMaterial === "glass") {
        bins[1].push(item.type);
      } else if (item.secondMaterial === "organic") {
        bins[2].push(item.type);
      } else if (item.secondMaterial === "plastic") {
        bins[3].push(item.type);
      }
    }
  }

  return bins;
}
```
