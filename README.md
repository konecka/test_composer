# Набор зависимостей для проекта, в котором:

### 1. Используется БД для хранения данных
[illuminate/database](https://packagist.org/packages/illuminate/database)

Пакет для работы с БД. В настоящее время поддерживаются MySQL, Postgres, SQL Server, SQLite.


Создание объекта класса Capsule и инициализация этого объекта констанстами:
```php
use Illuminate\Database\Capsule\Manager as Capsule;

$dotenv = new Dotenv\Dotenv('/.env');
$dotenv->load();

$capsule = new Capsule;

$capsule->addConnection([
  'driver' => getenv(DB_CONNECTION),
  'host' => getenv(DB_HOST),
  'database' => getenv(DB_DATABASE),
  'username' => getenv(DB_USERNAME),
  'password' => getenv(DB_PASSWORD),
  'charset' => 'utf8',
  'collation' => 'utf8_unicode_ci',
  'prefix' => '',
]);
  // Установка ORM Eloquent
  $capsule->bootEloquent();
}
```



### 2. Используется кеш в памяти для временного хранения сложных запросов к БД

```php

```

### 3. Формируются XLS-отчеты на основе данных

```php

```


### 4. Формируются PDF-документы на основе данных


### 5. Отправляются SMS-сообщения для верификации пользователей


### 6. Отправляются E-mail-уведомления и рассылки для пользователей


### 7. Используется облачное хранилище AWS S3 или Windows Azure Blob для статичных файлов


### 8. Используется интеграция со службой доставки для расчета стоимости (например, PickPoint или Почта России)


### 9. Используется интеграция с социальными сетями для авторизации пользователей


### 10. Данные о товарах регулярно отправляются в Яндекс.Маркет


### 11. Принимается онлайн-оплата от покупателей


### 12. Применяются средства тестирования (например, PHPUnit)
