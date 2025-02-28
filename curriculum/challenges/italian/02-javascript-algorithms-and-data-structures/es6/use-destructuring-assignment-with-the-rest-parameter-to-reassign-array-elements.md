---
id: 587d7b8a367417b2b2512b4c
title: >-
  Usare l'assegnazione destrutturante con il parametro di resto per riassegnare gli elementi dell'array
challengeType: 1
forumTopicId: 301218
dashedName: >-
  use-destructuring-assignment-with-the-rest-parameter-to-reassign-array-elements
---

# --description--

In alcune situazioni che comportano la destrutturazione di array, potremmo voler raccogliere il resto degli elementi in un array separato.

Il risultato è simile a `Array.prototype.slice()`, come mostrato sotto:

```js
const [a, b, ...arr] = [1, 2, 3, 4, 5, 7];
console.log(a, b);
console.log(arr);
```

La console mostrerà i valori `1, 2` e `[3, 4, 5, 7]`.

Le variabili `a` e `b` prendono il primo e il secondo valore dall'array. Dopodiché, a causa della presenza del parametro di resto, `arr` ottiene il resto dei valori sotto forma di un array. L'elemento di resto funziona correttamente solo come ultima variabile dell'elenco. Non è quindi possibile utilizzare il parametro di resto per catturare un sottoarray che lascia fuori l'ultimo elemento dell'array originale.

# --instructions--

Use a destructuring assignment with the rest parameter to emulate the behavior of `Array.prototype.slice()`. `removeFirstTwo()` should return a sub-array of the original array `list` with the first two elements omitted.

# --hints--

`removeFirstTwo([1, 2, 3, 4, 5])` should be `[3, 4, 5]`

```js
const testArr_ = [1, 2, 3, 4, 5];
const testArrWORemoved_ = removeFirstTwo(testArr_);
assert(testArrWORemoved_.every((e, i) => e === i + 3) && testArrWORemoved_.length === 3);
```

`removeFirstTwo()` should not modify `list`

```js
const testArr_ = [1, 2, 3, 4, 5];
const testArrWORemoved_ = removeFirstTwo(testArr_);
assert(testArr_.every((e, i) => e === i + 1) && testArr_.length === 5);
```

`Array.slice()` non dovrebbe essere utilizzato.

```js
(getUserInput) => assert(!getUserInput('index').match(/slice/g));
```

Si dovrebbe utilizzare la destrutturazione su `list`.

```js
assert(
  __helpers
    .removeWhiteSpace(code)
    .match(/\[(([_$a-z]\w*)?,){1,}\.\.\.shorterList\]=list/i)
);
```

# --seed--

## --seed-contents--

```js
function removeFirstTwo(list) {
  // Only change code below this line
  const shorterList = list; // Change this line
  // Only change code above this line
  return shorterList;
}

const source = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10];
const sourceWithoutFirstTwo = removeFirstTwo(source);
```

# --solutions--

```js
function removeFirstTwo(list) {
  const [, , ...shorterList] = list;
  return shorterList;
}

const source = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10];
const sourceWithoutFirstTwo = removeFirstTwo(source);
```
