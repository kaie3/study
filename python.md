
# モジュール

- [note.nkmk.me](https://note.nkmk.me/)
- [正規表現チェッカー](https://weblabo.oscasierra.net/tools/regex/)
- jsonモジュールはload , dump とloads, dumps に分けられます。
sがついてない方は、引数にファイルストリームを指定します。(dumpはdictも)
sがついている方は、loadsなら文字列を指定しますし、dumps なら戻り値が文字列になります。
つまりファイルから直接読み込んだり、直接書き込んだりするときにはsのついていない方を、文字列のJSONを扱いたいときにはsがついている方を使うということです。

Pythonで長い文字列を複数行に分けて書く

```python
s = 'https://ja.wikipedia.org/wiki/'\
    '%E3%83%97%E3%83%AD%E3%82%B0%E3%83'\
    '%A9%E3%83%9F%E3%83%B3%E3%82%B0%E8%A8%80%E8%AA%9E'

print(s)
# https://ja.wikipedia.org/wiki/%E3%83%97%E3%83%AD%E3%82%B0%E3%83%A9%E3%83%9F%E3%83%B3%E3%82%B0%E8%A8%80%E8%AA%9E
```

- python自体は0始まり,numpyは1始まり
- [NumPyの主要なデータ型dtype一覧](https://note.nkmk.me/python-numpy-dtype-astype/)

# Python命名規則一覧

|対象|ルール|例|
| --- | --- | --- |
|パッケージ|全小文字,なるべく短くアンダースコア非推奨|tqdm, requests ...|
|モジュール|全小文字 なるべく短くアンダースコア可|sys, os,...|
|クラス|最初大文字 + 大文字区切り|MyFavoriteClass|
|例外|最初大文字 + 大文字区切り|MyFuckingError|
|型変数|最初大文字 + 大文字区切り|MyFavoriteType|
|メソッド|全小文字 + アンダースコア区切り|my_favorite_method|
|関数|全小文字 + アンダースコア区切り|my_favorite_funcion|
|変数|全小文字 + アンダースコア区切り|my_favorite_instance|
|定数|全大文字 + アンダースコア区切り|MY_FAVORITE_CONST|

# 演算子の優先順位

| 演算子 | 説明 |
|--------|------|
| `(expressions...)`, `[expressions...]`, `{key: value...}`, `{expressions...}` | 結合式または括弧式、リスト表示、辞書表示、集合表示 |
| `x[index]`, `x[index:index]`, `x(arguments...)`, `x.attribute` | 添字指定、スライス操作、呼び出し、属性参照 |
| `await x` | Await 式 |
| `**` | べき乗 |
| `+x`, `-x`, `~x` | 正数、負数、ビット単位 NOT |
| `*`, `@`, `/`, `//`, `%` | 乗算、行列乗算、除算、切り捨て除算、剰余 |
| `+`, `-` | 加算および減算 |
| `<<`, `>>` | シフト演算 |
| `&` | ビット単位 AND |
| `^` | ビット単位 XOR |
| `\|` | ビット単位 OR |
| `in`, `not in`, `is`, `is not`, `<`, `<=`, `>`, `>=`, `!=`, `==` | 所属や同一性のテストを含む比較 |
| `not x` | ブール演算 NOT |
| `and` | ブール演算 AND |
| `or` | ブール演算 OR |
| `if -- else` | 条件式 |
| `lambda` | ラムダ式 |
| `:=` | 代入式 |

べき乗演算子 \*\*は、右側にある単項算術演算子あるいは単項ビット演算子より弱い結合優先順位となります。\
つまり 2**-1 は 0.5 になります。
% 演算子は文字列フォーマットにも使われ、同じ優先順位が当てはまります。

## memo

座標系
th-table header
tr-table row
td-table data
![座標系](img\座標系.png)
