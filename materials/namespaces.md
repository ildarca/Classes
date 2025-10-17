# Пространства имен (namespace) в C++

## Что такое пространства имен?

Пространства имен — это механизм для организации кода в логические группы и предотвращения конфликтов имен. Они позволяют иметь одинаковые имена в разных частях программы без конфликтов.

## Создание пространства имен

### Базовый синтаксис
```cpp
namespace имя_пространства {
  // объявления классов, функций, переменных
}
```

### Пример
```cpp
namespace Math {
  const double PI = 3.14159;

  double square(double x) {
    return x * x;
  }

  double circleArea(double radius) {
    return PI * square(radius);
  }
}
```

## Использование пространств имен

### Полное квалифицированное имя
Полное квалифицированное имя — это имя, которое включает в себя все пространства имен и классы, необходимые для однозначной идентификации сущности.
```cpp
double area = Math::circleArea(5.0);
double pi_value = Math::PI;
```

### using declaration
```cpp
using Math::PI; // Теперь PI доступен без префикса Math::
double circumference = 2 * PI * 5.0;
```

### using directive
```cpp
using namespace Math; // Все имена из Math доступны без префикса Math::
double area = circleArea(5.0);
```

## Вложенные пространства имен

```cpp
namespace Company {
  namespace Department {
    namespace Project {
      class Employee {
        // ...
      };
    }
  }
}

// Использование
Company::Department::Project::Employee emp;
```

В C++17 появилось возможность удобнее писсать вложенные namespace используя ::
Пример:
```cpp
namespace Company::Department::Project {
  class Employee {
    // ...
  };
}
```

## Анонимные пространства имен
Эквивалент static-функциям в C - ограничивает видимость в пределах файла.

```cpp
namespace {
  int localVariable = 42; // Видна только в этом файле

  void helperFunction() {
    // Доступна только в этом файле
  }
}
```

## Практические примеры

### Пример: библиотека математических функций
```cpp
namespace Geometry {
  const double PI = 3.14159;

  class Point {
  public:
    double x, y;
    Point(double x, double y) : x(x), y(y) {}
  };

  double Distance(const Point& p1, const Point& p2) {
    return std::sqrt(std::pow(p2.x - p1.x, 2) + std::pow(p2.y - p1.y, 2));
  }
}

namespace Physics {
  const double GRAVITY = 9.81;

  double СalculateForce(double mass) {
    return mass * GRAVITY;
  }
}

int main() {
  // Использование
  Geometry::Point p1(0, 0);
  Geometry::Point p2(3, 4);

  double dist = Geometry::Distance(p1, p2);
  double force = Physics::CalculateForce(10.0);

  return 0;
}
```

## Best Practices

1. **Используйте пространства имен для библиотек** - предотвращает конфликты имен
2. **Избегайте `using namespace`** - может вызвать конфликты
3. **Используйте вложенные пространства для сложных проектов**
4. **Давайте осмысленные имена** пространствам имен

### Правильно:
```cpp
namespace MyCompany {
  namespace Graphics {
      class Renderer { /* ... */ };
  }
}

MyCompany::Graphics::Renderer renderer;
```

### Избегайте:
```cpp
using namespace std; // Опасно!
```

## Основные преимущества пространств имен

**1. Предотвращение конфликтов имен**
```cpp
namespace LibraryA {
  class String { /* ... */ };
}

namespace LibraryB {
  class String { /* ... */ };
}

// Нет конфликта - разные пространства имен
LibraryA::String str1;
LibraryB::String str2;
```

**2. Логическая организация кода**
```cpp
namespace Database {
  class Connection { /* ... */ };
  class Query { /* ... */ };
}

namespace Network {
  class HttpClient { /* ... */ };
  class WebSocket { /* ... */ };
}
```

**3. Улучшение читаемости**
```cpp
// Без namespace
DatabaseConnection* conn = CreateDatabaseConnection();

// С namespace
Database::Connection conn; // Более ясно откуда взялся Connection
```
