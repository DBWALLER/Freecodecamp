---
id: 5a24c314108439a4d4036143
title: استخراج منطق حالة (State Logic) في Redux
challengeType: 6
forumTopicId: 301429
dashedName: extract-state-logic-to-redux
---

# --description--

الآن بعد الانتهاء من مكون React، تحتاج إلى نقل المنطق الذي يُقوم به محليا في `state` إلى Redux. هذه هي الخطوة الأولى لتوصيل تطبيق React البسيط إلى Redux. الوظيفة الوحيدة لتطبيقك هي إضافة رسائل جديدة من المستخدم إلى قائمة غير منظمة (unordered list). المثال بسيط من أجل توضيح كيفية عمل React و Redux معا.

# --instructions--

أولاً، حدد نوع الإجراء `ADD` ثم عيّنه إلى ثابت باسم `ADD`. بعد ذلك، حدد منشئ العمل `addMessage()` الذي ينشئ الإجراء لإضافة رسالة. ستحتاج إلى تمرير `message` إلى منشئ الإجراءات (action creator) وإدراج الرسالة في `action` الذي تم أنشئه.

ثم إنشاء مختصر يسمى `messageReducer()` الذي يتعامل مع الحالة للرسائل. يجب أن تساوي حالة أولى القائمة الفارغة. يجب أن يضيف هذا reducer رسالة إلى قائمة الرسائل المحفوظة في الحالة أو أن يعيد الحالة الحالية. أخيراً، أنشئ متجر Redux ومرر به reducer.

# --hints--

يجب أن يكون ثابت `ADD` موجود وأن تحتفظ بقيمة مساوية string باسم `ADD`

```js
assert(ADD === 'ADD');
```

يجب على منشئ الإجراء `addMessage` أن ينتج كائن مع `type` باسم `ADD` و `message` بقيمة الرسالة التي يتم تمريرها.

```js
assert(
  (function () {
    const addAction = addMessage('__TEST__MESSAGE__');
    return addAction.type === ADD && addAction.message === '__TEST__MESSAGE__';
  })()
);
```

يجب أن تكون `messageReducer` وظيفة function.

```js
assert(typeof messageReducer === 'function');
```

يجب أن يكون المتجر موجوداً وأن تكون لديه حالة أولية إلى قائمة فارغة.

```js
assert(
  (function () {
    const initialState = store.getState();
    return typeof store === 'object' && initialState.length === 0;
  })()
);
```

إرسال `addMessage` إلى المتجر يجب أن يضيف رسالة جديدة بشكل ثابت إلى قائمة من الرسائل المحفوظة في الحالة.

```js
assert(
  (function () {
    const initialState = store.getState();
    const isFrozen = DeepFreeze(initialState);
    store.dispatch(addMessage('__A__TEST__MESSAGE'));
    const addState = store.getState();
    return isFrozen && addState[0] === '__A__TEST__MESSAGE';
  })()
);
```

يجب أن ينتج `messageReducer` الحالة الحالية إذا تم الاتصال بها مع أي إجراءات أخرى.

```js
assert(
  (function () {
    const addState = store.getState();
    store.dispatch({ type: 'FAKE_ACTION' });
    const testState = store.getState();
    return addState === testState;
  })()
);
```

# --seed--

## --seed-contents--

```jsx
// Define ADD, addMessage(), messageReducer(), and store here:
```

# --solutions--

```jsx
const ADD = 'ADD';

const addMessage = (message) => {
  return {
    type: ADD,
    message
  }
};

const messageReducer = (state = [], action) => {
  switch (action.type) {
    case ADD:
      return [
        ...state,
        action.message
      ];
    default:
      return state;
  }
};

const store = Redux.createStore(messageReducer);
```
