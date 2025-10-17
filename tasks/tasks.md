## Class, enum class, namespace

### **Важные указания по выполнению заданий:**

**Общие требования:**
- Внимательно ознакомьтесь с каждым заданием перед началом работы
- По теоретическим вопросам обращайтесь к материалам в папке `materials`
- Во всех задачах обязательно проверяйте корректность входных данных
- При обнаружении некорректных входных данных выводите `"n/a"` и завершайте работу программы
- Соблюдайте стиль кодирования и требования к именованию классов, методов и переменных

**Примечание:** В каждом задании подробно описаны технические требования и приведены примеры работы. Следуйте им точно для успешного выполнения работы.

### **Quest 1: Класс "Фильм"**
**Файл:** `src/q1_movie_class.cc`

**Задача:** Создать класс `Movie` для управления коллекцией фильмов и функцию для сортировки и поиска фильмов.

**Технические требования:**
- Класс `Movie` должен содержать поля: название (string), год выпуска (Year), рейтинг (Rating)
- Класс `Movie` должен содержать методы:
  - конструктор для инициализации всех полей
  - геттеры для всех полей: `GetTitle()`, `GetYear()`, `GetRating()`
- Создать функцию `GetHighRatedMovies()` которая:
  - принимает вектор фильмов
  - возвращает вектор фильмов с рейтингом > 7.5, отсортированный по году выпуска (по возрастанию)
- Создать функцию `PrintMovies()` для вывода фильмов в формате: `"год: название (рейтинг)"`
- Использовать `using Year = int` для представления года выпуска
- Использовать `using Rating = double` для представления рейтинга фильма
- Использовать `namespace Cinema` для изоляции своего кода
- Если количество фильмов ≤ 0, вывести `"n/a"` и завершить работу

**Примеры работы:**

| Входные данные | Выходные данные |
|----------------|-----------------|
| `3`<br>`The_Matrix 1999 8.7`<br>`Inception 2010 8.8`<br>`Titanic 1997 7.8` | `High rated movies:`<br>`1997: Titanic (7.8)`<br>`1999: The_Matrix (8.7)`<br>`2010: Inception (8.8)` |
| `2`<br>`Avatar 2009 7.9`<br>`Twilight 2008 5.2` | `High rated movies:`<br>`2009: Avatar (7.9)` |
| `4`<br>`Film1 2015 6.0`<br>`Film2 2010 8.0`<br>`Film3 2005 7.6`<br>`Film4 2020 7.4` | `High rated movies:`<br>`2005: Film3 (7.6)`<br>`2010: Film2 (8.0)` |
| `0` | `n/a` |
| `1`<br>`Low_Rated_Film 2022 5.0` | `High rated movies:`<br>`No high rated movies` |

---

### **Quest 2: Класс "Покупатель"**
**Файл:** `src/q2_customer_class.cc`

**Задача:** Создать класс `Customer` для анализа данных о покупках клиентов.

**Технические требования:**
- Класс `Customer` должен содержать поля: имя (string), сумма покупок (Money)
- Класс `Customer` должен содержать методы:
  - конструктор для инициализации всех полей
  - геттеры для всех полей: `GetName()`, `GetTotalSpent()`
  - `GetStatus()` - определение статуса клиента (CustomerStatus)
- Создать функцию `FindCustomersAboveAverage()` которая:
  - принимает вектор покупателей
  - возвращает вектор покупателей с суммой покупок выше среднего
- Создать функцию `FindVIPCustomers()` которая:
  - принимает вектор покупателей
  - возвращает вектор VIP-клиентов
- Создать функцию `PrintCustomers()` для вывода покупателей в формате: `"имя: сумма - Статус"`
- Использовать `using Money = double` для представления денежных сумм
- Использовать `namespace Shop` для изоляции классов и функций, связанных с магазином
- Использовать `enum class CustomerStatus` для классификации статусов клиентов
- Если количество покупателей ≤ 0, вывести `"n/a"` и завершить работу

