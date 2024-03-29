## Транзакционность в Redis

Redis поддерживает транзакции, которые позволяют выполнить несколько команд как одну атомарную операцию. Это означает,
что либо все команды в транзакции будут выполнены, либо ни одна из них.

### Ключевые особенности транзакций в Redis:

1. **MULTI**: Эта команда начинает новую транзакцию.
2. Выполнение всех команд внутри транзакции.
3. **EXEC**: Эта команда выполняет все команды, добавленные в транзакцию.
4. Если все команды успешно выполнены, транзакция завершается успешно. Если хотя бы одна команда в транзакции вызывает
   ошибку, транзакция отменяется и никакие изменения не применяются.
5. Redis блокирует конкурентные операции других клиентов, пока транзакция не завершится.

### Пример использования транзакций Redis:

```redis
MULTI
SET key1 "value1"
SET key2 "value2"
EXEC
```

В этом примере мы начинаем транзакцию с помощью команды `MULTI`, затем добавляем две команды `SET` для установки
значений ключей `key1` и `key2`, и наконец, выполняем все эти команды с помощью команды `EXEC`.

Транзакции в Redis обеспечивают атомарность и консистентность при выполнении нескольких операций, что делает их
полезными инструментами для решения различных задач, таких как обновление нескольких ключей в одной операции или
выполнение серии связанных операций как одну атомарную операцию.

[Redis на главную](main.md)
