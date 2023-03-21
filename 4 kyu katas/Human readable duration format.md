
## Description:
Your task in order to complete this Kata is to write a function which formats a duration, given as a number of seconds, in a human-friendly way.

The function must accept a non-negative integer. If it is zero, it just returns "now". Otherwise, the duration is expressed as a combination of years, days, hours, minutes and seconds.

It is much easier to understand with an example:

### Examples (input --> output):

```
* For seconds = 62, your function should return
    "1 minute and 2 seconds"
* For seconds = 3662, your function should return
    "1 hour, 1 minute and 2 seconds"
```
### For the purpose of this Kata,
a year is 365 days and a day is 24 hours.

Note that spaces are important.


### Detailed rules
The resulting expression is made of components like 4 seconds, 1 year, etc. In general, a positive integer and one of the valid units of time, separated by a space. The unit of time is used in plural if the integer is greater than 1.

The components are separated by a comma and a space (", "). Except the last component, which is separated by " and ", just like it would be written in English.

A more significant units of time will occur before than a least significant one. Therefore, 1 second and 1 year is not correct, but 1 year and 1 second is.

Different components have different unit of times. So there is not repeated units like in 5 seconds and 1 second.

A component will not appear at all if its value happens to be zero. Hence, 1 minute and 0 seconds is not valid, but it should be just 1 minute.

A unit of time must be used "as much as possible". It means that the function should not return 61 seconds, but 1 minute and 1 second instead. Formally, the duration specified by of a component must not be greater than any valid more significant unit of time.

### Алгоритм выполнения
```
определение количества значений из секунд

1 год = (60сек * 60мин * 24ч * 365 дн)
1 день = (60сек * 60мин * 24ч)
1 час = (60сек * 60мин)
1 минута = 60сек
```

- создадим переменные для каждой величины времени
#### лет = (секунды /   (60сек * 60мин * 24ч * 365 дн));
количество полных лет в секундах - делим общее количество секунд на количество секунд в одном году
 (который принимается равным 365 дней)
- секунды / год в секундах

#### дней = (секунды % (60сек * 60мин * 24ч * 365дн)) / (60сек * 60мин * 24ч);
количество полных дней, оставшихся после вычисления полных лет. Для этого сначала вычисляется остаток от деления на количество секунд в году (seconds % (60 * 60 * 24 * 365)), и затем этот остаток делится на количество секунд в одном дне (60 секунд * 60 минут * 24 часа). Результат округляется до целого числа.
- остаток / день в сек

#### часы = (секунды % (60сек * 60мин * 24ч)) /  (60сек * 60мин);
количество полных часов, оставшихся после вычисления полных лет и дней. Вычисляется остаток от деления на количество секунд в сутках (seconds % (60 * 60 * 24)), и затем этот остаток делится на количество секунд в одном часе
(60 минут * 60 секунд)
- остаток / час в сек

#### минуты = (секунды % (60сек * 60мин))  / 60 сек;
количество полных минут, оставшихся после вычисления полных лет, дней и часов.
Вычисляется остаток от деления на количество секунд в одной минуте (60 секунд), и округляется.
- остаток / 60 сек


#### остатки секунд = секунды % 60;
количество оставшихся секунд, не учтённых в расчёте на предыдущих шагах. Для этого вычисляется остаток от деления на 60 (количество секунд в минуте), и полученный остаток и будет количеством оставшихся секунд.
- остаток / минута в сек
#### далее
- создадим массив в который будем добавлять значения, соответствующее кол-ву значения;
- достанем последний элемент из итогого массивa ( если там больше одного значения);
- соединим массив в строку(если в нем больше 1 элемента) и добавим последний элемент, поставиа перед ним 'and' ;
- иначе просто сделаем строку из массива


```javascript
function formatDuration (seconds) {
  if (seconds === 0) {
    return "now";
  }
  if (seconds === 1) {
    return "1 second";
  }
  if (seconds === 3600) {
    return "1 hour";
  }
  let years = Math.floor(seconds / (60 * 60 * 24 * 365));
  let days = Math.floor((seconds % (60 * 60 * 24 * 365)) / (60 * 60 * 24));
  let hours = Math.floor((seconds % (60 * 60 * 24)) / (60 * 60));
  let minutes = Math.floor((seconds % (60 * 60)) / 60);
  let remainingSeconds = seconds % 60;

  let result = [];

  if (years > 0) {
    result.push(years + (years === 1 ? " year" : " years"));
  }

  if (days > 0) {
    result.push(days + (days === 1 ? " day" : " days"));
  }

  if (hours > 0) {
    result.push(hours + (hours === 1 ? " hour" : " hours"));
  }

  if (minutes > 0) {
    result.push(minutes + (minutes === 1 ? " minute" : " minutes"));
  }

  if (remainingSeconds > 0) {
    result.push(remainingSeconds + (remainingSeconds === 1 ? " second" : " seconds"));
  }

  if (result.length > 1) {
    let last = result.pop();
    result = result.join(", ") + " and " + last;
  } else {
    result = result.join("");
  }

  return result;
}

```