**Статусы клиентов:**
- `REGULAR` - обычный (сумма покупок ≤ 1000)
- `PREMIUM` - премиум (сумма покупок 1001-1500)
- `VIP` - VIP (сумма покупок > 1500)

**Примеры работы:**

| Входные данные | Выходные данные |
|----------------|-----------------|
| `3`<br>`John 1500.50`<br>`Alice 800.25`<br>`Bob 2100.75` | `Above average:`<br>`John: 1500.50 - PREMIUM`<br>`Bob: 2100.75 - VIP`<br>`VIP customers:`<br>`Bob` |
| `2`<br>`Mike 500.0`<br>`Sarah 600.0` | `Above average:`<br>`Sarah: 600.00 - REGULAR`<br>`VIP customers: None` |
| `4`<br>`Client1 1200.0`<br>`Client2 900.0`<br>`Client3 1800.0`<br>`Client4 700.0` | `Above average:`<br>`Client1: 1200.00 - PREMIUM`<br>`Client3: 1800.00 - VIP`<br>`VIP customers:`<br>`Client3` |
| `0` | `n/a` |
| `1`<br>`Single_Client 2000.0` | `Above average:`<br>`Single_Client: 2000.00 - VIP`<br>`VIP customers:`<br>`Single_Client` |
---

### **Quest 3: Класс "Город"**
**Файл:** `src/q3_city_class.cc`

**Задача:** Создать класс `City` для анализа демографических данных городов.

**Технические требования:**
- Класс `City` должен содержать поля: название (string), население (Population), площадь (Area)
- Класс `City` должен содержать методы:
  - конструктор для инициализации всех полей
  - геттеры для всех полей: `GetName()`, `GetPopulation()`, `GetArea()`
  - `CalculateDensity()` - расчет плотности населения (Density)
  - `GetSizeCategory()` - определение категории размера города (CitySize)
- Создать функцию `FindHighestDensityCity()` которая:
  - принимает вектор городов
  - возвращает город с наибольшей плотностью населения
- Создать функцию `FindLargestAreaCity()` которая:
  - принимает вектор городов
  - возвращает город с наибольшей площадью
- Использовать `using Population = int` для представления численности населения
- Использовать `using Area = double` для представления площади в км²
- Использовать `using Density = double` для представления плотности населения (чел/км²)
- Использовать `namespace Geography` для изоляции своего кода
- Использовать `enum class CitySize` для классификации городов по размеру
- Если количество городов ≤ 0, вывести `"n/a"` и завершить работу

**Категории размеров городов:**
- `SMALL` - малый (население ≤ 500,000)
- `MEDIUM` - средний (население 500,001 - 1,000,000)
- `LARGE` - крупный (население 1,000,001 - 5,000,000)
- `MEGA` - мегаполис (население > 5,000,000)

**Примеры работы:**

| Входные данные | Выходные данные |
|----------------|-----------------|
| `3`<br>`Moscow 12600000 2561.5`<br>`Tokyo 13960000 2194.0`<br>`Paris 2200000 105.4` | `Highest density: Paris (20872.87)`<br>`Largest area: Moscow (2561.50)`<br>`City sizes:`<br>`Moscow - MEGA`<br>`Tokyo - MEGA`<br>`Paris - LARGE` |
| `2`<br>`London 8900000 1572.0`<br>`Berlin 3700000 891.7` | `Highest density: Berlin (4150.67)`<br>`Largest area: London (1572.00)`<br>`City sizes:`<br>`London - MEGA`<br>`Berlin - LARGE` |
| `4`<br>`New_York 8419000 783.8`<br>`Sydney 5312000 12367.0`<br>`Singapore 5686000 728.6`<br>`Vienna 1897000 414.6` | `Highest density: Singapore (7802.20)`<br>`Largest area: Sydney (12367.00)`<br>`City sizes:`<br>`New_York - MEGA`<br>`Sydney - MEGA`<br>`Singapore - MEGA`<br>`Vienna - LARGE` |
| `0` | `n/a` |
| `1`<br>`Small_City 100000 50.0` | `Highest density: Small_City (2000.00)`<br>`Largest area: Small_City (50.00)`<br>`City sizes:`<br>`Small_City - SMALL` |

