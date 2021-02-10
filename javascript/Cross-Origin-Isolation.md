# Cross-Origin Isolation

Spectreのようなサイドチャネル攻撃対策

正しく設定されている場合は`globalThis.crossOriginIsolated`の値が`true`になる  
Firefoxでは正しく設定していないと`SharedArrayBuffer`を使うことができない。

## Headers

### [Cross-Origin-Opener-Policy](https://developer.mozilla.org/ja/docs/Web/HTTP/Headers/Cross-Origin-Resource-Policy)

`window.opener`で開けるオリジンの定義

### [Cross-Origin-Embedder-Policy](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Cross-Origin-Embedder-Policy)

`require-corp`を設定している場合はCORSが設定されているかcrossorigin属性を付与しないといけない。

### [Cross-Origin-Resource-Policy](https://developer.mozilla.org/ja/docs/Web/HTTP/CORS)

CORSを利用する範囲の限定
