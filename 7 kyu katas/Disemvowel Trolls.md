## Description:
Trolls are attacking your comment section!

A common way to deal with this situation is to remove all of the vowels from the trolls' comments, neutralizing the threat.

Your task is to write a function that takes a string and return a new string with all vowels removed.


Note: for this kata y isn't considered a vowel.


### Examples (input --> output):

For example, the string "This website is for losers LOL!" would become "Ths wbst s fr lsrs LL!".

## Solution:


##### Алгоритм
 Используем регулярное выражение и два флага для него:

g - глобальный поиск. Этот флаг указывает на необходимость поиска всех совпадений в строке, а не только первого. В нашем случае это позволяет удалить все гласные буквы в строке, а не только первую найденную.

i - игнорировать регистр.
Этот флаг указывает на то, что поиск должен осуществляться без учета регистра символов. Таким образом, мы можем удалить все гласные, независимо от их регистра в исходной строке.

```javascript

function disemvowel(str) {
 return str.replace(/[aeiou]/gi, '');
}

```