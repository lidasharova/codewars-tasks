## Description:

Johnny is a farmer and he annually holds a beet farmers convention "Drop the beet".

Every year he takes photos of farmers handshaking. Johnny knows that no two farmers handshake more than once. He also knows that some of the possible handshake combinations may not happen.

However, Johnny would like to know the minimal amount of people that participated this year just by counting all the handshakes.

Help Johnny by writing a function, that takes the amount of handshakes and returns the minimal amount of people needed to perform these handshakes (a pair of farmers handshake only once).

### Examples (input --> output):

```
getParticipants(0) --> 0
getParticipants(1) --> 2
getParticipants(3) --> 3
getParticipants(6) --> 4
getParticipants(7) --> 5

```

#### Алгоритм выполнения

- определим формулу подсчета рукопожатий
```
кол-во рукопожатий = n( n - 1 ) /2
n = кол-во человек
```
формула получается путем суммирования чисел от 1 до n-1
(то есть количество рукопожатий первого человека с остальными людьми), что равно n-1, умноженному на n (то есть количество людей) и разделенному на 2 (так как каждое рукопожатие учитывается дважды - для двух людей).


##### Логический способ решения


 - создадим переменную =  кол-во участников;
 - напишем цикл while и будем постепенно увеличивать количество участников и проверять,
 достигли ли мы заданного количества рукопожатий.
 Как только мы достигнем нужного количества рукопожатий, мы вернем количество участников.
```
 кол.во рукопожатий  = (кол-во участников * (кол-во участников - 1) / 2)
 ```

```javascript
   while (рукопожатия > фермеры * (фермеры - 1) / 2){
    фермеры ++
  }

```


##### Математический способ решения
подробное обьяснение подобной задачи есть тут https://nazva.net/797/

###### Формула расчета людей по известному кол-ву рукопожатий:
n(n-1) = x * 2
n - кол-во людей
x - кол-во рукопожатий

переписываем в квадратное уравнение
n^2 - n - 2x = 0
Квадратное уравнение имеет два корня, которые можно вычислить с помощью формулы корней квадратного уравнения:
x1,2 = (-b ± √D) / 2a
D = b^2 - 4ac
a = 1, b = -1, c = -2x
D = b^2 - 4ac = 1 + 8x
n1,2 = (1 ± √(1 + 8x))
после решения этого квадратного уравнения
формула для поиска кол-ва человек:
```
(1 + sqrt(1 + 8 * кол-во рукопожатий)) / 2

```
```javascript
Math.ceil((1 + Math.sqrt(1 + 8 * кол-во рукопожатий)) / 2);
```




## Solution:

#### 1 solution way
```javascript
function getParticipants(handshakes){
  if(handshakes === 0){
      return 0;
  } else {
   return Math.ceil((1+ Math.sqrt(1 + 8 * handshakes)) / 2);
  }
}
```
#### 2 solution way
```javascript
function getParticipants(handshakes){
  let farmers = 0
  while(handshakes > farmers * (farmers - 1) / 2){
    farmers++
  }
  return farmers
}
```