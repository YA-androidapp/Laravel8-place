# Laravel8-place

---

## Laravel のインストール

```sh
$ composer create-project --prefer-dist laravel/laravel . '8.5.9'
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

```php
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
