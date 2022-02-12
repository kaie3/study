# メモ

- ADDよりCOPYを優先優先して使う
- [EXPOSE](https://docs.docker.jp/engine/reference/builder.html#expose)コマンド、だいたい-p使えばいい
- Dockerのキャッシュ削除

```script
docker builder prune
#またはビルド時に
docker-compose build --no-cache
```

- ttyコマンド:ネットワーク越しのシェルにリモートでログインしたときにローカルのクライアントにつけられる一時的な名前。例,/dev/pts/0,/dev/pts/1など
