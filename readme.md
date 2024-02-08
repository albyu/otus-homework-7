### 1. Пользовательские сценарии

#### Регистрация нового клиента

Есть новый клиент
И есть интернет-магазин
И клиент переходит по ссылке "Зарегестрироваться"
Тогда загружается страница с формой регистрации нового клиента,
содержащая поля для заполнения:
1) имя клиента
2) пароль (маскированное)
3) e-mail 
4) номер телефона
и неактивную кнопку "зарегистрировать" 
Когда клиент заполняет форму
Тогда кнопка "зарегистрировать" становится активной
Когда клиент нажимает кнопку "зарегестрировать" 
Тогда клиент получает страницу с результатом регистрации


#### Создание заказа

Есть авторизованный клиент
И есть интернет-магазин
И клиент еще не выбрал ни одного товара 
И клиент вводит в строке поиска "Требуемый товар"
Тогда появляется список товаров, подходящих под
запрос клиента
И в карточке товара пользователь видит
 1) название
 2) цену
 3) изображение
 4) доступность в разных магазинах
Когда клиент нажимает на карточку товара
Тогда клиент переходит на страничку с описанием
товара и кнопкой "Добавить в корзину"
Когда клиент нажимает "Добавить в корзину"
Тогда создается новый заказ с одним товаром.


#### Добавление товара в заказ

Есть авторизованный клиент
И есть интернет-магазин
И клиент уже выбрал хотя бы один товар 
И клиент вводит в строке поиска "Требуемый товар"
Тогда появляется список товаров, подходящих под
запрос клиента
И в карточке товара пользователь видит
 1) название
 2) цену
 3) изображение
 4) доступность в разных магазинах
Когда клиент нажимает на карточку товара
Тогда клиент переходит на страничку с описанием
товара и кнопкой "Добавить в корзину"
Когда клиент нажимает "Добавить в корзину"
Тогда товар добавляется в корзину.
 

#### Удаление товара из заказа

Есть авторизованный клиент
И есть интернет-магазин
И клиент уже выбрал хотя бы один товар 
Когда клиент нажимает ссылку "Моя корзина"
Тогда ему отображается форма, содержащая:
 1) список товарных позиций в заказе. Каждая позиция содежит:
   1.1) описание товара
   1.2) цена товара
   1.3) количество товара в заказе
   1.4) общая стоимость товарной позиции
   1.5) опцию "удалить товар из корзины"
 2) общую стоимость заказа
 3) кнопку "Оформить заказ"
Когда клиент выбирает опцию "удалить товар из корзины" для одной из товарных позиций
Тогда появляется окно подтверждения
Когда клиент подтверждает удаление
Тогда отображается корзина без удаленного товара 


#### Оформление заказа

Есть авторизованный клиент
И есть интернет-магазин
И клиент уже выбрал хотя бы один товар 
Когда клиент нажимает ссылку "Моя корзина"
Тогда ему отображается форма, содержащая:
 1) список товарных позиций в заказе. Каждая позиция содежит:
   1.1) описание товара
   1.2) цена товара
   1.3) количество товара в заказе
   1.4) общая стоимость товарной позиции
   1.5) опцию "удалить товар из корзины"
 2) общую стоимость заказа
 3) кнопку "Оформить заказ"
Когда клиент нажимает кнопку "Оформить заказ"
Тогда открывается форма с выбором способа доставки, содержащая опции:
 1) доставка курьером
 2) забрать товар на пункте выдачи
Когда и если клиент выбирает опцию "Забрать товар на пункте выдачи"
  Тогда активируется раздел, позволяющий выбрать пункт выдачи из списка 
  Когда клиент выбирает требуемый пункт выдачи из списка
  Тогда активируется кнопка "Оплатить заказ"
Когда и если клиент выбирает опцию "Доставка курьером"
  Тогда активируется раздел с формой, позволяющей:
    1) ввести адрес доставки
    2) выбрать курьерскую компанию 
  Когда клиент вводит адрес доставки
  И клиент выбирает курьерскую компанию
  Тогда визуализируется стоимость доставки и чек-бокс "подтвердить стоимость доставки"
  Когда клиент отмечает чек-бокс "подтвердить стоимость доставки"
  Тогда активируется кнопка "Оплатить заказ"


#### Оплата заказа

Есть авторизованный клиент
И есть интернет-магазин
И клиент находится в конце сценария "Оформление заказа" или "Оформление подарочной карты"
Когда клиент нажимает нажимает кнопку "Оплатить заказ"
Тогда появляется форма "Выбор способа оплаты" с опциями:
  1) банковской картой 
    1.1) со списком привязанных карт клиента 
    1.2) опцией "другая карта"
  2) через систему быстрых платежей
  3) из кошелька клиента с информацией о балансе кошелька
  4) подарочной картой
    4.1) со списком активированных подарочных карт клиента
    4.2) опцией "новая подарочная карта"