---

### **Quest 4: Класс "Игрок"**
**Файл:** `src/q4_player_class.cc`

**Задача:** Создать класс `Player` для рейтинга игроков в видеоигре.

**Технические требования:**
- Класс `Player` должен содержать поля:
  - никнейм (string)
  - уровень (Level)
  - количество очков (Score)
- Класс `Player` должен содержать методы:
  - конструктор для инициализации всех полей
  - геттеры для всех полей: `GetNickname()`, `GetLevel()`, `GetScore()`
  - `GetRank()` - определение ранга игрока (Rank)
- Создать функцию `GetTopPlayers()` которая:
  - принимает вектор игроков
  - возвращает топ-3 игрока по количеству очков (по убыванию)
- Создать функцию `CalculateAverageLevel()` которая:
  - принимает вектор игроков
  - возвращает средний уровень всех игроков
- Создать функцию `PrintPlayers()` для вывода игроков в формате: `"никнейм (очки) - ранг"`
- Использовать `using Score = double` для представления количества очков
- Использовать `using Level = int` для представления уровня игрока
- Использовать `namespace Game` для изоляции своего кода
- Использовать `enum class Rank` для классификации рангов игроков
- Если количество игроков ≤ 0, вывести `"n/a"` и завершить работу

**Ранги игроков:**
- `NOVICE` - новичок (0-4999 очков)
- `EXPERIENCED` - опытный (5000-14999 очков)
- `EXPERT` - эксперт (15000-24999 очков)
- `MASTER` - мастер (25000+ очков)

**Примеры работы:**

| Входные данные | Выходные данные |
|----------------|-----------------|
| `4`<br>`Player1 25 15400.5`<br>`Player2 30 18900.0`<br>`Player3 18 9200.0`<br>`Player4 42 25600.0` | `Top 3 players:`<br>`1. Player4 (25600.0) - MASTER`<br>`2. Player2 (18900.0) - EXPERT`<br>`3. Player1 (15400.0) - EXPERT`<br>`Average level: 28.75`|
| `2`<br>`Gamer1 15 3500.0`<br>`Gamer2 20 4800.0` | `Top 3 players:`<br>`1. Gamer2 (4800.0) - NOVICE`<br>`2. Gamer1 (3500.0) - NOVICE`<br>`Average level: 17.50`|
| `5`<br>`ProPlayer 50 30000.0`<br>`MidPlayer 35 12000.0`<br>`Newbie 10 800.0`<br>`Veteran 45 18000.0`<br>`Casual 20 3000.0` | `Top 3 players:`<br>`1. ProPlayer (30000.0) - MASTER`<br>`2. Veteran (18000.0) - EXPERT`<br>`3. MidPlayer (12000.0) - EXPERIENCED`<br>`Average level: 32.00`|
| `0` | `n/a` |
| `1`<br>`SoloPlayer 28 500.0` | `Top 3 players:`<br>`1. SoloPlayer (500.0) - NOVICE`<br>`Average level: 28.00`|
---

### **Quest 5: Класс "Библиотека"**
**Файл:** `src/q5_library_class.cc`

**Задача:** Создать систему управления библиотекой с классами `Book` и `Library`.

**Технические требования:**
- Класс `Book` должен содержать поля: название (string), автор (string), год издания (Year), статус доступности (BookStatus)
- Класс `Book` должен содержать методы:
  - конструктор для инициализации всех полей
  - геттеры для всех полей: `GetTitle()`, `GetAuthor()`, `GetYear()`, `GetStatus()`
  - `IsAvailable()` - проверка доступности книги (bool)
- Класс `Library` должен содержать поля:
  - коллекция книг (vector<Book>)
