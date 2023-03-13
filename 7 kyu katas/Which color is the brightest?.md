## Description:

One of the common ways of representing color is the RGB color model, in which the Red, Green, and Blue primary colors of light are added together in various ways to reproduce a broad array of colors.

One of the ways to determine brightness of a color is to find the value V of the alternative HSV (Hue, Saturation, Value) color model. Value is defined as the largest component of a color:

```
V = max(R,G,B)
```

You are given a list of colors in 6-digit hexidecimal notation #RRGGBB. Return the brightest of these colors!

Note that both input and output should use upper case for characters A, B, C, D, E, F.

### Examples (input --> output):

```
brightest(["#001000", "#000000"]) == "#001000"
brightest(["#ABCDEF", "#123456"]) == "#ABCDEF"

```

If there are multiple brightest colors, return the first one:

```
brightest(["#00FF00", "#FFFF00", "#01130F"]) == "#00FF00"

```

## Solution:

##### Алгоритм выполнения

- Пройти по всем цветам в списке.
- Для каждого цвета преобразовать его из 6-значного шестнадцатеричного представления в RGB значения R, G, B.
- Найти максимальное значение из R, G, B.
- Сохранить цвет с максимальным значением V.
- Вернуть цвет с максимальным значением V.

```javascript
function brightest(colors){
let arrayMax = [];

colors.forEach((color)=>{
//убираем решетку
   let hex = color.slice(1);
// преобразуем двузначные значения в десятичные числа
    let r = parseInt(hex.substring(0,2), 16);
    let g = parseInt(hex.substring(2,4), 16);
    let b = parseInt(hex.substring(4,6), 16);

    let v = Math.max(r,g,b)
//закидываем в массив наибольшие значения из каждого цвета
    arrayMax.push(v)
})

//найдем максимальную яркость
let maxV = Math.max(...arrayMax)

// находим по индексу число с наибольшим V и возвращаем из другого массива число с таким же индексом
for(let i = 0; i < arrayMax.length; i++){
        if (arrayMax[i] === maxV) {
        return colors[i]
      }
   }

}

```