Когда и если клиент выбирает опцию оплаты "банковской картой" (новой или привязанной)
  Тогда начинается сценарий "Оплата заказа банковской картой" (* здесь его не расписываем, поскольку он определяется банковским API)
  Когда сценарий "Оплата заказа банковской картой" успешно пройден
  Тогда активируется кнопка "Оплатить" 
Когда и если клиент выбирает опцию оплаты "через систему быстрых платежей"
  Тогда начинается сценарий "Оплата заказа через СБП" (* здесь его не расписываем, поскольку он определяется банковским API) 
  Когда сценарий "Оплата заказа через СБП" успешно пройден
  Тогда активируется кнопка "Оплатить" 
Когда и если клиент выбирает опцию оплаты "из кошелька клиента"
  И баланс кошелька достаточен для оплаты заказа
  Тогда активируется кнопка "Оплатить"
Когда и если клиент выбирает опцию оплаты "подарочной картой" 
И выбирает одну из активированных подарочных карт
  И баланс подарочной карты достаточен для оплаты заказа
  Тогда активируется кнопка "Оплатить"
Когда и если клиент выбирает опцию оплаты "подарочной картой" 
И выбирает опцию "Новая подарочная карта"
  Тогда начинается сценарий "Активация подарочной карты"
  Когда сценарий "Оплата заказа через СБП" успешно пройден
  Тогда активируется кнопка "Оплатить" 
Когда клиент нажимает кнопку "Оплатить"
Тогда отображается результат оплаты заказа
И на почту клиента отправляется письмо, содержащее результат оплаты
Если оплата заказа удачна
  Тогда отображается состав заказа с отметкой "Оплачено"
Если оплата заказа неудачна
Тогда отображается описание возникшей ошибки и предлагаются опции:
  1) Вернуться к редактированию заказа (сценарий "Удаление товара из корзины")
  2) Попробовать оплатить еще раз (возврат на "Выбор способа оплаты")

  
#### Оформление подарочной карты

Есть авторизованный клиент
И есть интернет-магазин
И клиент переходит по ссылке "Купить подарочную карту"
Тогда загружается страница с формой созданиея подарочной карты, содержащая поля для заполнения:
  1) имя одаряемого
  3) e-mail 
  4) сумма на карте
  5) дизайн открытки
и неактивную кнопку "Оплатить" 
Когда клиент заполняет форму
Тогда кнопка "Оплатить" становится активной
Когда клиент нажимает кнопку "Оплатить" 
Тогда начинается выполнение сценария "Оплата заказа"
Когда сценарий "Оплата заказа" успешно пройден
Тогда на выбранный клиентом адрес отправляется письмо, содержащее код активации подарочной карты
И на форме отображается:
   1) информация об успешном завершении операции
   2) ссылка-приглашение перейти к каталогу товаров


#### Активация подарочной карты

Есть авторизованный клиент
И есть интернет-магазин
И клиент переходит по ссылке "Активировать подарочную карту"
Тогда отображается окно активации подарочной карты, соержащее:
   1) поле для ввода кода активации
   2) кнопку "активировать"
Когда клиент ввел код активации 
И нажал кнопку "активировать"
Тогда на форме отображается 
   1) баланс активированной карты
   2) ссылка-приглашение перейти к каталогу товаров


#### Пополнение кошелька

Есть авторизованный клиент
И есть интернет-магазин
И клиент переходит по ссылке "Личный кабинет"
Тогда отображается окно, содержащее
   1) учетные данные клиента
   2) баланс его кошелька   
   3) поле ввода для суммы пополнения
   3) кнопку "Пополнить баланс кошелька"   
Когда клиент заполняет поле "сумма пополнения"
И клиент нажимает на кнопку "Пополнить баланс кошелька"
Тогда начинается выполнение сценария "Оплата заказа"
Когда сценарий "Оплата заказа" успешно пройден
Тогда на форме отображается:
   1) обновленный баланс кошелька
   2) ссылка-приглашение перейти к каталогу товаров


### 2. Общая схема взаимодействия сервисов.

### 3. Назначение сервисов и их зона ответственности.

#### auth (аутентификация и авторизация)

