# JavaScript の全般メモ(あとで整理する)

- [JavaScript Primer](https://jsprimer.net/)
- [TypeScript Deep Dive](https://typescript-jp.gitbook.io/deep-dive/)
- ES6 の仕様は import 文.require の仕様は CommonJS
- import 文は,Chrome などでは動くが IE など ES6 に対応していないブラウザでは動かない
- require 文は,Nodejs（サーバサイド）では動くがブラウザ側実行の js では動かない
- [拡張子が.cjs のファイルは CJS(CommonJS)、.mjs(ECMAScript)のファイルは ESM として扱われる](https://numb86-tech.hatenablog.com/entry/2020/08/07/091142)
- 混在させたいならバンドルツールを使う
  - [調査]バックエンドでは必ずしもひとまとめにする必要はないから混在する場合はどうしているのか?
- node.js は CommonJS 構文でモジュールをロードしようとします.ES モジュールを使うときは以下を追加する
  - [npm v8.0.0](https://github.com/npm/cli/releases/tag/v8.0.0)以降ではrequire('npm')のサポートを終了しました。
- [node-fetch は ESM のみのモジュールで、require ではインポートできません](https://github.com/node-fetch/node-fetch#installation)

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

## eslint&prettier

[完全版 eslint&prettier&vscode](https://zenn.dev/sawao/articles/6ad32596a82174)

- Prettier.コードフォーマッター(ソースコードを整形してくれるツール)のこと
- eslint.リンター.問題点を指摘してくれる静的解析ツール
- prettier でフォーマット後 eslint で解析する.eslint のフォーマットは無効にする
- eslint-config-prettier.Prettier と競合する ESLint ルールを無効化するためのプラグイン

1. vscode のプラグインである eslint,prettier インストール

```shell
yarn add eslint prettier eslint-config-prettier
```

1. eslint の設定

```cmd
touch .eslintrc.json
```

```json:.eslintrc.json
{
    "env": {
        "browser": true,
        "es2021": true
    },
    "extends": ["eslint:recommended", "prettier"],
    "parserOptions": {
        "ecmaVersion": 12,
        "sourceType": "module"
    },
    "rules": {}
}
```

1. prettier の設置

```cmd
touch .prettierrc
```

```json:.prettierrc
{
    "doubleQuote": true,
    "trailingComma": "all",
    "tabWidth": 4
}
```

1. vscode の設定

- ユーザワークスペースの settings.json に記入

```json:settings.josn
{
    // このファイルは/.vscode/settings.jsonです
    "editor.codeActionsOnSave": {
        "source.fixAll.eslint": true
    },
    "eslint.format.enable": false,
    "editor.formatOnSave": true,
    "[javascript]": {
        "editor.defaultFormatter": "esbenp.prettier-vscode"
    },
    "[json]": {
        "editor.defaultFormatter": "esbenp.prettier-vscode"
    },
    "editor.lineNumbers": "on",
    "editor.rulers": [80],
    "editor.wordWrap": "on",
    "eslint.packageManager": "yarn",
    "files.insertFinalNewline": true,
    "files.trimTrailingWhitespace": true,
    "npm.packageManager": "yarn",
    "typescript.enablePromptUseWorkspaceTsdk": true
}
```

## yarn

[yarn の使い方,ゼロから始める JavaScript 生活](https://qiita.com/takahashim/items/7838334d1451fb0a9811)

- パッケージは yarn で管理する。以下初期設定。すでに古い yarn が入っている前提。

```shell script
cd ~/path/to/project # プロジェクトフォルダに移動します。
yarn set version berry #「Berry」は、2以降のすべてのバージョンのYarn（2.x、3.xなど）のコードネームです。これは、リポジトリの名前でもあります。
yarn set version latest # Yarnを最新バージョンに更新する
# .yarnrc.ymlに追記する
yarn init #初期設定
```

- バージョン 3 にするとデフォルトで Zero-Installs が有効なことに注意。賛否がある模様。以下の設定を追加で node_modules ディレクトリ管理になる

```yml:.yarnrc.yml
# .yarnrc.yml
nodeLinker: node-modules
```

```:.gitignore
# .gitignore
node_modules
```
