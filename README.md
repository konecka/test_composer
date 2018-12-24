# Набор зависимостей для проекта, в котором:

### 1. Используется БД для хранения данных
[illuminate/database](https://packagist.org/packages/illuminate/database)

Пакет для работы с БД. В настоящее время поддерживаются MySQL, Postgres, SQL Server, SQLite.


Создание объекта класса Capsule и инициализация этого объекта констанстами:

```php
//php code 

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

Использование ORM Eloquent:

```php
  //php code

  class User extends Illuminate\Database\Eloquent\Model {}
  $users = User::where('verified', '=', TRUE)->get();
```


### 2. Используется кеш в памяти для временного хранения сложных запросов к БД
[watson/rememberable](https://packagist.org/packages/watson/rememberable)

Кэширование запросов для Laravel. Результаты запросов кэшируются в течение заданного промежутка времени.

Получить статьи первого пользователя и запомнить их на 6 часов :

```php

//php code 
User::first()->remember(360)->posts()->get();
```

### 3. Формируются XLS-отчеты на основе данных
[phpoffice/phpspreadsheet](https://packagist.org/packages/phpoffice/phpspreadsheet)

### 4. Формируются PDF-документы на основе данных
[phpoffice/phpspreadsheet](https://packagist.org/packages/phpoffice/phpspreadsheet)


### 5. Отправляются SMS-сообщения для верификации пользователей
[twilio/sdk](https://packagist.org/packages/twilio/sdk)

PHP обетка для API Twilio.

Отправка sms:

```php
// php code

public function sendSms(Request $request)
{
  $accountSid = getenv(TWILIO_ACCOUNT_SID); // присваивается при регистрации на twilio
  $authToken = getenv(TWILIO_AUTH_TOKEN); // присваивается при регистрации на twilio

  $code = rand(1000, 9999); // генерация 4-х значного кода
  $request['code'] = $code; 

  $client = new Twilio\Rest\Client($sid, $token);
  $message = $client->messages->create(
  $request->phone_number, // номер, на который высылаем

  array(
    'from' => '17637106051', // номер, арендованный на twilio
    'body' => 'CODE: '. $request->code
  )
  );
}
```

### 6. Отправляются E-mail-уведомления и рассылки для пользователей


### 7. Используется облачное хранилище AWS S3 или Windows Azure Blob для статичных файлов
[aws/aws-sdk-php](https://packagist.org/packages/aws/aws-sdk-php)

Пакет для создание php-приложений с использованием сервисов Amazon (Amazon S3, Amazon DynamoDB, Amazon Glacier)

```php
// php code

require 'vendor/autoload.php';

use Aws\S3\S3Client;

// Настройка клиента для S3, указание региона и последней версии
$s3 = new Aws\S3\S3Client([
    'version' => 'latest',
    'region'  => 'us-east-1'
]);

// Отправка запроса PutObject
$s3Client->putObject([
    'Bucket' => 'bucket',
    'Key'    => 'key',
    'Body'   => 'body'
]);

// Загрузка объекта
$result = $s3Client->getObject([
    'Bucket' => 'bucket',
    'Key'    => 'key'
]);

// Удаление контейнера
$client->deleteBucket([
    'Bucket' => 'test-bucket',
]);
```

### 8. Используется интеграция со службой доставки для расчета стоимости (например, PickPoint или Почта России)
[]()


### 9. Используется интеграция с социальными сетями для авторизации пользователей
[]()

### 10. Данные о товарах регулярно отправляются в Яндекс.Маркет
[]()

### 11. Принимается онлайн-оплата от покупателей
[]()

### 12. Применяются средства тестирования (например, PHPUnit)
[]()