- Класс `Library` должен содержать методы:
  - `AddBook(const Book& book)` - добавление книги в библиотеку (void)
  - `GetAvailableBooks()` - получение списка доступных книг (vector<Book>)
  - `CountAvailableBooks()` - подсчет количества доступных книг (int)
  - `FindBooksByAuthor(const string& author)` - поиск книг по автору (vector<Book>)
- Вывести список доступных книг в формате: `"название (год) - автор"`
- Подсчитать общее количество доступных книг
- Использовать `using BookId = int` для идентификации книг (если потребуется)
- Использовать `using Year = int` для представления года издания
- Использовать `namespace LibrarySystem` для изоляции библиотечных классов
- Использовать `enum class BookStatus` для типизации статусов книг
- Если количество книг ≤ 0, вывести `"n/a"` и завершить работу

**Статусы доступности книг:**
- `AVAILABLE` - книга доступна для выдачи
- `BORROWED` - книга выдана читателю
- `RESERVED` - книга забронирована
- `LOST` - книга утеряна

**Примеры работы:**

| Входные данные | Выходные данные |
|----------------|-----------------|
| `3`<br>`1984 George_Orwell 1949 AVAILABLE`<br>`Cosmos Carl_Sagan 1980 BORROWED`<br>`Dune Frank_Herbert 1965 AVAILABLE` | `Available books:`<br>`1984 (1949) - George_Orwell`<br>`Dune (1965) - Frank_Herbert`<br>`Total available: 2`|
| `2`<br>`Book1 Author1 2000 BORROWED`<br>`Book2 Author2 2010 RESERVED` | `Available books:`<br>`No books available`<br>`Total available: 0`|
| `4`<br>`Harry_Potter J.K._Rowling 1997 AVAILABLE`<br>`Lord_of_the_Rings J.R.R._Tolkien 1954 BORROWED`<br>`The_Hobbit J.R.R._Tolkien 1937 AVAILABLE`<br>`Game_of_Thrones George_Martin 1996 RESERVED` | `Available books:`<br>`Harry_Potter (1997) - J.K._Rowling`<br>`The_Hobbit (1937) - J.R.R._Tolkien`<br>`Total available: 2`|
| `1`<br>`Single_Book Author 2020 LOST` | `Available books:`<br>`No books available`<br>`Total available: 0`|
| `0` | `n/a` |

---

### **Quest 6: Класс "Банковский счет"**
**Файл:** `src/q6_bank_account.cc`

**Задача:** Создать класс `BankAccount` для управления банковскими операциями.

**Технические требования:**
- Класс `BankAccount` должен содержать поля: номер счета (AccountNumber), владелец (string), баланс (Money), история операций (vector<Transaction>)
- Класс `BankAccount` должен содержать методы:
  - конструктор для инициализации счета, владельца и начального баланса
  - геттеры для всех полей: `GetAccountNumber()`, `GetOwner()`, `GetBalance()`, `GetTransactionHistory()`
  - `Deposit(Money amount)` - пополнение счета (bool)
  - `Withdraw(Money amount)` - снятие средств (bool)
  - `Transfer(BankAccount& to, Money amount)` - перевод на другой счет (bool)
  - `AddFee(Money amount)` - начисление комиссии (bool)
- Структура `Transaction` должна содержать: тип операции (TransactionType), сумма (Money), связанный счет (для переводов), временная метка
- Создать функцию `FindAccountWithMaxBalance()` которая:
  - принимает вектор счетов
  - возвращает счет с максимальным балансом
- Создать функцию `ProcessOperations()` которая:
  - обрабатывает список операций
  - выводит ошибки при невозможности выполнения операции
- Использовать `using Money = double` для представления денежных сумм
- Использовать `using AccountNumber = string` для представления номеров счетов
- Использовать `namespace Banking` для изоляции своего кода
- Использовать `enum class TransactionType` для типизации банковских операций
- Если количество счетов ≤ 0, вывести `"n/a"` и завершить работу

**Типы банковских операций:**
- `DEPOSIT` - пополнение счета
- `WITHDRAWAL` - снятие средств
- `TRANSFER` - перевод между счетами
- `FEE` - банковская комиссия

