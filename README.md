# Laravel8-place

---

## PHP から PostgreSQL に接続するための設定

### Win

読み込まれる php.ini の場所を確認

```bat
$ php -r 'phpinfo();' | grep php.ini
```

php.ini のコメント解除

```ini
- ;extension=php_pgsql.dll
+ extension=php_pgsql.dll
```

## Composer のインストール

### Win

[Composer-Setup.exe](https://getcomposer.org/Composer-Setup.exe)

### Mac

```
$ brew install composer
```

### Linux

```sh
php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');"
php composer-setup.php
php -r "unlink('composer-setup.php');"
```

## Laravel のインストール

```sh
$ composer create-project --prefer-dist laravel/laravel . '8.5.9'
```

## PostgreSQL の設定

[ユーザー名とデータベース名を指定して Docker コンテナを起動する](https://github.com/YA-androidapp/Docker-Compose-PostgreSQL/blob/main/docker-compose.yml) か、
ローカルに PostgreSQL をインストールしてからユーザーとデータベースを以下のコマンドで用意する

```sh
$ createuser -U postgres -P YOUR_USERNAME
新しいロールのためのパスワード: <YOUR_PASSWORD>
もう一度入力してください: <YOUR_PASSWORD>
パスワード: <PASSWORD_OF_postgres>
$ createdb -U postgres -O YOUR_USERNAME YOUR_DATABASE
パスワード: <PASSWORD_OF_postgres>
```

## Laravel の初期設定

-   `config/app.php`

```php
-     'timezone' => 'UTC',
+     'timezone' => 'Asia/Tokyo',

-     'locale' => 'en',
+     'locale' => 'ja',
```

-   `.env`

```ini
- DB_CONNECTION=mysql
- DB_HOST=127.0.0.1
- DB_PORT=3306
- DB_DATABASE=laravel
- DB_USERNAME=root
- DB_PASSWORD=

+ DB_CONNECTION=pgsql
+ DB_HOST=127.0.0.1
+ DB_PORT=5432
+ DB_DATABASE=YOUR_DATABASE
+ DB_USERNAME=YOUR_USERNAME
+ DB_PASSWORD=YOUR_PASSWORD
```

## マイグレーション

```sh
$ php artisan migrate
```

## 動作確認（Welcome ページ）

```sh
$ php artisan serve

# Ctrl + C で停止
```

## ユーザー認証の追加

```sh
$ composer require laravel/jetstream:2.1.2

# memory_limit に引っかかった場合
# $ php -d memory_limit=-1 composer require laravel/jetstream laravel/jetstream:2.1.2

$ php artisan jetstream:install livewire

# チーム管理を追加する場合
# $ php artisan jetstream:install livewire --teams

$ npm install && npm run dev
$ php artisan migrate

$ php artisan vendor:publish --tag=jetstream-views
```

## 動作確認（ユーザー登録）

```sh
$ php artisan serve

# Ctrl + C で停止
```
