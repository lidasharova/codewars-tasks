## Description:

The goal of this exercise is to convert a string to a new string where each character in the new string is "(" if that character appears only once in the original string, or ")" if that character appears more than once in the original string. Ignore capitalization when determining if a character is a duplicate.

### Examples (input --> output):

```
"din"      =>  "((("
"recede"   =>  "()()()"
"Success"  =>  ")())())"
"(( @"     =>  "))(("
```


## Solution:
#### Алгоритм выполнения

- переведем входную строку в один регистр;
- проверим по итерации строки циклом - вхождения каждого символа,
  с помощью методов indexOf и lastIndexOf,которые проверят вхождение текущего символа(lowerWord[i]) с начала строки и с конца строки.
- если результаты вызова методов indexOf() и lastIndexOf() равны, то это означает, что в строке или массиве искомый элемент существует в одном месте(не повторяется)
- исходя их этого условия, мы будем добавлять в пустую строку соответствующее значение ')' или '('

```javascript
function duplicateEncode(word) {
  let str = '';
  let lowerWord = word.toLowerCase();
  console.log(lowerWord);

  for (let i = 0; i < lowerWord.length; i++) {
    console.log(lowerWord[i]);

    lowerWord.indexOf(lowerWord[i]) === lowerWord.lastIndexOf(lowerWord[i])
      ? (str += '(')
      : (str += ')');
  }
  return str;
}
```
