# Promise generator

简单可依赖的Promise 顺序执行（串行执行）器。

[![Build Status](https://travis-ci.org/xiongwilee/promise-generator.svg?branch=master)](https://travis-ci.org/xiongwilee/promise-generator)  [![npm version](https://img.shields.io/npm/v/promise-generator.svg?style=flat)](https://npmjs.org/package/promise-generator) [![download](https://img.shields.io/npm/dm/promise-generator.svg?style=flat)](https://npmjs.org/package/promise-generator)

## 安装

```shell
$ npm install promise-generator
```

## 使用

```javascript
const pg = require('promise-generator')

const promises = [() => {
  return Promise.resolve(0)
}, () => {
  return new Promise((resolve) => {
    resolve(1)
  })
}, () => {
  return new Promise((resolve) => {
    setTimeout(() => {
      resolve(2)
    }, 100)
  })
}, () => {
  return new Promise((resolve) => {
    setTimeout(() => {
      resolve(3)
    }, 100)
  })
}, () => {
  return new Promise((resolve) => {
    setTimeout(() => {
      resolve(4)
    }, 100)
  })
}]

pg(promises).then((data) => {
  console.log(data); // 300ms+之后输出：[0,1,2,3,4] 
})
```

## 贡献

欢迎大家提issue、fork；有任何疑问也可以邮件联系：xiongwilee[at]foxmail.com。