- хранит пользовательские данные: clientId, локальный пароль (если клиент использует (ашлокальную аутентификацию), средства коммуникации (телефон, e-mail)
- регистрирует нового клиента;
- создает задание на открытие нового кошелька (в billing) и учетной записи сервиса уведомлений (notification)
- аутентифицирует клиента через технологию "единого входа" (если клиент регистрируется через внешний сервис аутентификации, 
то играет роль resource service, в любом случае выполняется поиск учетной записи клиента в локальной БД сервиса);
- авторизует сессию клиента по запросу от других сервисов, передает им необходимые атрибуты клиента.

#### billing (локальный биллинг)

- хранит балансы клиентских кошельков и подарочных карт;
- заводит новые клиентские кошельки при регистрации клиента;
- добавляет новые (неавторизованные) подарочные карты по запросу от payment;
- выполняет пополнение клиентских кошельков по запросу от payment;
- выполняет списание суммы заказа во время процесса оплаты.

#### delivery (CRM доставки)

- ведет учет слотов собственной доставки;
- выполняет предварительное резервирование слота доставки по запросу клиента, в том числе внешними службами доставки.
- после прихода запроса от orchestra бронирует товар и создает кейс доставки (до пункта выдачи или до дома);
- управляет кейсом доставки;
- уведомляет клиента о доставке товара в пункт выдачи (или о предстоящей доставке на адрес)

#### notification (сервис доставки уведомлений клиентам)

- заводит новые клиентские учетные записи с привязкой к ним каналов доставки (почта, SMS, push);
- отправляет через зарегистрированные каналы уведомления о совершенных действиях  

#### orchestra (оркестратор согласования заказа)

- согласует готовые (укомплектованные, оплаченные и одобренные пользователем) заказы:
  - подтверждает факт и сумму платежа в payment;
  - подтверждает наличие товара в store и создает кейс на комплетование заказа в store;
  - создает кейс на доставку заказа до пункта выдачи в delivery;
  - (опционально) подтвержает наличие свободного слота доставки по указанному пользователем адресу;
- отправляет информацию об итоге обработки в сервис нотификации.

#### order (сервис управления заказом)

- по запросу пользователя создает и комплектует заказ;
- по запросу пользователя отменяет заказ;
- формирует заказ на покупку подарочной карты;
- передает заказ в обработку orchestra; 
- получает и сохраняет финальный статус заказа от orchestra


#### payment (сервис совершения платежей)

- управляет сохраненными средствами платежа клиента (банковские карты, подарочные карты);
- выполняет привязку подарочных карт к клиенту по запросу клиента;
- по запросу от клиента формирует списание с банковского счета клиента (через bank-api) для:
  - оплаты заказа;
  - пополнения кошелька клиента;
- по запросу от клиента формирует списание c кошелька или подарочной карты клиента (через billing);
- по запросу от orchestra выполняет отмену совершенного платежа (в рамках отката распределенной транзакции)
- формирует запросы на уведомление для notification;

#### store (сервис учета товаров на складе)

- ведет учет товаров на складах;
- предварительно бронирует товары по запросу клиента;
- после прихода запроса от orchestra бронирует товар и создает кейс на комплектацию заказа
- управляет кейсом комплектации заказа

### web-front (пользовательcкое приложение)

реализует все пользовательские сценарии, взаимодействует:
- auth, клиент: 
         -- регистрируется как новый клиент; 
         -- аутентификацию и авторизацию клиента в системе
         -- корректирует данные в личном кабинете

- delivery, клиент: 
         -- получает данные о пунктах выдачи  
         -- предоставляет данные для доставки (название пункта выдачи или адрес) и предварительно бронирует слот (в том числе, через внешние службы доставки) - создает кейс доставки 

- order, клиент:
        -- создает новый заказ 
        -- изменяет заказ 
        -- подтверждает (или отменяет) заказ
        -- просматривает текущий статус заказа

- payment: клиент выбирает средство платежа, создает новое средство платежа, выполняет запрос на привязку подарочной карты,
           выполняет оплату или пополнение через выбранное средство платежа

- store: клиент:
        -- получает актуальные сведения о наличии товара на складе
        -- выполняет предварительное резервирование товара на складе (создает кейс на комплектацию)


### 4. Контракты взаимодействия сервисов друг с другом.

#### auth (аутентификация и авторизация)

##### POST /login: запрос на вход в систему 

```
request: 
  headers:
    cookies: 
      oldSessionId:
        type: string 
        desc: текущий идентификатор сессии клиента
  body:
    model:
      username:
        type: string
        desc: идентификатор пользователя
      password:
        type: string
        desc: пароль пользователя
    example-value:
response:  
- respCode: 200/Success
    body:
      model:
        username:
          type: string
          desc: идентификатор пользователя
        fistName:
          type: string
          desc: имя пользователя
        lastName:
          type: string
          desc: фамилия пользователя
        email:
          type: string
          desc: email пользователя
	phone:
          type: string
          desc: номер телефона пользователя
- respCode: 400/Username and password should be provided
    body:
     errorMessage:
       type: string
       desc: описание ошибки 
- respCode: 401/Invalid login/password
    body:
     errorMessage:
       type: string
       desc: описание ошибки 
- respCode: 404/Not Found
    body:
     errorMessage:
       type: string
       desc: описание ошибки 
```

```
Example Request Value
{
  "password": "string",
  "username": "string"
}
```

```
Example Response Value
{
  "email": "string",
  "firstName": "string",
  "lastName": "string",
  "phone": "string",
  "username": "string"
}
``` 
  

##### POST /register: Зарегистрировать нового клиента

```
request: 
  body:
    model:
      username:
        type: string
        desc: идентификатор пользователя
      fistName:
        type: string
        desc: имя пользователя
      lastName:
        type: string
        desc: фамилия пользователя
      email:
        type: string
        desc: email пользователя
      phone:
        type: string
        desc: номер телефона пользователя
      password:
        type: string
        desc: пароль пользователя   
response:  
- respCode: 200/Success
    body:
      model:
       username:
         type: string
         desc: идентификатор пользователя
       fistName:
         type: string
         desc: имя пользователя
       lastName:
         type: string
         desc: фамилия пользователя
       email:
         type: string
         desc: email пользователя
       phone:
         type: string
         desc: номер телефона пользователя 
- respCode: 400/Username, password, email should be provided
    body:
     errorMessage:
       type: string
       desc: описание ошибки 
- respCode: 409/User already exists
    body:
     errorMessage:
       type: string
       desc: описание ошибки 
```

```
Example Request Value
{
  {
  "email": "string",
  "firstName": "string",
  "lastName": "string",
  "phone": "string",
  "username": "string",
  "password": "qwerty1234"

}
```

```
Example Response Value
{
  "email": "string",
  "firstName": "string",
  "lastName": "string",
  "phone": "string",
  "username": "string"
}
``` 

##### GET /logout: Завершение пользовательской сессии

```
request: 
  headers:
    cookies: 
      sessionId:
        type: string 
        desc: идентификатор сессии клиента
response:
- respCode: 200/Success
  headers:
    cookies: 
      sessionId:
        type: string 
        desc: пустой идентификатор сессии клиента
        value: "" 
```


##### GET /auth: запрос на подтвеждение авторизации

```
request: 
  headers:
    cookies: 
      sessionId:
        type: string 
        desc: идентификатор сессии клиента

response:  
- respCode: 200/Success
    body:
      model:
        username:
          type: string
          desc: идентификатор пользователя
        fistName:
          type: string
          desc: имя пользователя
        lastName:
          type: string
          desc: фамилия пользователя
- respCode: 401/User not authorized
- respCode: 403/Forbidden
- respCode: 404/Not Found

```
   
```
Response Example Value
Model
{
  "email": "string",
  "firstName": "string",
  "lastName": "string",
  "phone": "string",
  "username": "string"
}
``` 

##### Поток запросов через Message Broker на создание требуемых сущностей (от auth к billing, payment и notification) 

Format 1 на компонентной схеме

```
format: JSON
messageBody:
  username:
    type: string
    spec: Идентификатор клиента  
  firstName:
     type: string
     desc: имя пользователя
   lastName:
     type: string
     desc: фамилия пользователя
   email:
     type: string
     desc: email пользователя
   phone:
     type: string
     desc: номер телефона пользователя
``` 


```
Message example

{
  "username": "string",
  "firstName": "string",
  "lastName": "string",
  "email": "string",
  "phone": "string"  
}

```

#### billing (локальный биллинг)

##### GET /token/get: Получить сведения о средстве оплаты (кошельке, подарочной карте) 

```
request: 
  parameters:
    username:
      type: string
      desc: id клиента
response:
- respCode: 200/Success
    body:
      model:
        username:
          type: string
          desc: id клиента        
        tokens:
          type: array
          desc: Список средств платежа
          id:
            type: long
            spec: ид средства платежа (в payment)           
          tokenType:
            type: string
            spec: Тип средства оплаты (BANK_CARD/QR_PAY/GIFT_CARD/WALLET)
          maskedTokenId:
            type: string
            spec: Маскированный ид средства платежа (номер карты) 
          description:
            type: string
            spec: Описание            
- respCode: 401/Not authorized
- respCode: 404/Client not found
```

```
Response Example Value

{
  "username": "string",
  "tokens": [ 
    {
      "tokenType": "string",
      "maskedTokenId": "string",
      "description": "string"
    }
  ]
}
``` 


##### POST /token/charge: Провести операцию по счету

##### POST /trxn/get: Получить список операций по счету 

##### POST /token/create: Сгенерировать новую подарочную карту



#### delivery (CRM доставки)

##### GET /points: Получить список точек доставки

```
request: 
  parameters:
    addressFilter:
      type: string
      desc: фильтр по адресу
response:
- respCode: 200/Success
    body:
      model:
        pickupPoints:
          type: array
          desc: список точек доставки          
          id:
            type: int
            desc: идентификатор точки
          name:
            type: string
            desc: название точки
          address:
            type: string
            desc: адрес точки

- respCode: 401/Not authorized
```

```
Example Response Value
{
  "pickupPoints": [
    {
        "id": 1,
        "name": "string",
        "address": "string"
    }
  ]
}
```

##### GET /variants: Получить варианты доставки по указанному адресу

```
request: 
  parameters:
    address:
      type: string
      desc: требуемый адрес доставки
response:
- respCode: 200/Success
    body:
      model:
        address:
          type: string
          desc: адрес доставки
        variants:
          type: array
          desc: список вариантов доставки
          companyName:
            type: string
            desc: имя компании
          cost:
            type: double
            desc: адрес точки
          estimatedDate:
            type: date
            desc: оценочное время доставки
- respCode: 401/Not authorized
```

```
Example Response Value
{
  "address": "string",
  "variants": [
    {
        "companyName": 1,
        "cost": 16.96,
        "estimatedDate": "dd.mm.yyyy"
    }
  ]
}
```


#### notification (сервис доставки уведомлений клиентам)

##### Поток запросов через Message Broker на уведомления о подтверждении/ошибке подтверждения заказа (от orchestra)

Format 2 на компонентной схеме

```
format: JSON
messageBody:
  orderId: 
    type: string
    spec: Идентификатор заказа
  username:
    type: string
    spec: Идентификатор клиента
  response:
    type: string
    spec: Результат обработки совершенного заказа (SUCCESS/FAIL)
  timestamp:
    type: timestamp
    spec: время окончания обработки  
``` 

```
Message example
{
  "orderId": "string",
  "username": "string",
  "response": "SUCCESS",
  "timestamp": "timestamp",
}

```

##### Поток запросов через Message Broker на уведомления о совершении платежа/отмене платежа (от payment)

Format 3 на компонентной схеме

```
format: JSON
messageBody:
  orderId: 
    type: string
    spec: Идентификатор заказа
  username:
    type: string
    spec: Идентификатор клиента  
  requestType:
    type: string
    spec: Тип запроса (CHARGE/REVERSE)
  tokenType:
    type: string
    spec: Тип средства оплаты (BANK_CARD/QR_PAY/GIFT_CARD/WALLET)
  maskedTokenId:
    type: string
    spec: Маскированный ид средства платежа 
  response:
    type: string
    spec: Результат обработки совершенного заказа (SUCCESS/FAIL)
  errorMsg:
    type: string
    spec: Сведения об ошибке     
  timestamp:
    type: timestamp
    spec: время (попытки) оплаты  
``` 

```
Message example
{
  "orderId": "string",
  "username": "string",
  "requestType": "CHARGE"
  "tokenType": "BANK_CARD",
  "maskedTokenId": "string",
  "response": "SUCCESS",
  "errorMsg": "string",
  "timestamp": "timestamp"

}

```



##### Поток запросов через Message Broker на уведомление о доставке (от delivery)

Format 4 на компонентной схеме

```
format: JSON
messageBody:
  orderId: 
    type: string
    spec: Идентификатор заказа
  username:
    type: string
    spec: Идентификатор клиента  
  pickupPointDelivery:
    type: object
    spec: Описание получения заказа в точке выдачи
    pointId:
      type: int 
      spec: Идентификатор точки выдачи заказа
    address: 
      type: string
      spec: Адрес точки выдачи заказа 	 
    deliveryDate:
      type: date
      spec: Дата доступности заказа
  homeDelivery:
    type: object
    spec: Описание получения доставки заказа на дом 
    homeAddress: 
      type: string
      spec: Адрес точки выдачи заказа 	
    deliveryDate:
      type: date
      spec: Дата доставки  
    timeSlot:
      type: object
      spec: временной слот доставки
      beginTime:
        type: time
        spec: начало слота
      endTime:
        type: time
        spec: окончание слота     
  timestamp:
    type: timestamp
    spec: время (попытки) оплаты  
``` 

```
Message example
{
  "orderId": "string",
  "username": "string",
  "pickupPointDelivery": {
    "pointId": 120,
    "address": "string",
    "deliveryDate": "dd.mm.yyyy"
  }
  "homeDelivery": {
    "homeAddress: "string",
    "deliveryDate: "dd.mm.yyyy",
    "timeSlot": {
      "beginTime": "13:00",
      "endTime": "15:00"
    }
  }
  "timestamp": "timestamp"
}

```


##### Поток запросов через Message Broker на доставку данных подарочной карты (от billing)      

Format 5 на компонентной схеме

```
format: JSON
messageBody:
  giftCardNumber
    type: string
    spec: номер подарочной карты  
  granteeFirstName:
    type: string
    desc: имя получателя карты
  granteeLastName:
    type: string
    desc: фамилия получателя карты
  granteeEmail:
    type: string
    desc: email получателя карты
``` 

```
Message example:
{
  "giftCardNumber": "string",
  "granteeFirstName": "string",
  "granteeLastName": "string",
  "granteeEmail": "string"
}
```

#### orchestra (оркестратор согласования заказа)

##### Поток заказов, требующих подтверждения, от order к orchestra

Format 6 на компонентной схеме

```
format: JSON
messageBody:
  orderId: 
    type: string
    spec: Идентификатор заказа
  version:
    type: int
    spec: Версия объекта
  userName:
    type: string
    spec: идентификатор клиента
  orderItems:
    type: array
    desc: товарные позиции заказа 
    - id:
        type: int
        desc: идентификатор товарной позиции
      productId:
        type: int
        desc: идентификатор товара
      productName:
        type: string
        desc: название товара  
      quantity:
        type: int
        desc: количество товарных единиц в заказе     
```

```
Message Example:
{
  "orderId": "string",
  "requestType": "CONFIRM",
  "confirmator": "PAYMENT",
  "orderItems": [
    {
      "id": 1,
      "productId": 2
      "productName": "string",
      "productPrice": 20.20      
      "quantity": 0
    }
  ]
}
```



##### Поток ответов на запросы подьверждений, от orchestra к order

Format 7 на компонентной схеме

```
format: JSON
messageBody:
  orderId: 
    type: string
    spec: Идентификатор заказа
  version:
    type: int
    spec: Версия объекта
  response:
    type: string
    spec: Результат выполнения (SUCCESS/FAIL)
```

```
Message Example:
{
  "orderId": "string",
  "requestType": "CONFIRM",
  "confirmator": "PAYMENT",
  "orderItems": [
    {
      "id": 1,
      "productId": 2
      "productName": "string",
      "productPrice": 20.20      
      "quantity": 0
    }
  ]
}
```


##### Поток запросов через Message Broker на подтверждения от orchestra к payment, store, delivery

Format 8 на компонентной схеме

```
format: JSON
messageBody:
  orderId: 
    type: string
    spec: Идентификатор заказа
  requestType:
    type: string
    spec: Тип запрашиваемой операции CONFIRM (подтверждение)/REVERSE(отмена)
  confirmator:
    type: string
    spec: Код системы, у которой запрашиваем подтверждение (PAYMENT/STORE/DELIVERY)
  orderItems:
    type: array
    desc: товарные позиции заказа 
    - id:
        type: int
        desc: идентификатор товарной позиции
      productId:
        type: int
        desc: идентификатор товара
      productName:
        type: string
        desc: название товара  
      quantity:
        type: int
        desc: количество товарных единиц в заказе     
```

```
Message Example:
{
  "orderId": "string",
  "requestType": "CONFIRM",
  "confirmator": "PAYMENT",
  "orderItems": [
    {
      "id": 1,
      "productId": 2
      "productName": "string",
      "productPrice": 20.20      
      "quantity": 0
    }
  ]
}
```


##### Поток ответов на запросы подтверждений от payment, store, delivery к orchestra

Format 9 на компонентной схеме

```
format: JSON
messageBody:
  orderId: 
    type: string
    spec: Идентификатор заказа
  requestType:
    type: string
    spec: Тип запрашиваемой операции CONFIRM (подтверждение)/REVERSE(отмена)
  confirmator:
    type: string
    spec: Код системы, у которой запрашиваем подтверждение (PAYMENT/STORE/DELIVERY)
  response:
    type: string
    spec: Результат выполнения (SUCCESS/FAIL)

```

```
Message Example:

{
  "orderId": "string",
  "requestType": "CONFIRM",
  "confirmator": "PAYMENT",
  "response": "SUCCESS"
}
```

##### Поток запросов через Message Broker на открытие подарочной карты от orchestra к billing

Format 10 на компонентной схеме

```
format: JSON
messageBody:
  orderId: 
    type: string
    spec: Идентификатор заказа
  requestType:
    type: string
    spec: Тип запрашиваемой операции OPEN(открыть)/CLOSE(закрыть)
  cards:
    type: array
    desc: список подарочных карт
    - id:
        type: int
        desc: идентификатор карты в списке
      balance:
        type: double
        desc: баланс подарочной карты
      grantee:
        type: object
        desc: сведения об одаряемом
        firstName:
          type: string
          desc: имя получателя карты
        lastName:
          type: string
          desc: фамилия получателя карты
        email:
          type: string
          desc: email получателя карты         
```

```
Message Example:
{
  "orderId": "string",
  "requestType": "OPEN",
  "cards": [
    {
      "id": 1,
      "balance": 2,
      "grantee": 
       {
        "firsName": "string",      
        "lastName": "string",
        "email": "string"
    }
  ]
}
```
##### Поток запросов через Message Broker c результатами открытия подарочной карты от orchestra к billing

Format 11 на компонентной схеме

```
format: JSON
messageBody:
  orderId: 
    type: string
    spec: Идентификатор заказа
  requestType:
    type: string
    spec: Тип запрошенной операции OPEN(открыть)/CLOSE(закрыть)
  response:
    type: string
    spec: Результат выполнения (SUCCESS/FAIL)

```

```
Message Example:
{
  "orderId": "string",
  "requestType": "OPEN",
  "response": "SUCCESS"
}
```


#### order (сервис управления заказом)

##### POST /place Создание заказа

```
request: 
  headers:
    cookies: 
      sessionId:
        type: string 
        desc: идентификатор сессии клиента
  body:
    model:
      id:
        type: string
        desc: идентификатор заказа
      orderItems:
        type: array
        desc: товарные позиции заказа 
        - product:
            id:
              type: int
              desc: идентификатор товара
          quantity:
            type: int
            desc: количество товарных единиц в заказе
response:
- respCode: 200/Success
    body:
      model:
        id:
          type: string
          desc: идентификатор заказа
        status: 
          type: string
          desc: статус заказа
        version:
          type: int
          desc: версия объекта
        orderItems:
          type: array
          desc: товарные позиции заказа 
          - id:
              type: int
              desc: идентификатор товарной позиции
            product:
              id:
                type: int
                desc: идентификатор товара
              name:
                type: string
                desc: наименование товара
              price:
                type: double
                desc: цена товара
            quantity:
              type: int
              desc: количество товарных единиц в заказе
- respCode: 401/Not authorized
- respCode: 404/Product not found
    body:
     errorMessage:
       type: string
       desc: описание ошибки 
- respCode: 409/Inappropriate state of object for performing operation
    body:
     errorMessage:
       type: string
       desc: описание ошибки 
- respCode: 500/Authentication Server error
    body:
     errorMessage:
       type: string
       desc: описание ошибки 
```

```
Example Request Value
{
  "id": "string",
  "orderItems": [
    {
      "id": 1,
      "product": {
        "id": 1,
      },
      "quantity": 1
    }
  ]
}
```

```
Example Response Value
{
  "id": "string",
  "status": "NEW",
  "version": 0
  "orderItems": [
    {
      "id": 0,
      "product": {
        "id": 0,
        "name": "string",
        "price": 0
      },
      "quantity": 0
    }
  ]
}
```


##### PUT /adjust Изменение заказа

```
request: 
  headers:
    cookies: 
      sessionId:
        type: string 
        desc: идентификатор сессии клиента
  body:
    model:
      id:
        type: string
        desc: идентификатор заказа
      version:
        type: id
        desc: идентификатор версии
      orderItems:
        type: array
        desc: товарные позиции заказа 
        - product:
            id:
              type: int
              desc: идентификатор товара
          quantity:
            type: int
            desc: количество товарных единиц в заказе
response:
- respCode: 200/Success
    body:
      model:
        id:
          type: string
          desc: идентификатор заказа
        status: 
          type: string
          desc: статус заказа
        version:
          type: int
          desc: версия объекта
        orderItems:
          type: array
          desc: товарные позиции заказа 
          - id:
              type: int
              desc: идентификатор товарной позиции
            product:
              id:
                type: int
                desc: идентификатор товара
              name:
                type: string
                desc: наименование товара
              price:
                type: double
                desc: цена товара
            quantity:
              type: int
              desc: количество товарных единиц в заказе
- respCode: 401/Not authorized
- respCode: 404/Order not found
    body:
	     errorMessage:
       type: string
       desc: описание ошибки 
- respCode: 404/Product not found
    body:
     errorMessage:
       type: string
       desc: описание ошибки 
- respCode: 409/Inappropriate state of object for performing operation
    body:
     errorMessage:
       type: string
       desc: описание ошибки 
- respCode: 500/Authentication Server error
    body:
     errorMessage:
       type: string
       desc: описание ошибки 

```

```
Example Request Value
{
  "id": "string",
  "status": "NEW",
  "version": 1
  "orderItems": [
    {
      "id": 2,
      "product": {
        "id": 2,
      },
      "quantity": 3
    }
  ]
}
```

```
Example Response Value
{
  "id": "string",
  "status": "NEW",
  "version": 1
  "orderItems": [
    {
      "id": 2,
      "product": {
        "id": 2,
        "name": "string",
        "price": 0.98
      },
      "quantity": 1
    }
  ]
}
```


##### PUT /cancel Отмена заказа

```
request: 
  headers:
    cookies: 
      sessionId:
        type: string 
        desc: идентификатор сессии клиента
  body:
    model:
      id:
        type: string
        desc: идентификатор заказа
      version:
        type: id
        desc: идентификатор версии
      orderItems:
        type: array
        desc: товарные позиции заказа 
        - product:
            id:
              type: int
              desc: идентификатор товара
          quantity:
            type: int
            desc: количество товарных единиц в заказе
response:
- respCode: 200/Success
    body:
      model:
        id:
          type: string
          desc: идентификатор заказа
        status: 
          type: string
          desc: статус заказа
        version:
          type: int
          desc: версия объекта
        orderItems:
          type: array
          desc: товарные позиции заказа 
          - id:
              type: int
              desc: идентификатор товарной позиции
            product:
              id:
                type: int
                desc: идентификатор товара
              name:
                type: string
                desc: наименование товара
              price:
                type: double
                desc: цена товара
            quantity:
              type: int
              desc: количество товарных единиц в заказе
- respCode: 401/Not authorized
- respCode: 404/Order not found
    body:
     errorMessage:
       type: string
       desc: описание ошибки 
- respCode: 409/Inappropriate state of object for performing operation
    body:
     errorMessage:
       type: string
       desc: описание ошибки 
- respCode: 500/Authentication Server error
    body:
     errorMessage:
       type: string
       desc: описание ошибки 

```


```
Example Request Value
{
  "id": "string",
  "status": "NEW",
  "version": 0
  "orderItems": [
    {
      "id": 1,
      "product": {
        "id": 1,
        "name": "string",
        "price": 0.23
      },
      "quantity": 1
    }
  ]
}
```


```
Example Response Value
{
  "id": "string",
  "status": "CANCELED",
  "version": 0
  "orderItems": [
    {
      "id": 1,
      "product": {
        "id": 1,
        "name": "string",
        "price": 0.23
      },
      "quantity": 1
    }
  ]
}
```


##### PUT /process Передача заказа в обработку

```
request: 
  headers:
    cookies: 
      sessionId:
        type: string 
        desc: идентификатор сессии клиента
  body:
    model:
      id:
        type: string
        desc: идентификатор заказа
      version:
        type: id
        desc: идентификатор версии
      orderItems:
        type: array
        desc: товарные позиции заказа 
        - product:
            id:
              type: int
              desc: идентификатор товара
          quantity:
            type: int
            desc: количество товарных единиц в заказе
response:
- respCode: 200/Success
    body:
      model:
        id:
          type: string
          desc: идентификатор заказа
        status: 
          type: string
          desc: статус заказа
        version:
          type: int
          desc: версия объекта
        orderItems:
          type: array
          desc: товарные позиции заказа 
          - id:
              type: int
              desc: идентификатор товарной позиции
            product:
              id:
                type: int
                desc: идентификатор товара
              name:
                type: string
                desc: наименование товара
              price:
                type: double
                desc: цена товара
            quantity:
              type: int
              desc: количество товарных единиц в заказе
- respCode: 401/Not authorized
- respCode: 404/Order not found
    body:
     errorMessage:
       type: string
       desc: описание ошибки 
- respCode: 409/Inappropriate state of object for performing operation
    body:
     errorMessage:
       type: string
       desc: описание ошибки 
- respCode: 500/Authentication Server error
    body:
     errorMessage:
       type: string
       desc: описание ошибки 

```

```
Example Request Value
{
  "id": "string",
  "status": "NEW",
  "version": 2
  "orderItems": [
    {
      "id": 1,
      "product": {
        "id": 0,
        "name": "string",
        "price": 0.23
      },
      "quantity": 1
    }
  ]
}
```


```
Example Response Value
{
  "id": "string",
  "status": "IN_PROGRESS",
  "version": 3
  "orderItems": [
    {
      "id": 1,
      "product": {
        "id": 1,
        "name": "string",
        "price": 0.23
      },
      "quantity": 1
    }
  ]
}
```


##### GET /get Получить текущее состояние заказа

```
request: 
  headers:
    cookies: 
      sessionId:
        type: string 
        desc: идентификатор сессии клиента
  parameters:
    orderId:
      type: string
      desc: id интересующего заказа
response:
- respCode: 200/Success
    body:
      model:
        id:
          type: string
          desc: идентификатор заказа
        status: 
          type: string
          desc: статус заказа
        version:
          type: int
          desc: версия объекта
        orderItems:
          type: array
          desc: товарные позиции заказа 
          - id:
              type: int
              desc: идентификатор товарной позиции
            product:
              id:
                type: int
                desc: идентификатор товара
              name:
                type: string
                desc: наименование товара
              price:
                type: double
                desc: цена товара
            quantity:
              type: int
              desc: количество товарных единиц в заказе
- respCode: 401/Not authorized
- respCode: 404/Order not Found
```

```
Example Response Value
{
  "id": "string",
  "status": "COMPLETED",
  "version": 0
  "orderItems": [
    {
      "id": 0,
      "product": {
        "id": 0,
        "name": "string",
        "price": 0
      },
      "quantity": 0
    }
  ]
}
```

#### payment (сервис учета товаров на складе)

#### payment (сервис совершения платежей)

- управляет сохраненными средствами платежа клиента (банковские карты, подарочные карты);
- выполняет привязку подарочных карт к клиенту по запросу клиента;
- по запросу от клиента формирует списание с банковского счета клиента (через bank-api) для:
  - оплаты заказа;
  - пополнения кошелька клиента;
- по запросу от клиента формирует списание c кошелька или подарочной карты клиента (через billing);
- по запросу от orchestra выполняет отмену совершенного платежа (в рамках отката распределенной транзакции)
- формирует запросы на уведомление для notification;

##### GET /tokens/get Получение списка средств платежа клиента

##### POST /tokens/add Добавление средства платежа

##### DELETE /tokens/delete Удаление средства платежа

##### POST /pay Выполнение платежа

##### POST /activate Активация подарочной карты 


#### store (сервис учета товаров на складе)

##### GET /get Получение количества единиц товара на складах

```
request: 
  parameters:
    productId:
      type: int
      desc: идентификатор интересующего продукта
response:
- respCode: 200/Success
    body:
      model:
        productId:
          type: int
          desc: идентификатор продукта
        productPlaces:
          type: array
          desc: количества товара на каждом из складов
          - store:
              type: object
              desc: описание склада              
              id:
                type: int
                desc: идентификатор склада
              name:
                type: string
                desc: название склада
              address:
                type: string
                desc: адрес склада
            quantity:
              type: int
              desc: количество товара на складе
- respCode: 401/Not authorized
- respCode: 404/Product not Found

```

```
Example Response Value
{
  "productId": "string",
  "productPlaces": [
    {
      "store": {
        "id": 1,
        "name": "string",
        "address": "string"
      },
      "quantity": 2
    }
  ]
}

```