**Обработка ошибок:**
- При ошибке выводить сообщение в формате: `"Error: <описание ошибки>"`
- После вывода ошибки продолжать выполнение программы для остальных операций

**Возможные ошибки:**
- `Insufficient funds` - недостаточно средств для снятия или перевода
- `Account not found` - указанный счет не существует
- `Invalid amount` - сумма операции ≤ 0
- `Same account transfer` - попытка перевода на тот же счет
- `Negative balance` - попытка установить отрицательный начальный баланс

**Примеры работы:**

| Входные данные | Выходные данные |
|----------------|-----------------|
| `3`<br>`ACC001 John 5000.0`<br>`ACC002 Jane 3200.5`<br>`ACC003 Bob 10000.0`<br>`DEPOSIT ACC001 1000.0`<br>`WITHDRAWAL ACC002 500.0`<br>`TRANSFER ACC003 ACC001 2000.0`<br>`FEE ACC002 50.0` | `Highest balance: ACC003 (8000.0)`<br>`ACC001 history:`<br>`DEPOSIT: +1000.0`<br>`TRANSFER: +2000.0`<br>`ACC002 history:`<br>`WITHDRAWAL: -500.0`<br>`FEE: -50.0`<br>`ACC003 history:`<br>`TRANSFER: -2000.0` |
| `2`<br>`ACC001 Alice 1500.0`<br>`ACC002 Mike 800.0`<br>`DEPOSIT ACC001 300.0`<br>`WITHDRAWAL ACC002 1000.0`<br>`TRANSFER ACC001 ACC002 400.0`<br>`FEE ACC001 10.0` | `Error: Insufficient funds`<br>`Highest balance: ACC001 (1390.0)`<br>`ACC001 history:`<br>`DEPOSIT: +300.0`<br>`TRANSFER: -400.0`<br>`FEE: -10.0`<br>`ACC002 history:`<br>`TRANSFER: +400.0` |
| `2`<br>`ACC001 Tom 2000.0`<br>`ACC002 Anna 3000.0`<br>`DEPOSIT ACC001 -100.0`<br>`WITHDRAWAL ACC002 0.0`<br>`TRANSFER ACC001 ACC001 500.0`<br>`FEE ACC002 -20.0` | `Error: Invalid amount`<br>`Error: Invalid amount`<br>`Error: Same account transfer`<br>`Error: Invalid amount`<br>`Highest balance: ACC002 (3000.0)` |
| `1`<br>`ACC001 Sarah -100.0` | `Error: Negative balance`<br>`n/a` |
| `0` | `n/a` |

---

### **Quest 7: Класс "Музыкальный плейлист"**
**Файл:** `src/q7_music_collection.cc`

**Задача:** Создать систему управления музыкальной коллекцией с классами `Song` и `Playlist`.

**Технические требования:**
- Класс `Song` должен содержать поля: название (string), исполнителя (string), длительность (Duration), жанр (Genre), рейтинг (Rating)
- Класс `Song` должен содержать методы:
  - конструктор для инициализации всех полей
  - геттеры для всех полей: `GetTitle()`, `GetArtist()`, `GetDuration()`, `GetGenre()`, `GetRating()`
- Класс `Playlist` должен управлять коллекцией песен и содержать методы:
  - `AddSong(const Song& song)` - добавление песни в плейлист (void)
  - `GetTotalDuration() const` - расчет общей длительности (Duration)
  - `GetGenresStatistics() const` - статистика по жанрам (vector<pair<Genre, int>>)
  - `GetExcellentSongs() const` - получение песен с рейтингом EXCELLENT (vector<Song>)
- Рассчитать общую длительность плейлиста в формате: `XXXs (XXmXXs)`
- Сгруппировать песни по жанрам
- Вывести песни с наивысшим рейтингом
- Использовать `using Duration = int` для представления длительности треков в секундах
- Использовать `namespace Music` для изоляции своего кода
- Использовать `enum class Genre` для типизации музыкальных жанров
- Использовать `enum class Rating` для классификации качества песен по пользовательским оценкам

