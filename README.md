# UserInfoApp

## Описание программы

`UserInfoApp` — это консольная программа на Java, которая запрашивает у пользователя информацию в следующем формате:
```
Фамилия Имя Отчество ДатаРождения НомерТелефона Пол
```

Программа проверяет корректность введённых данных и сохраняет их в файл с именем, совпадающим с фамилией пользователя. В случае ошибок (например, неверный формат даты или номера телефона), программа выбрасывает соответствующие исключения и сообщает пользователю об ошибке.

### Формат данных:

- **Фамилия**, **Имя**, **Отчество** — строки.
- **Дата рождения** — строка формата `dd.MM.yyyy`.
- **Номер телефона** — целое беззнаковое число (без пробелов и символов форматирования).
- **Пол** — символ `f` (женский) или `m` (мужской).

### Программа выполняет следующие шаги:

1. Проверяет количество введённых данных. Если их больше или меньше шести, выводит сообщение об ошибке.
2. Проводит валидацию даты рождения, проверяя соответствие формату `dd.MM.yyyy`.
3. Проверяет, что номер телефона — это целое число.
4. Проверяет, что пол указан как 'f' или 'm'.
5. Сохраняет информацию в файл с названием, совпадающим с фамилией пользователя. Если файл с таким именем уже существует, новая запись добавляется в конец файла.

## Установка и запуск программы

1. Убедитесь, что у вас установлена версия **Java 8** или новее.
2. Склонируйте репозиторий или создайте локальный файл с кодом программы.
3. Скомпилируйте программу:
    ```bash
    javac UserInfoApp.java
    ```
4. Запустите программу:
    ```bash
    java UserInfoApp
    ```

Программа предложит ввести данные одной строкой в формате:

`
Фамилия Имя Отчество ДатаРождения НомерТелефона Пол
`

Пример ввода:

`
Coolman Raisa Edmundovna 2015-07-14 456789456 f
`

## Пример работы программы

1. Если пользователь вводит корректные данные, программа сохранит информацию в файл:

Данные успешно сохранены в файл `Coolman.txt.`


3. Пример вывода ошибок:
- Если неверное количество данных:
  ```
  Ошибка: Некорректное количество данных. Ожидалось 6.
  ```
- Если неверный формат даты:
  ```
  Ошибка: Неверный формат даты. Используйте формат dd.MM.yyyy.
  ```
- Если некорректный номер телефона:
  ```
  Ошибка: Некорректный формат номера телефона.
  ```
- Если неверно указан пол:
  ```
  Ошибка: Некорректный пол. Ожидалось 'f' или 'm'.
  ```

## Ход решения

1. **Получение данных**:
Программа запрашивает у пользователя строку, которую разбивает на отдельные части с помощью метода `split(" ")`.

2. **Проверка количества данных**:
Если количество элементов в массиве не равно 6, выбрасывается исключение с сообщением о некорректном количестве введённых данных.

3. **Валидация даты**:
Используется `LocalDate` и `DateTimeFormatter` для проверки корректности даты рождения. Если формат не соответствует, выбрасывается исключение `DateTimeParseException`.

4. **Валидация номера телефона**:
Для проверки номера телефона используется метод `Long.parseLong`. В случае ошибки, выбрасывается `IllegalArgumentException`.

5. **Проверка пола**:
Программа проверяет, что введённый символ для пола равен `f` или `m` (с игнорированием регистра). При несоответствии выбрасывается исключение.

6. **Запись в файл**:
После успешной валидации всех данных программа сохраняет их в файл с именем, соответствующим фамилии пользователя. При этом используется `BufferedWriter`, и новые данные добавляются в конец файла.