# Параллельные запросы

Иногда вам может потребоваться сделать несколько HTTP-запросов параллельно. Другими словами, вы хотите, чтобы несколько запросов были отправлены одновременно, а не последовательно. Это может привести к существенному улучшению производительности при взаимодействии с медленными HTTP-API.

К счастью, вы можете сделать это, используя метод `pool`. Метод `pool` принимает замыкание, которое получает экземпляр `Illuminate\Http\Client\Pool`, что позволяет вам легко добавлять запросы в пул запросов для отправки:

```php
use Illuminate\Http\Client\Pool;
use Illuminate\Support\Facades\Http;

$responses = Http::pool(fn (Pool $pool) => [
    $pool->get('http://localhost/first'),
    $pool->get('http://localhost/second'),
    $pool->get('http://localhost/third'),
]);

return $responses[0]->ok() &&
       $responses[1]->ok() &&
       $responses[2]->ok();
```