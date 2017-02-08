# Map

ES2015で追加された[Map](https://developer.mozilla.org/ja/docs/Web/JavaScript/Reference/Global_Objects/Map)はkey,value構成のハッシュです。  
注意が必要なのはObjectとは等価ではないということです。  
ArrayとSetは相互変換が簡単にできますが、現在のObjectとMapの場合は一手間加える必要があります。  
配列と相性のいいハッシュとして使うと便利になります。

```js

// 初期化
const map = new Map([
    [`key1`, `value1`],
    [`key2`, `value2`]
]);

// 追加・上書き
map.set(`key3`, `value3`);

// 配列に戻す
const arr = [...map]; // [ [`key1`, 'value1'], [`key2`, `value2`] ]

// Object に変換
const obj = {};
for (let [key, value] of map)
    obj[key] = value;
```
