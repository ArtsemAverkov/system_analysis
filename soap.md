[Вопросы для собеседования](README.md)

# SOAP REST

+ [SOAP](#SOAP)
	+ [Правила и рекомендации SOAP API](#Правила-и-рекомендации-SOAP-API)
	+ [Примеры SOAP запросов и ответов](#Примеры-SOAP-запросов-и-ответов)
	+ [WSDL](#WSDL)
+ [REST](#REST)
	+ [Спецификация RESTful API](#Спецификация-RESTful-API)
	+ [Основные правила спецификации REST](#Основные-правила-спецификации-REST)
	+ [Примеры спецификации RESTful API](#Примеры-спецификации-RESTful-API)



# SOAP

`SOAP (Simple Object Access Protocol)` — это протокол для обмена структурированными информационными данными в распределенной вычислительной среде. Он основан на XML и предоставляет способ для передачи сообщений между сервисами в сети. Вот основные аспекты и правила спецификации SOAP API.

### Основные компоненты SOAP

`Envelope (Оболочка):`

*Это корневой элемент каждого SOAP-сообщения. Он определяет, что сообщение является SOAP-сообщением и содержит обязательные и необязательные части, такие как заголовок и тело.*

```xml
<soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/">
</soapenv:Envelope>
```

`Header (Заголовок):`

*Необязательный элемент. Используется для передачи метаинформации, такой как аутентификация, информация о маршрутизации и т.д.*

```xml
<soapenv:Header>
</soapenv:Header>
```


`Body (Тело):`

*Обязательный элемент. Содержит фактические данные, которые должны быть обработаны сервисом. В нем находятся запросы и ответы SOAP.*

```xml
<soapenv:Body>
</soapenv:Body>
```

### Формат SOAP-сообщений

Запрос

```xml
<soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:ns="http://example.com/namespace">
```


- `<soapenv:Envelope>:` Корневой элемент каждого SOAP-сообщения. Он определяет сообщение как SOAP-сообщение.
- `xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/":` Пространство имен, указывающее на стандартную схему SOAP.
- `xmlns:ns="http://example.com/namespace":` Пространство имен для пользовательских данных. "ns" используется как префикс для элементов, специфичных для данного веб-сервиса.


```xml
  <soapenv:Header/>

```

- `<soapenv:Header/>:` Заголовок сообщения SOAP. Это необязательная часть, которая может содержать метаинформацию, такую как данные для аутентификации. В данном случае заголовок пуст.

```xml
  <soapenv:Body>
```

- `<soapenv:Body>:` Тело сообщения SOAP. Обязательная часть, содержащая фактические данные запроса или ответа.

```xml
     <ns:RequestName>
```

- `<ns:RequestName>:` Пользовательский элемент, представляющий конкретный запрос к веб-сервису. "RequestName" — это имя запроса, определенное в пространстве имен "ns".

```xml
        <!-- Параметры запроса -->
```

- `<!-- Параметры запроса -->:` Здесь размещаются параметры, необходимые для выполнения запроса. Это могут быть различные элементы данных, зависящие от конкретного запроса.

```xml
     </ns:RequestName>
   </soapenv:Body>
</soapenv:Envelope>
```


- </ns:RequestName>: Закрывающий тег для элемента запроса.
- </soapenv:Body>: Закрывающий тег для тела сообщения.
- </soapenv:Envelope>: Закрывающий тег для всего SOAP-сообщения.



### Вариации запроса
Заголовок может содержать различные элементы, например:

```xml
<soapenv:Header>
  <ns:Auth>
    <ns:Username>user</ns:Username>
    <ns:Password>pass</ns:Password>
  </ns:Auth>
</soapenv:Header>
```

В теле могут быть разные параметры:

```xml
<ns:RequestName>
  <ns:Param1>value1</ns:Param1>
  <ns:Param2>value2</ns:Param2>
</ns:RequestName>
```

Ответ

```xml
<soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:ns="http://example.com/namespace">
```

Аналогично запросу, корневой элемент и пространства имен.

```xml
  <soapenv:Header/>
```

Заголовок сообщения. В данном случае он пуст, но может содержать метаинформацию.

```xml
  <soapenv:Body>
```

Тело сообщения, содержащее данные ответа.

```xml
     <ns:ResponseName>
```

Элемент, представляющий ответ от веб-сервиса. "ResponseName" — имя ответа, определенное в пространстве имен "ns".

```xml
        <!-- Данные ответа -->
```

<!-- Данные ответа -->: Здесь размещаются данные, возвращаемые веб-сервисом в ответ на запрос. Это могут быть различные элементы данных, зависящие от конкретного ответа.

```xml
     </ns:ResponseName>
   </soapenv:Body>
</soapenv:Envelope>
```

- </ns:ResponseName>: Закрывающий тег для элемента ответа.
- </soapenv:Body>: Закрывающий тег для тела сообщения.
- </soapenv:Envelope>: Закрывающий тег для всего SOAP-сообщения.


Вариации ответа
Заголовок может содержать различные элементы, такие как метаинформация об ответе:

```xml
<soapenv:Header>
  <ns:ResponseMetadata>
    <ns:Timestamp>2024-07-04T12:34:56Z</ns:Timestamp>
  </ns:ResponseMetadata>
</soapenv:Header>
```

В теле могут быть разные данные:

```xml
<ns:ResponseName>
  <ns:Data1>value1</ns:Data1>
  <ns:Data2>value2</ns:Data2>
</ns:ResponseName>
```

### Заключение

Формат SOAP-сообщений основан на XML и обеспечивает структурированный способ обмена данными между клиентом и сервером. Ключевые элементы включают оболочку, заголовок и тело сообщения. Используя пространство имен, можно определить уникальные элементы для запросов и ответов, обеспечивая гибкость и масштабируемость веб-сервисов.


[к оглавлению](#SOAP-REST)

# Правила и рекомендации SOAP API

### Использование XML:

SOAP-сообщения должны быть хорошо сформированными XML-документами.
Включение пространств имен (namespaces) для предотвращения конфликтов имен.

`Пространства имен:`

Пространства имен используются для уникальной идентификации элементов в XML.

```xml
xmlns:ns="http://example.com/namespace"
```

`Стандарты и схемы:`

- Сообщения SOAP должны соответствовать определенной схеме XML Schema Definition (XSD).
- WSDL (Web Services Description Language) используется для описания доступных операций и типов данных.

`Обработка ошибок:`

В случае ошибки сервис должен возвращать SOAP Fault (ошибку SOAP).

```xml
<soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/">
   <soapenv:Body>
      <soapenv:Fault>
         <faultcode>soapenv:Client</faultcode>
         <faultstring>Invalid Request</faultstring>
         <detail>
            <!-- Дополнительная информация об ошибке -->
         </detail>
      </soapenv:Fault>
   </soapenv:Body>
</soapenv:Envelope>
```

`Транспорты:`

- Основной транспорт для SOAP — это HTTP/HTTPS.
- Использование других транспортов также возможно, например, SMTP.
- Безопасность:
- SOAP поддерживает WS-Security для обеспечения конфиденциальности, целостности и аутентификации сообщений.
- Использование SSL/TLS для защиты данных при передаче по сети.
- Расширяемость:
- SOAP специально разработан для того, чтобы быть расширяемым, позволяя добавлять новые элементы в заголовок и тело без нарушения существующих сервисов.


[к оглавлению](#SOAP-REST)


# Примеры SOAP запросов и ответов


`Получение данных о клиенте (Request)`

```xml
<soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:cli="http://example.com/client">
   <soapenv:Header/>
   <soapenv:Body>
      <cli:GetClientDataRequest>
         <cli:ClientID>12345</cli:ClientID>
      </cli:GetClientDataRequest>
   </soapenv:Body>
</soapenv:Envelope>
```

`Получение данных о клиенте (Response)`

```xml
<soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:cli="http://example.com/client">
   <soapenv:Header/>
   <soapenv:Body>
      <cli:GetClientDataResponse>
         <cli:Client>
            <cli:FullName>Иванов Иван Иванович</cli:FullName>
            <cli:BirthDate>1985-05-15</cli:BirthDate>
            <cli:Phone>+79991234567</cli:Phone>
            <cli:Email>ivanov@example.com</cli:Email>
            <cli:Documents>
               <cli:Document>
                  <cli:Type>Паспорт</cli:Type>
                  <cli:Number>1234567890</cli:Number>
                  <cli:Status>Активен</cli:Status>
               </cli:Document>
            </cli:Documents>
            <cli:ResidenceAddress>ул. Примерная, д. 1, кв. 1</cli:ResidenceAddress>
            <cli:RegistrationAddress>ул. Регистрационная, д. 2, кв. 3</cli:RegistrationAddress>
         </cli:Client>
      </cli:GetClientDataResponse>
   </soapenv:Body>
</soapenv:Envelope>
```


### Заключение

SOAP API обеспечивает надежный и стандартизированный способ обмена данными между распределенными системами. Он поддерживает сложные сценарии взаимодействия, такие как транзакции и маршрутизация сообщений, и обеспечивает высокий уровень безопасности. Эти особенности делают SOAP идеальным для корпоративных приложений и интеграционных решений.


[к оглавлению](#SOAP-REST)


# WSDL

`WSDL `(Web Services Description Language) является XML-языком, который используется для описания веб-сервисов и их интерфейсов. Он предоставляет способ для определения местоположения службы и операций, которые она поддерживает, что позволяет автоматизировать взаимодействие между различными системами.

### Структура WSDL документа

**Документ WSDL состоит из следующих основных элементов:**

- `definitions:` Корневой элемент WSDL документа, который содержит все остальные элементы. Он включает пространства имен, которые используются в документе.
- `types:` Определяет типы данных, используемые в сообщениях веб-сервиса. Этот раздел обычно использует XML Schema (XSD) для определения сложных типов данных.
- `message:` Определяет сообщения, которые обмениваются между клиентом и веб-сервисом. Сообщение состоит из одной или нескольких частей (part), каждая из которых может быть простым или сложным типом данных.
- `portType:` Описывает интерфейс веб-сервиса, определяя операции, которые он поддерживает. Каждая операция состоит из входного и выходного сообщений (и иногда сообщения об ошибках).
- `binding:` Указывает, какой транспортный протокол используется для взаимодействия с веб-сервисом (например, SOAP), и как сообщения должны быть закодированы.
- `service:` Определяет конкретные конечные точки (адреса), где веб-сервис доступен.


### Пример WSDL документа

Рассмотрим пример простого WSDL документа, описывающего веб-сервис для получения информации о книге:

```xml

<definitions xmlns="http://schemas.xmlsoap.org/wsdl/"
             xmlns:soap="http://schemas.xmlsoap.org/wsdl/soap/"
             xmlns:xsd="http://www.w3.org/2001/XMLSchema"
             xmlns:tns="http://example.com/bookservice"
             targetNamespace="http://example.com/bookservice">

    <types>
        <xsd:schema targetNamespace="http://example.com/bookservice">
            <xsd:element name="GetBookRequest">
                <xsd:complexType>
                    <xsd:sequence>
                        <xsd:element name="ISBN" type="xsd:string"/>
                    </xsd:sequence>
                </xsd:complexType>
            </xsd:element>
            <xsd:element name="GetBookResponse">
                <xsd:complexType>
                    <xsd:sequence>
                        <xsd:element name="Title" type="xsd:string"/>
                        <xsd:element name="Author" type="xsd:string"/>
                        <xsd:element name="Publisher" type="xsd:string"/>
                    </xsd:sequence>
                </xsd:complexType>
            </xsd:element>
        </xsd:schema>
    </types>

    <message name="GetBookRequestMessage">
        <part name="parameters" element="tns:GetBookRequest"/>
    </message>

    <message name="GetBookResponseMessage">
        <part name="parameters" element="tns:GetBookResponse"/>
    </message>

    <portType name="BookServicePortType">
        <operation name="GetBook">
            <input message="tns:GetBookRequestMessage"/>
            <output message="tns:GetBookResponseMessage"/>
        </operation>
    </portType>

    <binding name="BookServiceBinding" type="tns:BookServicePortType">
        <soap:binding transport="http://schemas.xmlsoap.org/soap/http"/>
        <operation name="GetBook">
            <soap:operation soapAction="http://example.com/bookservice/GetBook"/>
            <input>
                <soap:body use="literal"/>
            </input>
            <output>
                <soap:body use="literal"/>
            </output>
        </operation>
    </binding>

    <service name="BookService">
        <port name="BookServicePort" binding="tns:BookServiceBinding">
            <soap:address location="http://example.com/bookservice"/>
        </port>
    </service>
</definitions>

```


### Основные элементы WSDL документа

`Definitions`

Корневой элемент документа WSDL, который содержит другие элементы и задает пространство имен для документа:

```xml

<definitions xmlns="http://schemas.xmlsoap.org/wsdl/"
             xmlns:soap="http://schemas.xmlsoap.org/wsdl/soap/"
             xmlns:xsd="http://www.w3.org/2001/XMLSchema"
             xmlns:tns="http://example.com/bookservice"
             targetNamespace="http://example.com/bookservice">
```

`Types`

Определяет сложные типы данных, используемые в сообщениях. В данном примере используется XML Schema для определения типов:

```xml

<types>
    <xsd:schema targetNamespace="http://example.com/bookservice">
        <xsd:element name="GetBookRequest">
            <xsd:complexType>
                <xsd:sequence>
                    <xsd:element name="ISBN" type="xsd:string"/>
                </xsd:sequence>
            </xsd:complexType>
        </xsd:element>
        <xsd:element name="GetBookResponse">
            <xsd:complexType>
                <xsd:sequence>
                    <xsd:element name="Title" type="xsd:string"/>
                    <xsd:element name="Author" type="xsd:string"/>
                    <xsd:element name="Publisher" type="xsd:string"/>
                </xsd:sequence>
            </xsd:complexType>
        </xsd:element>
    </xsd:schema>
</types>
```


`Message`

Определяет сообщения, передаваемые между клиентом и сервером. Каждое сообщение состоит из одной или нескольких частей:

```xml

<message name="GetBookRequestMessage">
    <part name="parameters" element="tns:GetBookRequest"/>
</message>

<message name="GetBookResponseMessage">
    <part name="parameters" element="tns:GetBookResponse"/>
</message>
```

`PortType`

Описывает интерфейс веб-сервиса, определяя операции и их сообщения:

```xml

<portType name="BookServicePortType">
    <operation name="GetBook">
        <input message="tns:GetBookRequestMessage"/>
        <output message="tns:GetBookResponseMessage"/>
    </operation>
</portType>
```

`Binding`

Определяет, как операции и сообщения отображаются на конкретный протокол. В данном случае используется SOAP:

```xml

<binding name="BookServiceBinding" type="tns:BookServicePortType">
    <soap:binding transport="http://schemas.xmlsoap.org/soap/http"/>
    <operation name="GetBook">
        <soap:operation soapAction="http://example.com/bookservice/GetBook"/>
        <input>
            <soap:body use="literal"/>
        </input>
        <output>
            <soap:body use="literal"/>
        </output>
    </operation>
</binding>
```

`Service`

Определяет конкретные адреса, где доступен веб-сервис:

```xml

<service name="BookService">
    <port name="BookServicePort" binding="tns:BookServiceBinding">
        <soap:address location="http://example.com/bookservice"/>
    </port>
</service>
```
### Заключение

WSDL предоставляет стандартизированный способ описания веб-сервисов, что упрощает автоматизацию взаимодействия между различными системами и платформами. Он играет ключевую роль в экосистеме веб-сервисов, предоставляя подробные спецификации, необходимые для генерации клиентского и серверного кода, проверки сообщений и интеграции различных приложений.


[к оглавлению](#SOAP-REST)


# REST

`REST (Representational State Transfer)` — это архитектурный стиль для проектирования сетевых приложений, который фокусируется на системах, использующих HTTP для обмена данными. RESTful сервисы следуют принципам REST и часто используются для создания веб-сервисов.


### Основные принципы REST

`Клиент-серверная архитектура:`

- Клиенты и серверы взаимодействуют через четко определенные интерфейсы и протоколы, обычно HTTP.
- Клиенты инициируют запросы, а серверы обрабатывают их и возвращают ответы.

`Безсостоящность (Statelessness):`

- Каждое сообщение запроса от клиента к серверу должно содержать всю необходимую информацию для обработки запроса.
- Сервер не хранит состояние клиента между запросами.

`Кешируемость (Cacheability):`

- Ответы сервера должны быть явно помечены как кешируемые или некешируемые.
- Это помогает уменьшить нагрузку на сервер и улучшить производительность клиента.

`Единообразие интерфейса (Uniform Interface):`

- Использование стандартных методов HTTP (GET, POST, PUT, DELETE).
- Единый способ адресации ресурсов (URL).
- Стандартные форматы данных (JSON, XML).

`Многоуровневая система (Layered System):`

- Архитектура может состоять из нескольких уровней, где каждый уровень выполняет свою задачу (например, балансировка нагрузки, безопасность, прокси).

`Код по требованию (Code on Demand):`

- Сервер может предоставлять исполняемый код или скрипты клиенту, чтобы расширить его функциональность.

[к оглавлению](#SOAP-REST)


# Спецификация RESTful API


### Основные компоненты RESTful API

`Ресурсы:`

- Ресурсы идентифицируются уникальными URL-адресами.
- Каждый ресурс представляется определенным форматом данных (например, JSON, XML).

`Методы HTTP:`

- GET: Получение ресурса или коллекции ресурсов.
- POST: Создание нового ресурса.
- PUT: Обновление существующего ресурса.
- DELETE: Удаление ресурса.

`Структура URL:`

- URL-адреса должны быть понятными и легко читаемыми.
- Пример: http://example.com/api/clients/12345

`Заголовки HTTP:`

- Content-Type: Определяет тип данных запроса или ответа (например, application/json).
- Authorization: Используется для аутентификации и авторизации.

`Ответы HTTP:`

- 200 OK: Успешный запрос.
- 201 Created: Успешное создание ресурса.
- 204 No Content: Успешное удаление ресурса.
- 400 Bad Request: Ошибка клиента.
- 401 Unauthorized: Неавторизованный доступ.
- 404 Not Found: Ресурс не найден.
- 500 Internal Server Error: Внутренняя ошибка сервера.


Спецификация REST (Representational State Transfer) включает в себя ряд принципов и рекомендаций, которые направлены на создание удобных, масштабируемых и легко поддерживаемых веб-сервисов. Эти принципы помогут вам следовать RESTful архитектуре при разработке API.

[к оглавлению](#SOAP-REST)


# Основные правила спецификации REST


`1. Ресурсы и URI (Uniform Resource Identifier)`

- Идентификация ресурсов: Каждый ресурс должен иметь уникальный URI.
- Читабельность и логичность URI: URI должен быть понятным и описательным.
- Использование существительных: URI должен представлять ресурсы в виде существительных.
- Пример: http://example.com/api/clients/12345

`2. Методы HTTP`

- `GET:` Получение ресурса или коллекции ресурсов. Должен быть безопасным и идемпотентным (повторный вызов не изменяет состояние).
- Пример: GET /api/clients/12345
- `POST:` Создание нового ресурса. Не является идемпотентным.
- Пример: POST /api/clients
- `PUT:` Обновление существующего ресурса. Должен быть идемпотентным.
- Пример: PUT /api/clients/12345
- `DELETE:` Удаление ресурса. Должен быть идемпотентным.
- Пример: DELETE /api/clients/12345

`3. Статусные коды HTTP`

- 200 OK: Успешный запрос.
- 201 Created: Успешное создание ресурса.
- 204 No Content: Успешное удаление ресурса или обновление без контента в ответе.
- 400 Bad Request: Ошибка клиента (например, неверный синтаксис запроса).
- 401 Unauthorized: Неавторизованный доступ.
- 403 Forbidden: Доступ запрещен.
- 404 Not Found: Ресурс не найден.
- 500 Internal Server Error: Внутренняя ошибка сервера.

`4. Заголовки HTTP`

- Content-Type: Указывает тип данных в теле запроса или ответа (например, application/json).
- Accept: Указывает тип данных, которые клиент готов принять в ответе.
- Authorization: Используется для передачи аутентификационной информации.

`5. Форматы данных`

- JSON: Наиболее часто используемый формат для обмена данными.
- XML: Иногда используется, особенно в наследованных системах.
- Другие форматы: Возможны и другие форматы, такие как YAML или CSV, в зависимости от требований.

`6. Безсостоящность (Statelessness)`

- Каждое сообщение запроса должно содержать всю необходимую информацию для его обработки.
- Сервер не должен хранить состояние клиента между запросами.

`7. Кеширование (Caching)`

- Серверы и клиенты могут кешировать ответы для улучшения производительности.
- Использование заголовков кеширования (Cache-Control, ETag, Expires) для управления поведением кеша.

`8. Гипермедиа как движок состояния приложения (HATEOAS)`

- Ответы могут содержать гиперссылки, которые позволяют клиенту взаимодействовать с другими связанными ресурсами.
- Пример: в ответе на запрос клиента может быть ссылка на его заказы.

`9. Иерархическая структура ресурсов`

- Использование вложенных URI для представления иерархических отношений между ресурсами.
- Пример: http://example.com/api/clients/12345/documents


[к оглавлению](#SOAP-REST)

# Примеры спецификации RESTful API


### Получение данных о клиенте

```
Endpoint: GET /api/clients/{clientID}
Request:
http
Копировать код
GET /api/clients/12345 HTTP/1.1
Host: example.com
Accept: application/json
```

Response:

```json

{
   "id": "12345",
   "FullName": "Иванов Иван Иванович",
   "BirthDate": "1985-05-15",
   "Phone": "+79991234567",
   "Email": "ivanov@example.com",
   "Documents": [
      {
         "Type": "Паспорт",
         "Number": "1234567890",
         "Status": "Активен"
      }
   ],
   "ResidenceAddress": "ул. Примерная, д. 1, кв. 1",
   "RegistrationAddress": "ул. Регистрационная, д. 2, кв. 3"
}
```

### Добавление нового клиента

```
Endpoint: POST /api/clients
Request:
```

```http

POST /api/clients HTTP/1.1
Host: example.com
Content-Type: application/json
```

```json
{
   "FullName": "Петров Петр Петрович",
   "BirthDate": "1990-10-10",
   "Phone": "+79998887766",
   "Email": "petrov@example.com",
   "ResidenceAddress": "ул. Новая, д. 10, кв. 100",
   "RegistrationAddress": "ул. Регистрационная, д. 20, кв. 200"
}
```


### Response:


```http
HTTP/1.1 201 Created
Content-Type: application/json

```


```json
{
   "id": "67890",
   "FullName": "Петров Петр Петрович",
   "BirthDate": "1990-10-10",
   "Phone": "+79998887766",
   "Email": "petrov@example.com",
   "ResidenceAddress": "ул. Новая, д. 10, кв. 100",
   "RegistrationAddress": "ул. Регистрационная, д. 20, кв. 200"
}
````



### Заключение

Следуя этим принципам и рекомендациям, вы сможете разработать RESTful API, которое будет простым в использовании, масштабируемым и легким в поддержке. RESTful архитектура стала стандартом де-факто для разработки веб-сервисов благодаря своей простоте и гибкости.

[к оглавлению](#SOAP-REST)