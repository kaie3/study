
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