**Типы музыкальных жанров:**
- `POP` - поп-музыка
- `ROCK` - рок-музыка
- `JAZZ` - джаз
- `CLASSICAL` - классическая музыка
- `ELECTRONIC` - электронная музыка
- `HIPHOP` - хип-хоп
- `COUNTRY` - кантри

**Типы рейтингов песен:**
- `POOR` - плохой (0-2 звезды)
- `AVERAGE` - средний (2.1-3 звезды)
- `GOOD` - хороший (3.1-4 звезды)
- `EXCELLENT` - отличный (4.1-5 звезд)

**Примеры работы:**

| Входные данные | Выходные данные |
|----------------|-----------------|
| `4`<br>`Bohemian_Rhapsody Queen 354 ROCK 4.9`<br>`Shape_of_You Ed_Sheeran 233 POP 3.8`<br>`Take_Five Dave_Brubeck 324 JAZZ 4.7`<br>`Thunderstruck AC_DC 292 ROCK 4.2` | `Total duration: 1203s (20m3s)`<br>`Genres: ROCK(2) POP(1) JAZZ(1)`<br>`Top rated songs:`<br>`Bohemian_Rhapsody - Queen (4.9)`<br>`Take_Five - Dave_Brubeck (4.7)`<br>`Thunderstruck - AC_DC (4.2)` |
| `3`<br>`Song1 Artist1 180 POP 1.5`<br>`Song2 Artist2 240 ROCK 2.8`<br>`Song3 Artist3 200 JAZZ 3.5` | `Total duration: 620s (10m20s)`<br>`Genres: POP(1) ROCK(1) JAZZ(1)`<br>`Top rated songs:`<br>`Song3 - Artist3 (3.5)` |
| `2`<br>`Track1 Singer1 300 POP 4.5`<br>`Track2 Singer2 300 POP 4.8` | `Total duration: 600s (10m0s)`<br>`Genres: POP(2)`<br>`Top rated songs:`<br>`Track1 - Singer1 (4.5)`<br>`Track2 - Singer2 (4.8)` |
| `1`<br>`Bad_Song Artist 120 COUNTRY 0.5` | `Total duration: 120s (2m0s)`<br>`Genres: COUNTRY(1)`<br>`Top rated songs: No excellent songs` |
| `0` | `n/a` |

---

### **Quest 8: Класс "Медицинская карта"**
**Файл:** `src/q8_medical_record.cc`

**Задача:** Создать класс `Patient` для управления медицинскими записями.

**Технические требования:**
- Класс `Patient` должен содержать поля: имя (string), возраст (Age), диагноз (Diagnosis), наличие страховки (bool)
- Класс `Patient` должен содержать методы:
  - конструктор для инициализации всех полей
  - геттеры для всех полей: `GetName()`, `GetAge()`, `GetDiagnosis()`, `HasInsurance()`
  - `GetTreatmentCost()` - расчет стоимости лечения (Money)
  - `GetPriority()` - определение приоритета лечения (Priority)
- Определить пациентов, требующих срочного лечения (приоритет HIGH)
- Рассчитать среднюю стоимость лечения по всем пациентам
- Использовать `using Money = double` для представления денежных сумм
- Использовать `using Age = int` для представления возраста пациентов
- Использовать `namespace Medical` для изоляции своего кода и `enum class Diagnosis` для типизации заболеваний
- Использовать `enum class Priority` для классификации срочности лечения

**Типы диагнозов:**
- `FLU` - грипп
- `FRACTURE` - перелом
- `HEART_DISEASE` - сердечное заболевание
- `DIABETES` - диабет

**Типы приоритетов лечения:**
- `LOW` - низкий (грипп)
- `MEDIUM` - средний (диабет, перелом)
- `HIGH` - высокий (сердечные заболевания)

