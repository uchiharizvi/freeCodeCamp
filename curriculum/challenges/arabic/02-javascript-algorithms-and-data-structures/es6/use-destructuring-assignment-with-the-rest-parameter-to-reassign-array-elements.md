---
id: 587d7b8a367417b2b2512b4c
title: >-
  Use Destructuring Assignment with the Rest Parameter to Reassign Array Elements
challengeType: 1
forumTopicId: 301218
dashedName: >-
  use-destructuring-assignment-with-the-rest-parameter-to-reassign-array-elements
---

# --description--

في بعض المواقف التي تتضمن array destructuring، قد نرغب في تجميع باقي العناصر في array منفصلة.

النتيجة مشابهة لـ `Array.prototype.slice()`، كما هو موضح أدناه:

```js
const [a, b, ...arr] = [1, 2, 3, 4, 5, 7];
console.log(a, b);
console.log(arr);
```

ستعرض وحدة التحكم القيم `1, 2` و `[3, 4, 5, 7]`.

المتغيرات `a` و `b` تأخذ القيم الأولى والثانية من الـ array. بعد ذلك، بسبب وجود rest parameter، الـ `arr` يحصل على بقية القيم في شكل array. يعمل العنصر rest بشكل صحيح فقط كآخر متغير في القائمة. بمعني انه لا يمكنك استخدام rest parameter لالتقاط subarray (اي array فرعية) تترك العنصر الأخير من الـ array الأصلية.

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

`Array.slice()` لا ينبغي استخدامه.

```js
(getUserInput) => assert(!getUserInput('index').match(/slice/g));
```

يجب استخدام Destructuring علي `list`.

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
