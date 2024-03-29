## Паттерн "Значимый объект" (Value Object)

Паттерн "Значимый объект" является важным элементом в Domain-Driven Design (DDD). Он используется для представления
объектов, чья идентичность определяется их свойствами, а не уникальным идентификатором.

### Особенности значимых объектов:

- **Идентичность**: Значимый объект не имеет уникального идентификатора и равенство между объектами определяется их
  свойствами.

- **Неизменяемость**: Обычно значимые объекты являются неизменяемыми, то есть после создания их состояние не может быть
  изменено.

- **Сравнение по значению**: Для сравнения значимых объектов обычно используется сравнение их свойств, а не ссылок на
  объекты.

### Примеры значимых объектов:

- **Деньги**: Сумма денег (например, 100 USD) является значимым объектом. Она не имеет уникального идентификатора и
  сравнивается по своей величине.

- **Адрес**: Адрес (например, улица, город, почтовый индекс) также является значимым объектом. Два адреса с одинаковыми
  свойствами считаются равными.

### Преимущества использования паттерна "Значимый объект":

- **Простота и ясность**: Значимые объекты позволяют явно выразить понятия предметной области, не требуя для этого
  уникального идентификатора.

- **Предотвращение ошибок**: Благодаря неизменяемости и сравнению по значению, значимые объекты предотвращают случайные
  изменения и ошибки в системе.

- **Улучшение производительности**: Использование значимых объектов может повысить производительность системы, особенно
  при сравнении объектов.

[К паттернам DDD](main.md)

[На главную DDD](../main.md)