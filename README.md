# コンテンツ管理アプリ用環境構築ファイル群

好きな名前でフォルダ作成する

`cd フォルダ名`

`sudo systemctl restart docker`

- コンテナイメージ作成

`docker-compose build`

- コンテナ起動

`docker-compose up -d`

- コンテナに入る

`docker-compose exec apache-php bash`

- php8.0にパスを通す

`ln -sf /usr/bin/php80 /usr/bin/php`

- composer install 実行

`composer install`

- envファイルの修正（example.envをコピーして作成）

*compose updateは絶対しない（Versionが変わってしまうため）
