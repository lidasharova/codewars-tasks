## Description:
There's no such thing as private properties on a coffeescript object! But, maybe there are?

Implement a function createSecretHolder(secret) which accepts any value as secret and returns an object with ONLY two methods

getSecret() which returns the secret
setSecret() which sets the secret

## Examples
```
obj = createSecretHolder(5)
obj.getSecret() # returns 5
obj.setSecret(2)
obj.getSecret() # returns 2
```

#### Алгоритм выполнения
- Создать функцию createSecretHolder, которая принимает один аргумент secret.
- Внутри функции создать переменную secretValue и присвоить ей значение аргумента secret.
- Создать объект с двумя методами:
     * getSecret(), который возвращает значение переменной secretValue.
     * setSecret(value), который устанавливает значение переменной secretValue в значение аргумента value.
- Вернуть созданный объект.

## Solution:

```javascript
function createSecretHolder(secret) {
  let secretValue = secret;
  const secretHolder = {
    getSecret() {
      return secretValue;
    },
    setSecret(value) {
      secretValue = value;
    }
  };
  return secretHolder;
}

```
