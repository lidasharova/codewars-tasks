## Description:
In this kata you're expected to sort an array of 32-bit integers in ascending order of the number of on bits they have.

E.g Given the array [7, 6, 15, 8]

- 7 has 3 on bits (000...0111)
- 6 has 2 on bits (000...0011)
- 15 has 4 on bits (000...1111)
- 8 has 1 on bit (000...1000)


So the array in sorted order would be [8, 6, 7, 15].

In cases where two numbers have the same number of bits, compare their real values instead.

E.g between 10 (...1010) and 12 (...1100), they both have the same number of on bits '2' but the integer 10 is less than 12 so it comes first in sorted order.

Your task is to write the function sortBybit() that takes an array of integers and sort them as described above.

Note: your solution has to sort the array in place.
### Examples (input --> output):
```
[3, 8, 3, 6, 5, 7, 9, 1]   =>    [1, 8, 3, 3, 5, 6, 9, 7]
```

#### Алгоритм выполнения

- решение задачи будет состоять из нескольких ф-ций

- 1 ф-ция получения суммы единиц двоичного представления входного числа
	* переводим число в двоичную запись (получаем строку //'00101')
	* создаем массив из цифр этого числа ( получился массив строк //['0','0','1','0','1'])
	* находим сумму единиц с помощью метода reduce(он складывает все цифры в массиве),
	при этом необходимо перевести значение которое прибавляется в число тк массив состоял из строк (parseInt(currentValue))
	* возвращаем сумму единичек

- 2 ф-ция (Компаратор) сравнения двух входных чисел
	* получаем суммы двух сравниваемых чисел с помощью ф-ции выше
	* если суммы равны, то сравниваем сами числа
	* если суммы не равны то сравниваем суммы

- сортируем входной массив с помощью метода sort  и ф-ции компаратора и получаем измененный массив

## Solution:

```javascript
function sortByBit(arr) {

//ф-ция получения суммы единиц двоичного представления входного числа
function getSumNumber(num){
// переводим каждое число массива в двоичную систему
      let bitString = (num).toString(2)  //'00101'
      let arrayBinNumber = Array.from(bitString)   //['0','0','1','0','1']
      let sumBin = arrayBinNumber.reduce(
  (accumulator, currentValue) => accumulator + parseInt(currentValue),
  0);

return sumBin;
}


//ф-ция (Компаратор) сравнения двух сумм битов
   function cmp(a,b){
//найдем сумму битов двоичного представления каждого числа
    const aSum = getSumNumber(a);
    const bSum = getSumNumber(b);

     if (aSum === bSum) {
         return a - b             //если суммы равны, то сравниваем сами числа
     } else {
         return aSum - bSum       //если суммы не равны то сравниваем суммы
 }}


  return arr.sort(cmp); //вернет отсортированный массив по количеству единиц в двоичном представлении каждого числа
}

```
