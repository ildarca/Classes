# Перечисления (enum) в C++

## Что такое перечисления?

Перечисления (enumerations) — это специальный тип данных в C++, который позволяет создавать именованные константы. Они решают фундаментальную проблему "магических чисел" в программировании.

## Создание перечислений

### Базовый синтаксис
```cpp
enum ИмяПеречисления {
  КОНСТАНТА1,
  КОНСТАНТА2,
  КОНСТАНТА3
};
```

### Пример
```cpp
enum Color {
  RED,    // RED = 0
  GREEN,  // GREEN = 1
  BLUE    // BLUE = 2
};
```

## Правила нумерации

### 1. Автоматическая нумерация (по умолчанию)
- Первая константа получает значение **0**
- Каждая следующая константа получает значение **на 1 больше** предыдущей

```cpp
enum Direction {
  NORTH,      // 0
  EAST,       // 1
  SOUTH,      // 2
  WEST        // 3
};
```

### 2. Явное указание значений
Можно задавать конкретные числовые значения:

```cpp
enum HttpStatus {
  OK = 200,
  NOT_FOUND = 404,
  SERVER_ERROR = 500
};
```

### 3. Смешанная нумерация
Комбинация явных и автоматических значений:

```cpp
enum Values {
  FIRST = 10,     // 10 (явно)
  SECOND,         // 11 (автоматически)
  THIRD = 50,     // 50 (явно)
  FOURTH          // 51 (автоматически)
};
```

### 4. Отрицательные значения
Значения могут быть отрицательными:

```cpp
enum ErrorCode {
  SUCCESS = 0,
  FILE_ERROR = -1,
  NETWORK_ERROR = -2
};
```

## Типы перечислений в C++

### C-style enum (устаревший подход)

Рассмотренные нами ранее перечисления являются устаревшими и пришли из языка C. Какие же проблемы в них имеются:

#### 1. Константы видны в общей области видимости

```cpp
enum Color { RED, GREEN, BLUE };
enum TrafficLight { RED, YELLOW, GREEN }; // ОШИБКА компиляции!
// Ошибка: повторное определение 'RED' и 'GREEN'
```

Проблема: все константы из перечисления "вываливаются" в окружающую область видимости, вызывая конфликты имен.

#### 2. Возможны конфликты имен

```cpp
enum FileType { TEXT, BINARY };
enum UserType { ADMIN, USER, GUEST };

int TEXT = 5; // ОШИБКА: конфликт с FileType::TEXT
```

Проблема: имена констант могут конфликтовать с другими идентификаторами в той же области видимости.

#### 3. Неявное преобразование к int

```cpp
enum Color { RED, GREEN, BLUE };
Color c = RED;

int number = c;           // Неявное преобразование - разрешено
if (c == 0) { ... }       // Сравнение с числом - разрешено
c = 5;                    // Присвоение числа - разрешено (опасно!)

// Бессмысленные, но допустимые операции:
Color color = RED;
if (color == 100) { ... } // Сравнение с произвольным числом
color = 255;              // Присвоение недопустимого значения
```

Проблема: компилятор не предотвращает ошибочное использование перечислений как обычных чисел.

#### 4. Отсутствие типобезопасности

```cpp
enum Color { RED, GREEN, BLUE };
enum Size { SMALL, MEDIUM, LARGE };

Color c = RED;
Size s = SMALL;

if (c == s) { ... }  // Разрешено, но логически неверно!
// Сравниваются разные сущности, но компилятор не ругается
```

Проблема: можно сравнивать и смешивать совершенно разные перечисления.


### enum class (современный подход)
### enum class (современный подход)

```cpp
enum class Color { RED, GREEN, BLUE };
enum class Size { SMALL, MEDIUM, LARGE };
```

**Преимущества:**

#### 1. Типобезопасность

```cpp
enum class Color { RED, GREEN, BLUE };
enum class Size { SMALL, MEDIUM, LARGE };

Color c = Color::RED;
// if (c == 0) { ... }           // ОШИБКА - нельзя сравнивать с числом
// if (c == Size::SMALL) { ... } // ОШИБКА - нельзя сравнивать разные enum
if (c == Color::RED) { ... }     // Правильно - только сравнение своего типа
```

#### 2. Локальная область видимости

```cpp
enum class Color { RED, GREEN, BLUE };
enum class TrafficLight { RED, YELLOW, GREEN }; // OK - нет конфликта

Color c = Color::RED;           // Доступ через ::
TrafficLight tl = TrafficLight::RED; // Разные RED
```