**Стоимость лечения по диагнозам:**
- `FLU` - 500
- `FRACTURE` - 2000
- `DIABETES` - 1000
- `HEART_DISEASE` - 25000
- При наличии страховки стоимость уменьшается на 80%

**Примеры работы:**

| Входные данные | Выходные данные |
|----------------|-----------------|
| `3`<br>`John 45 HEART_DISEASE true`<br>`Maria 28 FLU false`<br>`Robert 62 DIABETES true` | `Urgent care:`<br>`John (HEART_DISEASE) - HIGH`<br>`Avg cost: 8833.33` |
| `2`<br>`Patient1 30 FLU true`<br>`Patient2 25 FRACTURE false` | `Urgent care: None`<br>`Avg cost: 1500.00` |
| `1`<br>`Anna 50 DIABETES true` | `Urgent care: None`<br>`Avg cost: 200.00` |
| `0` | `n/a` |

---

### **Quest 9: Класс "Автомобиль"**
**Файл:** `src/q9_car_fleet.cc`

**Задача:** Создать систему управления автопарком с классом `Car`.

**Технические требования:**
- Класс `Car` должен содержать поля: марка (string), модель (string), год выпуска (int), объем двигателя (double), пробег (Mileage), тип топлива (FuelType)
- Класс `Car` должен содержать методы:
  - конструктор для инициализации всех полей
  - геттеры для всех полей: `GetBrand()`, `GetModel()`, `GetYear()`, `GetEngineVolume()`, `GetMileage()`, `GetFuelType()`
  - `CalculateTax()` - расчет транспортного налога (Money)
  - `NeedsMaintenance()` - проверка необходимости ТО (bool)
  - `GetCarClass()` - определение класса автомобиля (CarClass)
- Найти автомобили, требующие техобслуживания (пробег > 30000 км)
- Рассчитать общую сумму налогов по всему автопарку
- Использовать `using Money = double` для представления денежных сумм
- Использовать `using Mileage = int` для представления пробега в километрах
- Использовать `namespace Automotive` для изоляции своего кода и `enum class FuelType` для типизации видов топлива
- Использовать `enum class CarClass` для классификации автомобилей

**Типы топлива:**
- `PETROL` - бензин
- `DIESEL` - дизель
- `ELECTRIC` - электричество
- `HYBRID` - гибрид

**Классы автомобилей:**
- `ECONOMY` - эконом (объем двигателя ≤ 1.6)
- `COMFORT` - комфорт (объем двигателя 1.7-2.5)
- `BUSINESS` - бизнес (объем двигателя 2.6-3.5)
- `LUXURY` - люкс (объем двигателя > 3.5 или электромобили)

**Расчет налога:**
- Эконом: 1000 × объем двигателя
- Комфорт: 2000 × объем двигателя
- Бизнес: 5000 × объем двигателя
- Люкс: 10000 × объем двигателя
- Электромобили: фиксированно 5000
- Гибридные автомобили: 70% от расчета для бензинового автомобиля того же класса

**Примеры работы:**

| Входные данные | Выходные данные |
|----------------|-----------------|
| `3`<br>`Toyota Corolla 2020 1.8 45000 PETROL`<br>`BMW X5 2022 3.0 12000 DIESEL`<br>`Tesla Model_S 2023 0.0 8000 ELECTRIC` | `Maintenance needed:`<br>`Toyota Corolla (45000km)`<br>`Car classes:`<br>`Toyota Corolla - COMFORT`<br>`BMW X5 - BUSINESS`<br>`Tesla Model_S - LUXURY`<br>`Total tax: 48500.0` |
| `2`<br>`Hundai Solaris 2018 1.6 25000 PETROL`<br>`Kia Rio 2019 1.4 28000 PETROL` | `Maintenance needed: None`<br>`Car classes:`<br>`Hundai Solaris - ECONOMY`<br>`Kia Rio - ECONOMY`<br>`Total tax: 3000.0` |
| `1`<br>`Mercedes S-class 2021 4.0 15000 PETROL` | `Maintenance needed: None`<br>`Car classes:`<br>`Mercedes S-class - LUXURY`<br>`Total tax: 40000.0` |
| `3`<br>`Toyota_Prius 2021 1.8 15000 HYBRID`<br>`Honda_Insight 2020 1.5 12000 HYBRID`<br>`Ford_Fusion 2019 2.0 18000 HYBRID` | `Maintenance needed: None`<br>`Car classes:`<br>`Toyota_Prius - COMFORT`<br>`Honda_Insight - ECONOMY`<br>`Ford_Fusion - COMFORT`<br>`Total tax: 4760.0` |
| `0` | `n/a` |

