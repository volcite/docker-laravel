# dockerで Apache, Laravel6, MySQL8.0, Redis, phpMyAdmin の環境を構築するファイル群です

- ます、以下の環境構築が終わらせる

https://github.com/volcite/docker-on-vagrant

- Docksフォルダの中で環境構築のファイル群をcloneする

`git clone https://github.com/volcite/docker-laravel.git プロジェクト名`

- 仮想マシンに接続する

`cd ..`

`vagrant ssh`

- dockerを起動させる

`cd docks`

`cd プロジェクト名`

`sudo systemctl restart docker`

- コンテナイメージ作成

`docker-compose build`

- コンテナ起動

`docker-compose up -d`

- コンテナに入る

`docker-compose exec apache-php bash`

- Laravelインストール

`composer global require laravel/installer`

`composer create-project --prefer-dist laravel/laravel lara-d "6.*"`

- php8.0にパスを通す

`ln -sf /usr/bin/php80 /usr/bin/php`

`exit`

- コンテナ停止

`docker-compose down`

- apatch.conf修正

`docker/apache-php/apache.conf`のファイルを開く

119行目、131行目を変更

修正前 `var/www/html/` →　修正後 `var/www/html/public`

- docker-compose.yml修正

docker-compose.ymlのファイルを開く

 13行目を変更

修正前 `"./src:/var/www/html"` → 修正後 `./src/lara-d:/var/www/html`

- コンテナ起動

`docker-compose up -d`

http://192.168.33.11 で表示確認

envファイルの修正（example.envをコピーして作成）

環境構築終了
