---
title: JavaScript 异步编程指南
date: 2026-03-12 14:30:00
tags:
  - JavaScript
  - 异步编程
  - 前端
categories:
  - 技术
cover: https://picsum.photos/800/400?random=21
description: 深入理解 JavaScript 中的 Promise、async/await 和事件循环。
---

## 回调地狱

在 ES6 之前，异步操作主要依靠回调函数：

```javascript
getData(function(a) {
  getMoreData(a, function(b) {
    getEvenMoreData(b, function(c) {
      console.log(c);
    });
  });
});
```

这就是著名的"回调地狱"。

## Promise

Promise 提供了更优雅的解决方案：

```javascript
getData()
  .then(a => getMoreData(a))
  .then(b => getEvenMoreData(b))
  .then(c => console.log(c))
  .catch(err => console.error(err));
```

## Async/Await

ES2017 引入的 async/await 让异步代码看起来像同步代码：

```javascript
async function fetchData() {
  try {
    const a = await getData();
    const b = await getMoreData(a);
    const c = await getEvenMoreData(b);
    console.log(c);
  } catch (err) {
    console.error(err);
  }
}
```

## 并行执行

当多个异步操作互不依赖时，使用 `Promise.all` 并行执行：

```javascript
const [users, posts, comments] = await Promise.all([
  fetchUsers(),
  fetchPosts(),
  fetchComments()
]);
```

> 异步编程是前端开发的核心技能之一。
