
## Description:
Given a string made of digits [0-9], return a string where each digit is repeated a number of times equals to its value.

### Examples (input --> output):

```
explode("312") ----> "333122"

explode("102269") ----> "12222666666999999999"
```

## Solution:

#### Алгоритм выполнения
- создадим массив в который будем добавлять цифры
- пройдемся по входному числу
- внутри цикла создадим еще один цикл длинной равной текущей цифре и каждую итерацию будем добавлять цифру в массив необходимое кол-во раз
- вернем итоговый массив, соединив его элементы в число

```javascript
function explode(s) {
  let newArray = [];
      for(let i = 0 ; i< s.length; i++){
       for (let l = 0 ; l< Number(s[i]); l++ ){
          newArray.push(s[i])
        }
 }
return newArray.join('')
}

```
