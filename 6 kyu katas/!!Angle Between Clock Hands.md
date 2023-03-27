## Description:
Given a Date (in JS and Ruby) or hours and minutes (in C and Python), return the angle between the two hands of a 12-hour analog clock in radians.

## Notes:
- The minute hand always points to the exact minute (there is no seconds hand).
- The hour hand does not "snap" to the tick marks: e.g. at 6:30 the angle is not 0 because the hour hand is already half way between 6 and 7.
- Return the smaller of the angles ( <= π ).
- Return π if the hands are opposite.

## Examples
```
at noon the angle is: 0
at 3:00 the angle is: π/2 (90 degrees)
at 6:00 the angle is: π (180 degrees)
at 9:00 the angle is: π/2 (90 degrees)
```

#### Алгоритм выполнения
- Получаем значение часов и минут из даты, переданной в качестве аргумента функции.
- Вычисляем угол, который образует минутная стрелка с положением 12 на циферблате. Для этого умножаем количество минут на 6 (360 градусов / 60 минут = 6 градусов в 1 минуте).
- Вычисляем угол, который образует часовая стрелка с положением 12 на циферблате. Для этого сначала вычисляем количество часов в 12-часовом формате, т.е. берем остаток от деления на 12 и добавляем долю от часа, которую занимают минуты. Затем умножаем полученное число на 30 (360 градусов / 12 часов = 30 градусов в 1 часе).
- Вычисляем разницу между углами минутной и часовой стрелок. Если полученный угол больше 180 градусов, то находим дополнительный угол до 360 градусов, иначе берем исходный угол.
- Возвращаем угол в радианах, который получили в пункте 4.

## Solution:

```javascript
function handAngle(date) {
  // Получаем значения часов и минут из даты
  const hours = date.getHours();
  const minutes = date.getMinutes();

  // Вычисляем углы между стрелками в градусах
  const minuteAngle = 360 * minutes / 60;
  const hourAngle = 360 * (hours % 12 + minutes / 60) / 12;
  const angle = Math.abs(hourAngle - minuteAngle);

  // Приводим угол к наименьшему значению (<= 180 градусов)
  if (angle > 180) {
    return Math.PI * 2 - angle * Math.PI / 180;
  } else {
    return angle * Math.PI / 180;
  }
}
```
