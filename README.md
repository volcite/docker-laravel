# コンテンツ管理アプリ用環境構築ファイル群

好きな名前でフォルダ作成する

`cd フォルダ名`

```
git clone https://github.com/volcite/system-api.git
git clone https://github.com/volcite/front-manage.git
git clone https://github.com/volcite/front-content.git
git clone -b feature/コンテンツ管理アプリ用 https://github.com/volcite/docker-laravel.git
```

## コンテナイメージ作成＆起動

```
docker-compose build
docker-compose up -d
docker-compose exec apache-php bash
```

### php8.0にパスを通す
```
ln -sf /usr/bin/php80 /usr/bin/php
```

### composer install 実行

```
composer install
```
*compose updateは絶対しない（Versionが変わってしまうため）

### envファイルの作成（example.envをコピーして作成）

### DBにデータ挿入

```
php artisan migrate
php artisan db:seed
```

## hostsファイルに以下を追記

```
127.0.0.1 manage.sample
127.0.0.1 content.sample
```

## フロント側構築（yarnはインストール済みを想定)

```
yarn -v （これでバージョンが表示されて入ればOK）
cd front-manage
yarn install
yarn dev
```

front-contentも同様に

## 初期ログインユーザ（シーダで挿入されるユーザ）
- ユーザ：user@user.com
- パスワード：p@ssw0rd


