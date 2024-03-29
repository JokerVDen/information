### Виды блокировок:

1. **Блокировка таблицы (Table Locks)**:
    - Блокирует всю таблицу для определенного типа операции (чтение, запись и т. д.).
    - Применяется с помощью операторов `LOCK TABLES` и `UNLOCK TABLES`.

2. **Блокировка строк (Row Locks)**:
    - Блокирует отдельные строки в таблице.
    - Обычно используется для обеспечения согласованности данных в многопользовательской среде.
    - MySQL автоматически устанавливает блокировки строк в рамках транзакций, если используется соответствующий уровень
      изоляции.

### Проблемы с блокировками:

1. **Blocking (блокирование)**:
    - Это ситуация, когда один процесс или транзакция блокирует доступ к ресурсу (например, строке данных или таблице) и
      не позволяет другим процессам или транзакциям получить доступ к этому ресурсу до тех пор, пока блокировка не будет
      снята.
    - Blocking может быть временным и решается, когда ресурс снова становится доступным.
    - Обычно происходит из-за операций записи, когда одна транзакция изменяет данные и удерживает блокировку на них, что
      может предотвратить доступ других транзакций к этим данным до завершения операции.

2. **Deadlock (взаимоблокировка)**:
    - Это более серьезная ситуация, когда два или более процесса или транзакции взаимно блокируют друг друга, ожидая
      освобождения ресурсов, которые удерживают другие процессы в цепочке.
    - В отличие от обычного blocking, deadlock является более критической проблемой, так как процессы не могут
      разрешиться без внешнего вмешательства или обработки, например, через обнаружение и разрешение deadlock'ов.
    - Deadlock'и могут возникать из-за неправильного управления блокировками, взаимных ожиданий и синхронизации
      ресурсов.

Таким образом, основное различие между blocking и deadlock заключается в степени серьезности проблемы и способах ее
решения. Blocking - это временное препятствие, в то время как deadlock - это более серьезная проблема, которая требует
специальных мер для ее предотвращения и разрешения.

### Способы обнаружения блокировок:

1. **Использование инструментов мониторинга**:
    - MySQL предоставляет множество инструментов мониторинга, таких как MySQL Enterprise Monitor, MySQL Workbench,
      Percona Monitoring and Management (PMM) и другие, которые позволяют отслеживать активные блокировки и долгие
      запросы.

2. **Использование команды SHOW**:

_**SHOW PROCESSLIST:**_

Команда `SHOW PROCESSLIST` в MySQL отображает список текущих активных процессов (запросов), выполняемых на сервере
MySQL. Это мощный инструмент для мониторинга активности сервера и выявления проблем с производительностью. Ниже
приведены основные столбцы, которые можно увидеть в выводе команды `SHOW PROCESSLIST`:

- **Id**: Идентификатор процесса (ID).
- **User**: Пользователь, от имени которого выполняется запрос.
- **Host**: Хост, откуда поступил запрос.
- **db**: Имя базы данных, с которой связан запрос.
- **Command**: Команда, которую выполняет процесс (например, Sleep, Query, Connect, Execute и т. д.).
- **Time**: Время, в течение которого запрос находится в этом состоянии.
- **State**: Текущее состояние запроса.
- **Info**: Информация о запросе (например, сам SQL-запрос).

Эта команда позволяет администраторам отслеживать активность базы данных, обнаруживать долгие запросы, анализировать
узкие места производительности и принимать меры по оптимизации запросов.

_**SHOW ENGINE INNODB STATUS:**_

Команда `SHOW ENGINE INNODB STATUS` предоставляет подробную информацию о текущем состоянии движка InnoDB в MySQL. Вывод
этой команды содержит различные сведения о внутренних операциях InnoDB, включая:

- **Информация о транзакциях**: Список активных транзакций, которые выполняются в данный момент, и их состояние.
- **Информация о блокировках**: Сведения о блокировках, которые в настоящее время удерживаются или ожидаются.
- **Журналы и буферы**: Статистика по журналам и буферам, используемым InnoDB для обеспечения целостности данных и
  производительности.
- **Информация о сегментах хранения**: Детали о сегментах хранения данных InnoDB, включая количество записей,
  использование пространства и т. д.

Эта команда полезна при анализе проблем с производительностью, выявлении взаимоблокировок (deadlocks), оптимизации
запросов и обнаружении прочих аномалий, связанных с работой движка InnoDB.

В целом, команды `SHOW PROCESSLIST` и `SHOW ENGINE INNODB STATUS` предоставляют важную информацию для мониторинга и
администрирования MySQL-сервера, помогая администраторам обнаруживать и устранять проблемы, связанные с
производительностью и целостностью данных.

3. **Использование мониторинговых скриптов**:
    - Можно написать скрипты, которые регулярно проверяют систему на наличие активных блокировок и проблем с
      блокировками.

4. **Использование журналов и логов**:
    - MySQL также записывает информацию о блокировках и взаимоблокировках в журналы и логи, такие как error log и slow
      query log. Эту информацию можно проанализировать, чтобы обнаружить проблемы с блокировками.

[SELECT ... FOR UPDATE](select-for-update.md)

[К оглавлению](../readme.md)
