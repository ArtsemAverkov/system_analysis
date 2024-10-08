[Вопросы для собеседования](README.md)

# Форматы данных

+ [форматы данных](#форматы-данных)
+ [XML](#XML)
+ [XML Schema Definition](#XML-Schema-Definition)
+ [JSON](#JSON)
+ [JSON Schema](#JSON-Schema)
+ [Полный обзор валидации JSON с использованием JSON Schema](#Полный-обзор-валидации-JSON-с-использованием-JSON-Schema)
+ [YAML](#YAML)
+ [Регулярные выражения](#Регулярные-выражения)




# форматы данных

`Форматы данных `– это стандартизированные способы представления информации, которые позволяют обмениваться данными между системами. Они обеспечивают структурирование данных, делая их удобными для хранения, передачи и обработки.

## XML (eXtensible Markup Language)

`Описание:` Теговый формат данных, использующий иерархическую структуру для представления данных.

### Преимущества:

- Читаемость и самодокументируемость.
- Хорошо подходит для сложных и иерархических структур данных.
- Широкая поддержка и множество инструментов для работы.


### Недостатки:

- Избыточность: большое количество тегов увеличивает объем данных.
- Сложность обработки по сравнению с более простыми форматами.


Пример XML:

```xml

<book>
  <title>XML Developer's Guide</title>
  <author>John Doe</author>
  <price>44.95</price>
</book>
```

## JSON (JavaScript Object Notation)


`Описание:` Легковесный формат обмена данными, который легко читается и пишется человеком и легко парсится и генерируется компьютерами.


`Преимущества:`

- Простота и читаемость.
- Менее избыточен по сравнению с XML.
- Поддержка большинства языков программирования.

`Недостатки:`

- Менее строгий и универсальный для сложных структур по сравнению с XML.
- Нет встроенной схемы валидации (хотя существуют сторонние решения).

Пример JSON:


```json

{
  "title": "JSON Developer's Guide",
  "author": "Jane Doe",
  "price": 39.95
}
```


## YAML (YAML Ain't Markup Language)


`Описание:` Формат сериализации данных, ориентированный на удобочитаемость и возможность легкого написания данных человеком.


`Преимущества:`

- Читаемость и простота синтаксиса.
- Поддержка сложных структур данных (массивы, словари, вложенные структуры).
- Легкость интеграции с современными языками программирования.

`Недостатки:`

- Меньшая популярность по сравнению с XML и JSON.
- Возможны ошибки при парсинге из-за чувствительности к отступам.


Пример YAML:

```yaml

title: YAML Developer's Guide
author: Jake Doe
price: 29.95
```

### Применение форматов данных

- `XML:` Используется в сложных иерархических системах, таких как веб-сервисы (SOAP), конфигурационные файлы и документация.
- `JSON: `Популярен в веб-разработке (REST API), для передачи данных между сервером и клиентом, а также для хранения данных.
- `YAML:` Широко используется для конфигурационных файлов в DevOps и CI/CD системах (например, Ansible, Kubernetes).

Таким образом, выбор формата данных зависит от конкретных требований проекта, таких как объем данных, сложность структуры, потребности в читаемости и простоте обработки.


[к оглавлению](#Форматы-данных)


# XML

`XML (Extensible Markup Language)` — это язык разметки, предназначенный для хранения и передачи данных. В отличие от HTML, который используется для отображения данных, XML предназначен для описания и структурирования данных.

### Основные компоненты XML

- `Элементы (Elements):` Основные строительные блоки XML-документа.
- `Атрибуты (Attributes): `Дополнительные данные, предоставляемые элементам.
- `Теги (Tags):` Обрамляют элементы и атрибуты.
- `Прокомментированные секции (Comments):` Описания или заметки, которые не обрабатываются парсерами.
- `Пролог (Prolog): `Введение в XML-документ, содержащее объявление XML и, возможно, инструкции по обработке.


Пример XML-документа

```xml

<?xml version="1.0" encoding="UTF-8"?>
<bookstore>
  <book category="programming">
    <title lang="en">XML Developer's Guide</title>
    <author>John Doe</author>
    <year>2024</year>
    <price>44.95</price>
  </book>
  <book category="fiction">
    <title lang="en">Fictional Book</title>
    <author>Jane Doe</author>
    <year>2021</year>
    <price>19.95</price>
  </book>
</bookstore>
```


Подробное описание компонентов XML

`1. Пролог (Prolog)`
Пролог находится в самом начале XML-документа и включает в себя объявление XML и, возможно, инструкции по обработке.
```
<?xml version="1.0" encoding="UTF-8"?>
```

- version: Указывает версию XML (обычно "1.0").
- encoding: Указывает кодировку символов (обычно "UTF-8").


`2. Элементы (Elements)`
Элементы являются основными строительными блоками XML-документа. Они могут содержать текст, атрибуты, другие элементы или все вышеперечисленное.

```
<book>
  <title>XML Developer's Guide</title>
  <author>John Doe</author>
  <year>2024</year>
  <price>44.95</price>
</book>
```

- Начальный тег: `<book>`
- Конечный тег: `</book>`
- Содержимое элемента: текст и вложенные элементы (например, `<title>, <author>`).


`3. Атрибуты (Attributes)`
Атрибуты предоставляют дополнительную информацию о элементах и находятся внутри начальных тегов элементов.


```
<book category="programming">
  <title lang="en">XML Developer's Guide</title>
</book>
```

- category: Атрибут элемента `<book>.`
- lang: Атрибут элемента `<title>.`


`4. Прокомментированные секции (Comments)`
Комментарии используются для добавления заметок или описаний в XML-документ, которые не обрабатываются парсерами.

```xml

<!-- This is a comment -->
```

`5. Теги (Tags)`
Теги обрамляют элементы и атрибуты. В XML различают начальные и конечные теги.

```xml

<book> ... </book>
```

### Правила написания XML

- Корневой элемент: Каждый XML-документ должен иметь один корневой элемент, который содержит все остальные элементы.
- Иерархия: Элементы должны быть правильно вложены.
- Закрытие тегов: Каждый элемент должен иметь начальный и конечный теги.
- Чувствительность к регистру: Теги и атрибуты чувствительны к регистру.
- Экранирование специальных символов: Некоторые символы должны быть экранированы (например, &, <, >).


### Преимущества XML

- `Читаемость:` XML-документы легко читаются и понимаются как человеком, так и машиной.
- `Самодокументируемость:` Теги XML описывают данные, что делает структуру документа интуитивно понятной.
- `Гибкость:` XML не имеет фиксированного набора тегов, что позволяет создавать пользовательские схемы данных.
- `Расширяемость:` Легко добавлять новые элементы и атрибуты без нарушения существующих данных.
- `Межплатформенность:` XML является стандартом W3C и поддерживается большинством современных языков программирования и платформ.


### Недостатки XML

- `Избыточность:` Большое количество тегов увеличивает объем данных.
- `Сложность обработки:` Парсинг XML может быть более сложным и медленным по сравнению с более легковесными форматами (например, JSON).
- `Производительность:` За счет избыточности и сложности парсинга, работа с XML может требовать больше ресурсов.

### Использование XML

- `Веб-сервисы:` Использование в SOAP для обмена данными между веб-приложениями.
- `Конфигурационные файлы:` Применение в конфигурационных файлах для настройки приложений и систем.
- `Документирование данных:` Использование для хранения и обмена структурированными данными.
- `Программные интерфейсы:` Использование в API для передачи данных.


**Заключение**

XML остается важным и мощным инструментом для работы с данными, особенно в случаях, требующих гибкости и самоописания данных. Несмотря на появление более легковесных альтернатив, таких как JSON и YAML, XML продолжает широко использоваться в различных областях благодаря своим уникальным преимуществам.


[к оглавлению](#Форматы-данных)


# XML Schema Definition

`XML Schema Definition (XSD)` — это язык для определения структуры и типа данных XML-документа. XSD предоставляет мощные возможности для валидации XML-документов, обеспечивая соответствие данных заданным правилам.

### Основные компоненты XSD

- `Элементы (Elements):` Определяют данные, которые могут появляться в XML-документе.
- `Атрибуты (Attributes):` Определяют свойства элементов.
- `Типы данных (Data Types):` Указывают тип данных элементов и атрибутов.
- `Комплексы типов (Complex Types):` Определяют элементы, которые могут содержать другие элементы и атрибуты.
- `Простые типы (Simple Types):` Определяют элементы и атрибуты, которые содержат текстовые данные.




Рассмотрим пример XSD для XML-документа, описывающего книги.


```xml

<?xml version="1.0" encoding="UTF-8"?>
<xs:schema xmlns:xs="http://www.w3.org/2001/XMLSchema">
  <!-- Определение элемента bookstore -->
  <xs:element name="bookstore">
    <xs:complexType>
      <xs:sequence>
        <!-- Определение элемента book -->
        <xs:element name="book" maxOccurs="unbounded">
          <xs:complexType>
            <xs:sequence>
              <!-- Определение элемента title -->
              <xs:element name="title">
                <xs:complexType>
                  <xs:simpleContent>
                    <xs:extension base="xs:string">
                      <xs:attribute name="lang" type="xs:string" use="required"/>
                    </xs:extension>
                  </xs:simpleContent>
                </xs:complexType>
              </xs:element>
              <!-- Определение элемента author -->
              <xs:element name="author" type="xs:string"/>
              <!-- Определение элемента year -->
              <xs:element name="year" type="xs:gYear"/>
              <!-- Определение элемента price -->
              <xs:element name="price" type="xs:decimal"/>
            </xs:sequence>
            <!-- Определение атрибута category -->
            <xs:attribute name="category" type="xs:string" use="required"/>
          </xs:complexType>
        </xs:element>
      </xs:sequence>
    </xs:complexType>
  </xs:element>
</xs:schema>
```

### Объяснение XSD

Пролог и пространство имен:
```
<?xml version="1.0" encoding="UTF-8"?>
<xs:schema xmlns:xs="http://www.w3.org/2001/XMLSchema">
```
`xmlns`
: Пространство имен для элементов схемы XSD.
Определение элемента bookstore:
```
<xs:element name="bookstore">
  <xs:complexType>
    <xs:sequence>
      <!-- Определение элемента book -->
```


- xs:element: Определяет элемент XML.
- xs:complexType: Указывает, что элемент содержит другие элементы.
- xs:sequence: Определяет последовательность вложенных элементов.



### Определение элемента book:
```
<xs:element name="book" maxOccurs="unbounded">
  <xs:complexType>
    <xs:sequence>
      <!-- Определение элемента title -->
```
`name="book": `Имя элемента.

`maxOccurs="unbounded":` Элемент может повторяться неограниченное количество раз.


### Определение элемента title:
```
<xs:element name="title">
  <xs:complexType>
    <xs:simpleContent>
      <xs:extension base="xs:string">
        <xs:attribute name="lang" type="xs:string" use="required"/>
      </xs:extension>
    </xs:simpleContent>
  </xs:complexType>
</xs:element>
```

`xs:simpleContent: `Используется для элементов, содержащих текст и атрибуты.
`<xs`
`base="xs`

`">:` Расширяет базовый тип данных xs:string.

`xs:attribute: `Определяет атрибут элемента.


### Определение элементов author, year и price:
```
<xs:element name="author" type="xs:string"/>
<xs:element name="year" type="xs:gYear"/>
<xs:element name="price" type="xs:decimal"/>
```
```
type="xs
": Тип данных элемента.
type="xs
": Тип данных для года.
type="xs
": Тип данных для цены.
```

### Определение атрибута category для элемента book:
```
<xs:attribute name="category" type="xs:string" use="required"/>
```
```
name="category": Имя атрибута.
type="xs
": Тип данных атрибута.
use="required": Атрибут обязателен.

```
[к оглавлению](#Форматы-данных)


# JSON

JSON (JavaScript Object Notation) — это легковесный формат обмена данными, который легко читается и пишется людьми, а также легко парсится и генерируется машинами. JSON часто используется для передачи данных между клиентом и сервером в веб-приложениях.

### Основные компоненты JSON

- `Объекты (Objects):` Представляют собой коллекцию пар "ключ-значение".
- `Массивы (Arrays):` Представляют собой упорядоченный список значений.
- `Значения (Values):` Могут быть объектами, массивами, строками, числами, логическими значениями или null.
- `Строки (Strings):` Последовательности символов, заключенные в двойные кавычки.
- `Числа (Numbers):` Целые и дробные числа.
- `Логические значения (Booleans):` true и false.
- `Null:` Специальное значение, представляющее собой отсутствие значения.

Пример JSON-документа
```
{
  "bookstore": [
    {
      "category": "programming",
      "title": "JSON Developer's Guide",
      "author": "John Doe",
      "year": 2024,
      "price": 44.95,
      "available": true
    },
    {
      "category": "fiction",
      "title": "Fictional Book",
      "author": "Jane Doe",
      "year": 2021,
      "price": 19.95,
      "available": false
    }
  ]
}
```

Объяснение компонентов JSON

`Объект (Object):`

```
{
  "key": "value",
  "key2": "value2"
}
```

Заключен в фигурные скобки {}.

- Состоит из пар "ключ-значение", разделенных запятыми.
- Ключи — строки, заключенные в двойные кавычки.
- Значения могут быть любого допустимого типа данных.

Массив (Array):
```
[
  "value1",
  "value2",
  "value3"
]
```

`Заключен в квадратные скобки [].`

Состоит из упорядоченного списка значений, разделенных запятыми.

`Строка (String): `
```
"This is a string"
```

`Заключена в двойные кавычки.`

Может содержать любые символы Unicode.

`Число (Number):`
```
1234
-1234
1234.56
-1234.56
```

- Может быть целым или дробным.
- Поддерживает научную нотацию.


`Логическое значение (Boolean):`

```
true
false
```

`Null:`

```
null
```

### Преимущества JSON

- Простота: Легко читается и пишется человеком.
- Легковесность: Меньший объем данных по сравнению с XML.
- Машинная обработка: Легко парсится и генерируется на большинстве языков программирования.
- Является подмножеством JavaScript: Природная совместимость с JavaScript, что делает его идеальным для веб-приложений.
- Гибкость: Поддержка сложных вложенных структур (объектов и массивов).


### Недостатки JSON

- Отсутствие схемы: Нет встроенного механизма для валидации структуры данных, как в XML с XSD.
- Поддержка типов данных: Ограниченная поддержка типов данных (нет явной поддержки для даты, времени и т. д.).
- Безопасность: При неправильной обработке может быть уязвим для атак, таких как JSON Injection.


Использование JSON

- `Передача данных в веб-приложениях:` Использование в AJAX-запросах для обмена данными между клиентом и сервером.
- `Конфигурационные файлы:` Использование для хранения настроек приложений.
- `API:` Использование в RESTful API для передачи данных между различными системами.
- `Логирование:` Использование для записи логов и событий.



[к оглавлению](#Форматы-данных)


# JSON Schema

`JSON Schema` — это мощный инструмент для валидации и описания структуры JSON-документов. Он позволяет определить правила, которым должны соответствовать данные в JSON, включая типы данных, допустимые значения и структуры объектов.


Основные компоненты JSON Schema

- `Типы данных (Data Types):` JSON Schema поддерживает основные типы данных JSON, такие как string, number, integer, boolean, object, array, и null.
- `Свойства объектов (Properties):` Описание структуры объектов, включая обязательные и необязательные поля.
- `Паттерны (Patterns):` Регулярные выражения для проверки строк.
- `Ограничения (Constraints):` Ограничения на значения, такие как минимальная и максимальная длина строки, минимальное и максимальное значение числа.
- `Ссылки (References):` Возможность ссылаться на другие схемы.


Пример JSON Schema

Рассмотрим JSON-документ, описывающий книги, и создадим для него схему.
JSON-документ (books.json)

```
{
  "bookstore": [
    {
      "category": "programming",
      "title": "JSON Developer's Guide",
      "author": "John Doe",
      "year": 2024,
      "price": 44.95,
      "available": true
    },
    {
      "category": "fiction",
      "title": "Fictional Book",
      "author": "Jane Doe",
      "year": 2021,
      "price": 19.95,
      "available": false
    }
  ]
}
```

JSON Schema (books-schema.json)

```
{
  "$schema": "http://json-schema.org/draft-07/schema#",
  "type": "object",
  "properties": {
    "bookstore": {
      "type": "array",
      "items": {
        "type": "object",
        "properties": {
          "category": {
            "type": "string"
          },
          "title": {
            "type": "string"
          },
          "author": {
            "type": "string"
          },
          "year": {
            "type": "integer",
            "minimum": 1000,
            "maximum": 9999
          },
          "price": {
            "type": "number",
            "minimum": 0
          },
          "available": {
            "type": "boolean"
          }
        },
        "required": ["category", "title", "author", "year", "price"]
      }
    }
  },
  "required": ["bookstore"]
}

```

Объяснение JSON Schema

`Корневой объект и $schema:`

```
{
  "$schema": "http://json-schema.org/draft-07/schema#",
  "type": "object",
  "properties": {
```

- `$schema:` Указывает версию JSON Schema.
- `type:` Определяет, что корневой элемент является объектом.
- `properties:` Содержит описание свойств объекта.

`Массив bookstore:`

```
"bookstore": {
  "type": "array",
  "items": {
    "type": "object",
    "properties": {
```

- type: Определяет, что bookstore является массивом.
- items: Описывает структуру объектов внутри массива.


`Свойства объектов в массиве bookstore:`

```
"category": {
  "type": "string"
},
"title": {
  "type": "string"
},
"author": {
  "type": "string"
},
"year": {
  "type": "integer",
  "minimum": 1000,
  "maximum": 9999
},
"price": {
  "type": "number",
  "minimum": 0
},
"available": {
  "type": "boolean"
}
```

- `type:` Определяет тип данных для каждого свойства (строка, число, логическое значение).
- `minimum и maximum:` Ограничивают значения для чисел.


`Обязательные свойства:`
```

"required": ["category", "title", "author", "year", "price"]
```

- `required:` Определяет обязательные свойства для объектов в массиве bookstore.

[к оглавлению](#Форматы-данных)



# Полный обзор валидации JSON с использованием JSON Schema

`JSON Schema `— мощный инструмент для описания структуры JSON-документов, включающий разнообразные возможности для валидации данных. Рассмотрим все основные ограничения и правила, которые можно задать с помощью JSON Schema.

Основные ограничения в JSON Schema

1. Типы данных (type)

Типы данных определяют, какой тип данных может принимать поле.
```
string
number
integer
object
array
boolean
null
```
Пример
```
{
  "type": "string"
}
```


2. Ограничения для строк

- `minLength:` Минимальная длина строки.
- `maxLength:` Максимальная длина строки.
- `pattern:` Регулярное выражение, которому должна соответствовать строка.
- `format:` Специальные форматы для строк (дата, email, URI и т.д.).


Пример
```
{
  "type": "string",
  "minLength": 5,
  "maxLength": 100,
  "pattern": "^[a-zA-Z]+$",
  "format": "email"
}
```


3. Ограничения для чисел

- `minimum:` Минимальное значение.
- `maximum:` Максимальное значение.
- `exclusiveMinimum:` Минимальное значение (исключающее).
- `exclusiveMaximum:` Максимальное значение (исключающее).
- `multipleOf:` Число должно быть кратно указанному значению.


Пример
```
{
  "type": "number",
  "minimum": 0,
  "maximum": 100,
  "exclusiveMinimum": 0,
  "exclusiveMaximum": 100,
  "multipleOf": 5
}
```

4. Ограничения для объектов

- `properties:` Описание свойств объекта.
- `required:` Список обязательных полей.
- `additionalProperties:` Разрешение или запрет дополнительных свойств.
- `minProperties:` Минимальное количество свойств.
- `maxProperties:` Максимальное количество свойств.
- `dependencies:` Зависимости между свойствами.


Пример
```
{
  "type": "object",
  "properties": {
    "name": {
      "type": "string"
    },
    "age": {
      "type": "integer"
    }
  },
  "required": ["name"],
  "additionalProperties": false,
  "minProperties": 1,
  "maxProperties": 3,
  "dependencies": {
    "age": ["name"]
  }
}
```

5. Ограничения для массивов

- `items:` Схема для элементов массива.
- `minItems:` Минимальное количество элементов.
- `maxItems:` Максимальное количество элементов.
- `uniqueItems:` Все элементы должны быть уникальными.


Пример
```
{
  "type": "array",
  "items": {
    "type": "string"
  },
  "minItems": 1,
  "maxItems": 10,
  "uniqueItems": true
}
```

6. Комбинированные схемы

- `allOf:` Все указанные схемы должны быть выполнены.
- `anyOf:` Должна быть выполнена хотя бы одна из указанных схем.
- `oneOf:` Должна быть выполнена ровно одна из указанных схем.
- `not:` Данные не должны соответствовать указанной схеме.


Пример

```
{
  "allOf": [
    { "type": "string" },
    { "maxLength": 5 }
  ],
  "anyOf": [
    { "type": "string" },
    { "type": "number" }
  ],
  "oneOf": [
    { "type": "string" },
    { "type": "number" }
  ],
  "not": {
    "type": "null"
  }
}
```

[к оглавлению](#Форматы-данных)

# YAML

YAML (YAML Ain't Markup Language) — это человекочитаемый формат сериализации данных, который часто используется для конфигурационных файлов и обмена данными между языками программирования с динамической типизацией.


### Основные особенности YAML

- `Человекочитаемость:` YAML фокусируется на том, чтобы данные были легко читаемы и писаны людьми.
- `Иерархическая структура:` Использование отступов для представления вложенности данных.
- `Множество типов данных:` Поддержка различных типов данных, включая строки, числа, массивы, ассоциативные массивы и др.
- `Комментарии:` Поддержка комментариев, которые начинаются с #.

### Основные компоненты YAML

- `Ключ-значение:` Определение данных в виде пар "ключ-значение".
- `Списки:` Перечисление значений в виде списка.
- `Многострочные строки:` Поддержка многострочных строк.
- `Ссылки и привязки:` Возможность ссылаться на ранее определенные значения.


Пример YAML-документа

Рассмотрим пример конфигурационного файла YAML для описания книги.

```YAML

bookstore:
  - category: programming
    title: "YAML Developer's Guide"
    author: John Doe
    year: 2024
    price: 44.95
    available: true
  - category: fiction
    title: "Fictional Book"
    author: Jane Doe
    year: 2021
    price: 19.95
    available: false
```

### Объяснение компонентов YAML
```
Ключ-значение:
title: "YAML Developer's Guide"
```
```
title: Ключ.
"YAML Developer's Guide": Значение.
```
```
Списки:
- category: programming
  title: "YAML Developer's Guide"
```
```
Списки обозначаются дефисами -.
```
```
Многострочные строки:
description: >

  Это многострочная
  строка в YAML.
```

- Символ > используется для многострочных строк с сохранением пробелов.
- Символ | используется для многострочных строк с сохранением разрывов строк.

```
Комментарии:

# Это комментарий
title: "YAML Developer's Guide"
```
*Комментарии начинаются с #.*



### Преимущества YAML


- Человекочитаемость: Легко читается и пишется человеком.
- Простота: Минимальный синтаксис без сложных структур.
- Гибкость: Поддержка различных типов данных и структур.
- Является подмножеством JSON: YAML может быть легко преобразован в JSON и наоборот.



### Недостатки YAML

- Отступы: Использование отступов для вложенности может привести к ошибкам, если они неправильно использованы.
- Поддержка типов данных: Ограниченная поддержка типов данных по сравнению с некоторыми другими форматами.
- Производительность: Медленнее парсится по сравнению с JSON.
- Использование YAML
- Конфигурационные файлы: Часто используется для настройки приложений и сервисов.
- Обмен данными: Используется для обмена данными между различными системами и языками программирования.
- Документация: Используется для написания человекочитаемой документации.


[к оглавлению](#Форматы-данных)

# Регулярные выражения

`Регулярные выражения (RegEx, от англ. Regular Expressions) `— это мощный инструмент для поиска, сопоставления и манипулирования текстом. Они используются для описания шаблонов строк, которые могут использоваться для проверки, поиска и замены текста.

### Основные элементы регулярных выражений

`Литералы:` Обычные символы, которые совпадают сами с собой.
Пример: a соответствует "a".

`Мета-символы:` Специальные символы с особыми значениями.
- .: Соответствует любому одиночному символу, кроме новой строки.
- ^: Начало строки.
- $: Конец строки.
- *: 0 или более повторений предыдущего элемента.
- +: 1 или более повторений предыдущего элемента.
- ?: 0 или 1 повторение предыдущего элемента.
- \: Экранирование специального символа.

`Квантификаторы:` Определяют количество повторений элемента.
- {n}: Ровно n повторений.
- {n,}: n или более повторений.
- {n,m}: От n до m повторений.

`Группировка и альтернативы:`
- (): Группировка элементов.
- |: Альтернатива (логическое ИЛИ).

`Классы символов:`
- [abc]: Любой из символов a, b или c.
- [^abc]: Любой символ, кроме a, b или c.
- [a-z]: Любой символ от a до z.

`Предопределенные классы символов:`
- \d: Любая цифра (эквивалент [0-9]).
- \D: Любой символ, кроме цифры.
- \w: Любая буква, цифра или символ подчеркивания (эквивалент [A-Za-z0-9_]).
- \W: Любой символ, кроме букв, цифр и символа подчеркивания.
- \s: Любой пробельный символ.
- \S: Любой символ, кроме пробельного.

### Примеры регулярных выражений

Проверка email-адреса

```regex

^[a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,}$
```
- `^[a-zA-Z0-9._%+-]+:` Начало строки, за которым следуют один или более символов, состоящих из букв, цифр, точки, подчеркивания, процента, плюса или дефиса.
- `@[a-zA-Z0-9.-]+:` Знак @, за которым следует один или более символов, состоящих из букв, цифр, точки или дефиса.
- `\.[a-zA-Z]{2,}$:` Точка, за которой следует два или более символов из букв, и конец строки.


### Проверка номера телефона (формат: +XXX-XXXX-XXXX)

```regex


^\+\d{3}-\d{4}-\d{4}$

^\+: Начало строки и знак +.
\d{3}: Три цифры.
-: Дефис.
\d{4}: Четыре цифры.
-: Дефис.
\d{4}$: Четыре цифры и конец строки.
```

[к оглавлению](#Форматы-данных)

