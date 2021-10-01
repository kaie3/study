# gitのメモ

## gitの初期設定

- githubのサイトに行き新規リポジトリを作成してURLをgetしてくる

```cmd
echo "# xxx" >> README.md
git init
git add README.md
git commit -m "first commit"
git branch -M main
git remote add origin https://github.com/kaie3/xxx.git
git push -u origin main
```

## コミットの仕方

```cmd
git status #変更のあったファイルを確認
git diff #変更した箇所を確認
git add . #変更されているファイルを全て追加
git reset #追加したファイルをキャンセル
git commit -m "bug fixed" #コメント付きコミット
git push origin main #プッシュ
```
