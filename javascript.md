# JavaScriptのメモ

- ES6の仕様はimport文.requireの仕様はCommonJS
- import文は,Chromeなどでは動くがIEなどES6に対応していないブラウザでは動かない
- require文は,Nodejs（サーバサイド）では動くがブラウザ側実行のjsでは動かない
- 拡張子が.cjsのファイルはCJS(CommonJS)、.mjs()のファイルはESMとして扱われる
- 混在させたいならバンドルツールを使う
- node.jsはCommonJS構文でモジュールをロードしようとします.ESモジュールを使うときは以下を追加する

```json:package.json
// package.json
"type": "module"
```

```JavaScript
// ES6のモジュール側
export const helloWorld = function() {
    console.log('Hello World!!');
}

// ES6の読み込み側
import { helloWorld } from './module'
helloWorld();
// ==========================================================================
//CommonJSのモジュール側
module.exports = function() {
    console.log('Hello World!!');
}

//CommonJSの読み込み側
const helloWorldModule = require('./module.js');
helloWorldModule();
// 出力：Hello World!!
```

## yarn

- パッケージはyarnで管理する。以下初期設定。すでに古いyarnが入っている前提。

```cmd
cd ~/path/to/project # プロジェクトフォルダに移動します。
yarn set version berry #「Berry」は、2以降のすべてのバージョンのYarn（2.x、3.xなど）のコードネームです。これは、リポジトリの名前でもあります。
yarn set version latest # Yarnを最新バージョンに更新する
# .yarnrc.ymlに追記する
yarn init #初期設定
```

- バージョン3にするとデフォルトでZero-Installsが有効なことに注意。賛否がある模様。以下の設定を追加でnode_modulesディレクトリ管理になる

```yml:.yarnrc.yml
# .yarnrc.yml
nodeLinker: node-modules
```

```.gitignore
# .gitignore
node_modules
```

yarnの使い方,ゼロから始めるJavaScript生活<https://qiita.com/takahashim/items/7838334d1451fb0a9811>
