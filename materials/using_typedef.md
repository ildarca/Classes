# Псевдонимы типов (typedef и using) в C++

## Что такое псевдонимы типов?

Псевдонимы типов позволяют создавать новые имена для существующих типов данных. Это улучшает читаемость кода и упрощает его поддержку.

## typedef (C-стиль)

### Синтаксис
```cpp
typedef существующий_тип новое_имя;
```

### Примеры
```cpp
typedef int Age;
typedef double Salary;
typedef std::string Name;

Age userAge = 25;
Salary userSalary = 50000.0;
Name userName = "Иван Иванов";
```

### Для сложных типов
```cpp
typedef int* IntPointer;
typedef int IntArray[10];
typedef void (*FunctionPtr)(int); // Указатель на функцию

IntPointer ptr = new int(5);
IntArray numbers = {1, 2, 3, 4, 5};
FunctionPtr callback = nullptr;
```

## using (современный подход, C++11)

### Синтаксис
```cpp
using новое_имя = существующий_тип;
```

### Примеры
```cpp
using Age = int;
using Salary = double;
using Name = std::string;

Age userAge = 25;
Salary userSalary = 50000.0;
Name userName = "Иван Иванов";
```

### Для сложных типов
```cpp
using IntPointer = int*;
using IntArray = int[10];
using FunctionPtr = void(*)(int); // Указатель на функцию

IntPointer ptr = new int(5);
IntArray numbers = {1, 2, 3, 4, 5};
FunctionPtr callback = nullptr;
```

## Сравнение typedef и using

### typedef (менее читаемый)
```cpp
typedef void (*OldFuncPtr)(int, double); // Сложно читать
typedef int (*ArrayPtr)[10]; // Неочевидный синтаксис
```

### using (более понятный)
```cpp
using NewFuncPtr = void(*)(int, double); // Более понятно
using ArrayPtr = int(*)[10];             // Четкий синтаксис
```

## Практические примеры использования

### Упрощение сложных типов
```cpp
#include <vector>
#include <map>
#include <string>

// Псевдонимы для упрощения кода
using StringList = std::vector<std::string>;
using StudentGrades = std::map<std::string, double>;
using IntMatrix = std::vector<std::vector<int>>;

StringList names = {"Анна", "Борис", "Виктор"};
StudentGrades grades = {{"Анна", 4.5}, {"Борис", 3.8}};
IntMatrix matrix = {{1, 2, 3}, {4, 5, 6}};
```

### Пример: система управления заказами
```cpp
#include <vector>
#include <string>
#include <cstdint>

// Псевдонимы для бизнес-логики
using CustomerId = uint32_t;
using OrderId = uint64_t;
using Price = double;
using ProductList = std::vector<std::string>;

struct Order {
  OrderId id;
  CustomerId customer;
  Price total;
  ProductList products;
};

void processOrder(const Order& order) {
  // Код становится более читаемым
  std::cout << "Обработка заказа #" << order.id << std::endl;
  std::cout << "Клиент: " << order.customer << std::endl;
  std::cout << "Сумма: " << order.total << std::endl;
}
```

## Best Practices

1. **Используйте `using` вместо `typedef`** в новом коде
2. **Давайте описательные имена** псевдонимам
3. **Группируйте псевдонимы** в соответствующих namespace
4. **Используйте для упрощения сложных типов**
5. **Применяйте для платформо-независимых типов**
