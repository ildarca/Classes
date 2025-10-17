### **Quest 1: Класс "Фильм"**
**Файл:** `src/q1_movie_class.cc`

**Задача:** Создать класс `Movie` для управления коллекцией фильмов с поиском и сортировкой.

**Технические требования:**
- Класс должен содержать поля: название (string), год выпуска (int), рейтинг (double)
- Реализовать метод для вывода фильмов с рейтингом выше 7.5
- Отсортировать результат по году выпуска (по возрастанию)
- Если количество фильмов ≤ 0, вывести `"n/a"` и завершить работу
- Использовать `using Year = int` и `using Rating = double`

**Примеры работы:**

| Входные данные | Выходные данные |
|----------------|-----------------|
| `3`<br>`The_Matrix 1999 8.7`<br>`Inception 2010 8.8`<br>`Titanic 1997 7.8` | `High rated movies:`<br>`1997: Titanic (7.8)`<br>`1999: The_Matrix (8.7)`<br>`2010: Inception (8.8)` |
| `2`<br>`Avatar 2009 7.9`<br>`Twilight 2008 5.2` | `High rated movies:`<br>`2009: Avatar (7.9)` |
| `0` | `n/a` |

---

### **Quest 2: Класс "Покупатель"**
**Файл:** `src/q2_customer_class.cc`

**Задача:** Создать класс `Customer` для анализа данных о покупках клиентов.

**Технические требования:**
- Класс должен содержать поля: имя (string), сумма покупок (double)
- Найти и вывести покупателей с суммой покупок выше среднего
- Определить VIP-клиентов (сумма покупок > 1500)
- Использовать `using Money = double` и `namespace Shop`
- Если количество покупателей ≤ 0, вывести `"n/a"`

**Примеры работы:**

| Входные данные | Выходные данные |
|----------------|-----------------|
| `3`<br>`John 1500.50`<br>`Alice 800.25`<br>`Bob 2100.75` | `Above average:`<br>`John: 1500.50`<br>`Bob: 2100.75`<br>`VIP: Bob` |
| `2`<br>`Mike 500.0`<br>`Sarah 600.0` | `Above average:`<br>`Sarah: 600.00`<br>`VIP: None` |
| `0` | `n/a` |

---

### **Quest 3: Класс "Город"**
**Файл:** `src/q3_city_class.cc`

**Задача:** Создать класс `City` для анализа демографических данных городов.

**Технические требования:**
- Класс должен содержать поля: название (string), население (int), площадь (double)
- Найти город с наибольшей плотностью населения (население / площадь)
- Найти город с наибольшей площадью
- Использовать `using Population = int`, `using Area = double`, `using Density = double`
- Использовать `namespace Geography`
- Если количество городов ≤ 0, вывести `"n/a"`

**Примеры работы:**

| Входные данные | Выходные данные |
|----------------|-----------------|
| `3`<br>`Moscow 12600000 2561.5`<br>`Tokyo 13960000 2194.0`<br>`Paris 2200000 105.4` | `Highest density: Paris (20872.87)`<br>`Largest area: Moscow (2561.50)` |
| `2`<br>`London 8900000 1572.0`<br>`Berlin 3700000 891.7` | `Highest density: Berlin (4150.67)`<br>`Largest area: London (1572.00)` |
| `0` | `n/a` |

---

### **Quest 4: Класс "Игрок"**
**Файл:** `src/q4_player_class.cc`

**Задача:** Создать класс `Player` для рейтинга игроков в видеоигре.

**Технические требования:**
- Класс должен содержать поля: никнейм (string), уровень (int), количество очков (double)
- Вывести топ-3 игрока по количеству очков (по убыванию)
- Рассчитать средний уровень всех игроков
- Определить ранг игрока на основе очков:
  - NOVICE: 0-4999 очков
  - EXPERIENCED: 5000-14999 очков
  - EXPERT: 15000-24999 очков
  - MASTER: 25000+ очков
- Использовать `using Score = double`, `using Level = int`
- Использовать `enum class Rank` для ранга
- Обернуть код в `namespace Game`
- Если количество игроков ≤ 0, вывести `"n/a"`

**Примеры работы:**

| Входные данные | Выходные данные |
|----------------|-----------------|
| `4`<br>`Player1 25 15400.5`<br>`Player2 30 18900.0`<br>`Player3 18 9200.0`<br>`Player4 42 25600.0` | `Top 3:`<br>`1. Player4 (25600.0) - MASTER`<br>`2. Player2 (18900.0) - EXPERT`<br>`3. Player1 (15400.0) - EXPERT`<br>`Avg level: 28.75` |
| `2`<br>`Gamer1 15 3500.0`<br>`Gamer2 20 4800.0` | `Top 3:`<br>`1. Gamer2 (4800.0) - NOVICE`<br>`2. Gamer1 (3500.0) - NOVICE`<br>`Avg level: 17.50` |
| `0` | `n/a` |

---

### **Quest 5: Класс "Библиотека"**
**Файл:** `src/q5_library_class.cc`

**Задача:** Создать систему управления библиотекой с классами `Book` и `Library`.

