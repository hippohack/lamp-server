## 環境構築手順

/docker/web/base.sample.conf を base.conf にリネームする。

docker-compose.yml があるフォルダに移動して、

```
docker-compose up -d
```

```
docker-compose ps
```

Status が 4 つ RUNNING になってれば OK

ホスト設定

```
echo "127.0.0.1 www.hoge.test" | sudo tee -a /etc/hosts
echo "127.0.0.1 www.fuga.test" | sudo tee -a /etc/hosts
```

パスワードを聞かれるので、端末のログインパスワードを入力。

その後、ブラウザで http://www.hoge.test にアクセスすると index.html が表示される

## WordPressを設置する場合

/html/www.hoge.test/html/public が公開ディレクトリとなるので、ここに WP を設置します。

/html/www.fuga.test/html/public も同様です。

設置後、ブラウザで http://www.hoge.test にアクセスすると WP が開く

## 開発用ツール

- phpmyadmin / http://localhost:8080/
- mailCather / http://localhost:1080/
- XDebug