#### 3. Отсутствие конфликтов имен

```cpp
enum class FileType { TEXT, BINARY };
int TEXT = 5; // OK - нет конфликта

FileType ft = FileType::TEXT; // Доступ через ::
```

#### 4. Явное преобразование типов

```cpp
enum class Color { RED, GREEN, BLUE };
Color c = Color::RED;
// int number = c;                    // ОШИБКА - неявное преобразование
int number = static_cast<int>(c);     // Только явное преобразование
// c = 5;                            // ОШИБКА - нельзя присвоить число
```

## Указание базового типа

Для экономии памяти или работы с большими значениями можно указать базовый тип:
```cpp
enum class RbTreeColor : bool {
  RED = false,
  BLACK = true
}; // 1 байт

enum class SmallEnum : uint8_t {
  A,
  B,
  C
}; // 1 байт

enum class BigEnum : int32_t {
  LARGE = 1000000
}; // 4 байта
```

## Best Practices

1. **Всегда используйте `enum class`** вместо C-style enum
2. **Давайте осмысленные имена** перечислениям и их константам
3. **Группируйте связанные перечисления** в namespace
4. **Указывайте базовый тип** когда это важно для производительности
5. **Избегайте избыточных префиксов** в именах констант

**Правильно:**
```cpp
enum class Color { RED, GREEN, BLUE };
Color background = Color::RED;
```

**Избыточно:**
```cpp
enum class Color { COLOR_RED, COLOR_GREEN, COLOR_BLUE };
Color background = Color::COLOR_RED;
```

## Основные преимущества перечислений:

**1. Самодокументирующий код**
Вместо непонятных чисел:
```cpp
if (status == 1) { ... }  // Что означает 1?
```
Используем понятные имена:
```cpp
enum Status { PENDING, APPROVED, REJECTED };
if (status == Status::APPROVED) { ... }  // Ясно видно что это Статус APPROVED
```

**2. Ограничение допустимых значений**
Перечисления ограничивают возможные значения переменной. Компилятор не позволит присвоить переменной недопустимое значение.
```cpp
enum class Direction { NORTH, EAST, SOUTH, WEST };
Direction dir = Direction::NORTH; // Только 4 допустимых значения!
Direction dir = 5;                // ОШИБКА компиляции!
```

**3. Безопасность типов**
С `enum class` нельзя случайно сравнить значения разных перечислений или смешать их с числами.

**4. Удобство рефакторинга**
Если нужно изменить числовые значения констант, достаточно изменить их в одном месте — объявлении перечисления.
```cpp
// Было:
enum class Status {
  PENDING,  // 0
  APPROVED  // 1
};

// Стало:
enum class Status {
  PENDING = 10, // 10
  APPROVED = 20 // 20
};

// Код, использующий Status::PENDING, продолжит работать!
// Не нужно менять числа по всему коду
```

## Пример: Система статусов заказа
В этом примере мы создаем систему для отслеживания статуса заказа в интернет-магазине. В зависимости от статуса заказа на экран выводится соответствующая информация.

**Статусы заказа:**
- `PENDING` - ожидает обработки
- `PROCESSING` - в процессе сборки
- `SHIPPED` - отправлен
- `DELIVERED` - доставлен
- `CANCELLED` - отменен

```cpp
#include <iostream>
#include <string>

enum class OrderStatus {
  PENDING,
  PROCESSING,
  SHIPPED,
  DELIVERED,
  CANCELLED
};

void printOrderStatus(OrderStatus status) {
  switch(status) {
    case OrderStatus::PENDING:
      std::cout << "Заказ ожидает обработки" << std::endl;
      break;
    case OrderStatus::PROCESSING:
      std::cout << "Заказ в процессе сборки" << std::endl;
      break;
    case OrderStatus::SHIPPED:
      std::cout << "Заказ отправлен" << std::endl;
      break;
    case OrderStatus::DELIVERED:
      std::cout << "Заказ доставлен" << std::endl;
      break;
    case OrderStatus::CANCELLED:
      std::cout << "Заказ отменен" << std::endl;
      break;
  }
}

int main() {
  OrderStatus order = OrderStatus::PENDING;
  printOrderStatus(order);  // "Заказ ожидает обработки"

  order = OrderStatus::SHIPPED;
  printOrderStatus(order);  // "Заказ отправлен"

  return 0;
}
```