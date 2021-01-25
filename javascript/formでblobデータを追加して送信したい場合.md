# formでblobデータを追加して送信したい場合

**ポイント**

+ formにblobデータを追加したい場合はformDataに追加する。
+ formDataに追加するにはformdataイベントを通して行う
+ formdataイベントの発火タイミングはsubmitされる直前

サンプル

```js
const mp4 = new Blob([data.buffer], { type: 'video/mp4' });
const form = document.querySelector('#form');
form.addEventListener('formdata', (e) => {
  e.formData.append('mp4', mp4, 'test.mp4');
});
```
