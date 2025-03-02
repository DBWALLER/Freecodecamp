---
id: 56533eb9ac21ba0edf2244ca
title: Використання об'єктів для пошуків
challengeType: 1
videoUrl: 'https://scrimba.com/c/cdBk8sM'
forumTopicId: 18373
dashedName: using-objects-for-lookups
---

# --description--

Об'єкти можна вважати сховищем ключів та значень, як словники. Якщо ви маєте табличні дані, ви краще можете використати об'єкт для пошуку значень, ніж `switch` твердження або `if/else` ланцюжок. Це найбільш корисно, коли ви знаєте, що ваші вхідні дані обмежені до певного діапазону.

Here is an example of an article object:

```js
const article = {
  "title": "How to create objects in JavaScript",
  "link": "https://www.freecodecamp.org/news/a-complete-guide-to-creating-objects-in-javascript-b0e2450655e8/",
  "author": "Kaashan Hussain",
  "language": "JavaScript",
  "tags": "TECHNOLOGY",
  "createdAt": "NOVEMBER 28, 2018"
};

const articleAuthor = article[author];
const articleLink = article[link];

const value = "title";
const valueLookup = article[value];
```

`articleAuthor` is the string `Kaashan Hussain`, `articleLink` is the string `https://www.freecodecamp.org/news/a-complete-guide-to-creating-objects-in-javascript-b0e2450655e8/`, and `valueLookup` is the string `How to create objects in JavaScript`.

# --instructions--

Переробіть ключове твердження на об'єкт, що називається `lookup`. Використовуйте його, щоб шукати `val` і призначати пов'язаний рядок до `result` змінної.

# --hints--

`phoneticLookup("alpha")` має дорівнювати рядку `Adams`

```js
assert(phoneticLookup('alpha') === 'Adams');
```

`phoneticLookup("bravo")` має дорівнювати рядку `Boston`

```js
assert(phoneticLookup('bravo') === 'Boston');
```

`phoneticLookup("charlie")` має дорівнювати рядку `Chicago`

```js
assert(phoneticLookup('charlie') === 'Chicago');
```

`phoneticLookup("delta")` має дорівнювати рядку `Denver`

```js
assert(phoneticLookup('delta') === 'Denver');
```

`phoneticLookup("echo")` має дорівнювати рядку `Easy`

```js
assert(phoneticLookup('echo') === 'Easy');
```

`phoneticLookup("foxtrot")` має дорівнювати рядку `Frank`

```js
assert(phoneticLookup('foxtrot') === 'Frank');
```

`phoneticLookup("")` має дорівнювати `undefined`

```js
assert(typeof phoneticLookup('') === 'undefined');
```

Вам не слід змінювати `return` твердження

```js
assert(code.match(/return\sresult;/));
```

Вам не слід використовувати `case`, `switch` або `if` твердження

```js
assert(
  !/case|switch|if/g.test(code.replace(/([/]{2}.*)|([/][*][^/*]*[*][/])/g, ''))
);
```

# --seed--

## --seed-contents--

```js
// Setup
function phoneticLookup(val) {
  let result = "";

  // Only change code below this line
  switch(val) {
    case "alpha":
      result = "Adams";
      break;
    case "bravo":
      result = "Boston";
      break;
    case "charlie":
      result = "Chicago";
      break;
    case "delta":
      result = "Denver";
      break;
    case "echo":
      result = "Easy";
      break;
    case "foxtrot":
      result = "Frank";
  }

  // Only change code above this line
  return result;
}

phoneticLookup("charlie");
```

# --solutions--

```js
function phoneticLookup(val) {
  let result = "";

  const lookup = {
    alpha: "Adams",
    bravo: "Boston",
    charlie: "Chicago",
    delta: "Denver",
    echo: "Easy",
    foxtrot: "Frank"
  };

  result = lookup[val];

  return result;
}
```
