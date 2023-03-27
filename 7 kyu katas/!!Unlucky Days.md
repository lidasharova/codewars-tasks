## Description:
Friday 13th or Black Friday is considered as unlucky day. Calculate how many unlucky days are in the given year.

Find the number of Friday 13th in the given year.

Input: Year in Gregorian calendar as integer.

Output: Number of Black Fridays in the year as an integer.


## Examples
```
unluckyDays(2015) == 3
unluckyDays(1986) == 1
```

#### Алгоритм выполнения

- Создать объект даты, используя переданный год.
- Для каждого месяца в году, устанавливаем дату на 13 число и проверяем, является ли этот день пятницей.
- Если день является пятницей, увеличиваем счетчик на 1.
- Возвращаем счетчик.


## Solution:

```javascript
function unluckyDays(year){
  let unluckyCount = 0;
  for (let month = 0; month < 12; month++) {
    const d = new Date(year, month, 13);
    if (d.getDay() === 5) {
      unluckyCount++;
    }
  }
  return unluckyCount;
}

```
