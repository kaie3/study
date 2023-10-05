# JavaScript の全般メモ(あとで整理する)

- [JavaScript Primer](https://jsprimer.net/)
- [TypeScript Deep Dive](https://typescript-jp.gitbook.io/deep-dive/)
- [Native ESM + TypeScript 拡張子問題: 歯にものが挟まったようなスッキリしない書き流し](https://zenn.dev/qnighy/articles/19603f11d5f264),これが詳しい
- ES6 の仕様は import 文.require の仕様は CommonJS
  - import 文はクライアント(Chrome) などでは動くが IE など ES6 に対応していないブラウザでは動かない
  - require 文はNodejs（サーバサイド）では動くがブラウザ側実行の js では動かない
- [拡張子が.cjs のファイルは CJS(CommonJS)、.mjs(ECMAScript)のファイルは ESM として扱われる](https://numb86-tech.hatenablog.com/entry/2020/08/07/091142)
- 混在させたいならバンドルツールを使う
  - *調査* バックエンドでは必ずしもひとまとめにする必要はないから混在する場合はどうしているのか?
    - *解* 対象のファイルを.mjsにリネームする。export defaultに書き直してimportする
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

```node.js
yarn add eslint prettier eslint-config-prettier
```

1. eslint の設定

```script
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

```script
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

Client Side Rendering(CSR)
Server Side Rendering(SSR)
Static Site Generation(SSG)
Incremental Static Regeneration(ISR)
Server Side Component(SSC)
