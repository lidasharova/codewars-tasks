## Story
Your online store likes to give out coupons for special occasions. Some customers try to cheat the system by entering invalid codes or using expired coupons.

## Task
Your mission:
Write a function called checkCoupon which verifies that a coupon code is valid and not expired.

A coupon is no more valid on the day AFTER the expiration date. All dates will be passed as strings in this format: "MONTH DATE, YEAR".

## Examples

```
checkCoupon("123", "123", "July 9, 2015", "July 9, 2015")  ===  true
checkCoupon("123", "123", "July 9, 2015", "July 2, 2015")  ===  false
```

#### Алгоритм выполнения

- Преобразовать даты из строкового формата в объект Date.
- Сравнить дату использования купона с датой истечения срока действия купона.
- Если дата использования купона находится в пределах срока действия купона (или на дату истечения), вернуть true, иначе вернуть false.

Функция принимает 4 параметра: введенный код купона, правильный код купона, текущую дату и дату истечения срока действия купона. Функция сравнивает введенный код купона с правильным кодом и преобразует даты из строкового формата в объект Date. Затем функция сравнивает текущую дату с датой истечения срока действия купона и возвращает true, если текущая дата находится в пределах срока действия купона, иначе - false.

## Solution:

```javascript
function checkCoupon(enteredCode, correctCode, currentDate, expirationDate) {
  var current = new Date(currentDate);
  var expiration = new Date(expirationDate);
  return enteredCode === correctCode && current <= expiration;
}

```