---

### **Quest 10: Класс "Учебный курс"**
**Файл:** `src/q10_university_course.cc`

**Задача:** Создать систему управления учебным курсом с классами `Student` и `Course`.

**Технические требования:**
- Класс `Student` должен содержать поля: имя (string), список оценок (vector<Grade>)
- Класс `Student` должен содержать методы:
  - конструктор для инициализации имени и оценок
  - `GetName()` - получение имени студента (string)
  - `GetGrades()` - получение списка оценок (vector<Grade>)
  - `CalculateGPA()` - расчет среднего балла (GPA)
  - `GetGradeLetter()` - получение буквенной оценки (GradeLetter)
  - `GetPerformance()` - определение успеваемости (Performance)
- Класс `Course` должен управлять студентами и содержать методы:
  - `AddStudent(const Student& student)` - добавление студента в курс (void)
  - `GetBestStudent()` - поиск лучшего студента (Student)
  - `GetStudentsNeedingHelp()` - получение студентов, нуждающихся в помощи (vector<Student>)
  - `CalculateAverageGPA()` - расчет среднего GPA по курсу (GPA)
- Найти лучшего студента по среднему баллу
- Выявить студентов, нуждающихся в помощи (GPA < 2.0)
- Рассчитать средний GPA по всему курсу
- Использовать `using Grade = int` для представления оценок в баллах
- Использовать `using GPA = double` для представления среднего балла
- Использовать `namespace University` для изоляции учебных классов и `enum class GradeLetter` для буквенных оценок
- Использовать `enum class Performance` для классификации успеваемости

**Буквенные оценки:**
- `A` - отлично (90-100 баллов)
- `B` - хорошо (75-89 баллов)
- `C` - удовлетворительно (60-74 балла)
- `D` - плохо (40-59 баллов)
- `F` - неудовлетворительно (0-39 баллов)

**Уровни успеваемости:**
- `EXCELLENT` - отличная (GPA ≥ 3.5)
- `GOOD` - хорошая (GPA 2.5-3.4)
- `AVERAGE` - средняя (GPA 2.0-2.4)
- `FAILING` - неуспевающая (GPA < 2.0)

**Расчет GPA:**
- A = 4.0 балла
- B = 3.0 балла
- C = 2.0 балла
- D = 1.0 балл
- F = 0.0 баллов

**Примеры работы:**

| Входные данные | Выходные данные |
|----------------|-----------------|
| `4`<br>`Alice 85 92 78`<br>`Bob 45 60 55`<br>`Carol 95 88 92`<br>`David 75 80 72` | `Best student: Carol (GPA: 4.0) - A`<br>`Students needing help:`<br>`Bob (GPA: 1.0) - D`<br>`Average course GPA: 3.08`<br>`Performance: GOOD` |
| `3`<br>`Student1 90 85 95`<br>`Student2 80 75 85`<br>`Student3 70 65 75` | `Best student: Student1 (GPA: 4.0) - A`<br>`Students needing help: None`<br>`Average course GPA: 3.67`<br>`Performance: EXCELLENT` |
| `2`<br>`John 50 55 60`<br>`Jane 35 40 45` | `Best student: John (GPA: 2.0) - C`<br>`Students needing help:`<br>`Jane (GPA: 0.0) - F`<br>`Average course GPA: 1.00`<br>`Performance: FAILING` |
| `0` | `n/a` |