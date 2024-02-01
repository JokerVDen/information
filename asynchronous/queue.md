В Laravel очереди (Queue) представляют собой механизм для отложенного выполнения задач. Это позволяет выполнять
длительные операции асинхронно, что повышает производительность вашего приложения и улучшает пользовательский опыт.

Вот пример использования очередей в Laravel:

1. **Настройка очередей:** В Laravel очереди могут быть настроены для использования различных драйверов, таких как база
   данных, Redis, Amazon SQS и другие. Настройка драйвера очереди происходит в файле конфигурации `config/queue.php`.

2. **Создание задачи (Job):** Задача (Job) представляет собой класс, который определяет работу, которую нужно выполнить
   асинхронно. Каждая задача наследуется от базового класса `Illuminate\Queue\Jobs\Job` и реализует метод `handle()`,
   который содержит логику задачи.

Пример класса задачи (app/Jobs/SendEmail.php):

```php
<?php

namespace App\Jobs;

use Illuminate\Bus\Queueable;
use Illuminate\Contracts\Queue\ShouldQueue;
use Illuminate\Queue\InteractsWithQueue;
use Illuminate\Queue\SerializesModels;

class SendEmail implements ShouldQueue
{
    use InteractsWithQueue, Queueable, SerializesModels;

    protected $user;

    public function __construct($user)
    {
        $this->user = $user;
    }

    public function handle()
    {
        // Логика отправки электронной почты пользователю
        \Mail::to($this->user->email)->send(new \App\Mail\WelcomeEmail($this->user));
    }
}
```

3. **Добавление задач в очередь:** Чтобы добавить задачу в очередь, вы можете использовать фасад `Queue` или
   метод `dispatch()` из диспетчера очередей.
   Пример добавления задачи в очередь:

```php
use App\Jobs\SendEmail;

$user = App\User::find(1);

SendEmail::dispatch($user);
```

4. **Обработка задач:** Laravel предоставляет команду `php artisan queue:work`, которая обрабатывает задачи в очереди. Эту
   команду можно запускать непрерывно, чтобы непрерывно обрабатывать задачи из очереди.
   Пример запуска обработчика очереди:

```shell
php artisan queue:work
```

Таким образом, при добавлении задачи `SendEmail` в очередь, Laravel поместит эту задачу в очередь, а затем обработчик
очереди автоматически выполнит эту задачу асинхронно, когда придет её очередь.

[На главную Асинхронность](main.md)
