Название
=========
Node.js обертка для драйвера торгового оборудования (ДТО) версии 10 от компании [АТОЛ](https://www.atol.ru/)

Функции
========
Реализованы следующие методы работы с драйвером
1. create() -  Инициализация драйвера 
1. destroy() - Деинициализация драйвера
1. getSettings() - Выгрузка настроек

Возвращает json-объект настроек, который затем можно передать в функцию setSettings
```json
{ AccessPassword: '',
  AutoDisableBluetooth: false,
  AutoEnableBluetooth: true,
  BaudRate: 115200,
  Bits: 8,
  ComFile: '1',
  IPAddress: '192.168.1.10',
  IPPort: 5555,
  LibraryPath: '',
  MACAddress: 'FF:FF:FF:FF:FF:FF',
  Model: 500,
  OfdChannel: 0,
  Parity: 0,
  Port: 0,
  StopBits: 0,
  UsbDevicePath: 'auto',
  UserPassword: '' }
```
1. setSettings(settings) - Настройка драйвера

Принимает _settings_ json-объект настроек полученных на предыдущем шаге и модифицированых по необходимости.
1. open() - Соединение с ККТ
1. close() - Завершение соединения с ККТ
1. processJson(task) - Выполнение JSON-задания

Здесь _task_ - json-объект описание задания для ККТ. Например, задание для открытия смены:
```json
{
    type: 'openShift',
    operator: {
       name: 'Иванов',
       vatin: '123654789507'
    }
}
```
Более подробную информацию по видам json-задании можно получить из документации к ДТО 10.
#### Обработка ошибок
При возникновении ошибки во время выполнения функций ДТО, она обрабытвается и выбрасывается Error c текстом ошибки, 
например, Error: Ошибка - 4 [ Порт недоступен ].

### Поддерживаемые платформы:
* Widows x86

Пример использования
========
Пример использования обертки можно посмотерть в файле index.js