**Технические требования:**
- Класс `Book` должен содержать: название, автора, год издания, статус доступности
- Класс `Library` должен управлять коллекцией книг
- Вывести список доступных книг
- Подсчитать общее количество доступных книг
- Использовать `using BookId = int`, `using Year = int`
- Использовать `namespace LibrarySystem` и `enum class BookStatus`
- Статусы доступности книг:
  - `AVAILABLE` - книга доступна для выдачи
  - `BORROWED` - книга выдана читателю
  - `RESERVED` - книга забронирована
  - `LOST` - книга утеряна
- Если количество книг ≤ 0, вывести `"n/a"`

**Примеры работы:**

| Входные данные | Выходные данные |
|----------------|-----------------|
| `3`<br>`1984 George_Orwell 1949 AVAILABLE`<br>`Cosmos Carl_Sagan 1980 BORROWED`<br>`Dune Frank_Herbert 1965 AVAILABLE` | `Available books:`<br>`1984 (1949)`<br>`Dune (1965)`<br>`Total: 2 available` |
| `2`<br>`Book1 Author1 2000 BORROWED`<br>`Book2 Author2 2010 RESERVED` | `Available books:`<br>`No books available` |
| `0` | `n/a` |

---

### **Quest 6: Класс "Банковский счет"**
**Файл:** `src/q6_bank_account.cc`

**Задача:** Создать класс `BankAccount` для управления банковскими операциями.

**Технические требования:**
- Класс должен содержать: номер счета, владельца, баланс
- Реализовать операции: пополнение, снятие, перевод
- Найти счет с максимальным балансом
- Вывести историю операций для счета
- Использовать `using Money = double`, `using AccountNumber = string`
- Использовать `namespace Banking` и `enum class TransactionType`
- Типы банковских операций:
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
- Класс должен содержать: имя, возраст, диагноз, наличие страховки
- Определить пациентов, требующих срочного лечения
- Рассчитать среднюю стоимость лечения
- Использовать `using Money = double`, `using Age = int`
- Использовать `namespace Medical` и `enum class Priority`
- Если количество пациентов ≤ 0, вывести `"n/a"`

**Примеры работы:**

| Входные данные | Выходные данные |
|----------------|-----------------|
| `3`<br>`John 45 HEART_DISEASE true`<br>`Maria 28 FLU false`<br>`Robert 62 CANCER true` | `Urgent care:`<br>`Robert (CANCER)`<br>`John (HEART_DISEASE)`<br>`Avg cost: 25833.33` |
| `2`<br>`Patient1 30 FLU true`<br>`Patient2 25 FLU false` | `Urgent care: None`<br>`Avg cost: 500.00` |
| `0` | `n/a` |

---

### **Quest 9: Класс "Автомобиль"**
**Файл:** `src/q9_car_fleet.cc`

**Задача:** Создать систему управления автопарком с классом `Car`.

**Технические требования:**
- Класс должен содержать: марку, модель, год, объем двигателя, пробег
- Найти автомобили, требующие техобслуживания (пробег > 30000)
- Рассчитать общую сумму налогов
- Использовать `using Money = double`, `using Mileage = int`
- Использовать `namespace Automotive` и `enum class FuelType`
- Если количество автомобилей ≤ 0, вывести `"n/a"`

**Примеры работы:**

| Входные данные | Выходные данные |
|----------------|-----------------|
| `3`<br>`Toyota_Corolla 2020 1.8 45000`<br>`BMW_X5 2022 3.0 12000`<br>`Tesla_Model_S 2023 0.0 8000` | `Maintenance needed:`<br>`Toyota_Corolla (45000km)`<br>`Total tax: 48500.0` |
| `2`<br>`Car1 2018 2.0 25000`<br>`Car2 2019 1.6 28000` | `Maintenance needed: None`<br>`Total tax: 18000.0` |
| `0` | `n/a` |

---

### **Quest 10: Класс "Учебный курс"**
**Файл:** `src/q10_university_course.cc`

**Задача:** Создать систему управления учебным курсом с классами `Student` и `Course`.

**Технические требования:**
- Класс `Student` должен содержать: имя, список оценок
- Класс `Course` должен управлять студентами и оценками
- Найти лучшего студента по среднему баллу
- Выявить студентов, нуждающихся в помощи (GPA < 2.0)
- Использовать `using Grade = int`, `using GPA = double`
- Использовать `namespace University` и `enum class GradeLetter`
- Если количество студентов ≤ 0, вывести `"n/a"`

**Примеры работы:**

| Входные данные | Выходные данные |
|----------------|-----------------|
| `4`<br>`Alice 85 92 78`<br>`Bob 45 60 55`<br>`Carol 95 88 92`<br>`David 75 80 72` | `Best: Carol (4.0)`<br>`Need help: Bob (1.0)`<br>`Avg GPA: 3.08` |
| `3`<br>`Student1 90 85 95`<br>`Student2 80 75 85`<br>`Student3 70 65 75` | `Best: Student1 (4.0)`<br>`Need help: None`<br>`Avg GPA: 3.67` |
| `0` | `n/a` |