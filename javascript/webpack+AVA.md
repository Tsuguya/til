# webpack + AVA

webpackとAVAを合わせて使うとハマった箇所があったのでメモします。

## Tree Shakingを使用しているとAVAでimport, exportが使えない

webpackでTree Shakingを有効化していますとAVAでimport, exportしている箇所でエラーが発生します。  
原因は`.babelrc`で`module: false`を有効化しているため、それに引きずられてエラーがおきている模様です。  
調べた限りだとオプション等での回避方法は見つかりませんでした。  
とりあえずは以下の方法で対応しました。

`webpack.config.js`で`modules: false`に書き換えてbabel-loaderのoptionsに入れています。

`.babelrc`

```json
{
  "presets": [
    ["env", {
      "targets": {
        "browsers": ["last 2 versions", "safari >= 7"]

      },
      "modules": "commonjs"
    }]
  ]
}
```

`webpack.config.js`

```js
const fs = require(`fs`);
const babelrc = JSON.parse(fs.readFileSync(path.join(`./`, `package.json`))).babel;

babelrc.presets[0][1].modules = false;

// ...

module.export = {
  // ...
  module: {
    // ...
    {
        test: /(\.webpack)?\.jsx?$/,
        exclude: /node_modules/,
        use: {
          loader: `babel-loader`,
          options: babelrc,
        },
      },
  }
};

```
