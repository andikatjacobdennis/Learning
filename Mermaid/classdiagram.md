A Mermaid class diagram is a way to describe object-oriented structures (classes, attributes, methods, inheritance, relationships) using simple text syntax that renders into UML-style diagrams.

## Basic Example

```mermaid
classDiagram
    class Animal {
        +String name
        +eat()
    }

    class Dog {
        +bark()
    }

    Animal <|-- Dog
```

This creates:

* `Animal` class with fields and methods
* `Dog` class inheriting from `Animal`

---

# Common Syntax

### Visibility Symbols

| Symbol | Meaning          |
| ------ | ---------------- |
| `+`    | public           |
| `-`    | private          |
| `#`    | protected        |
| `~`    | package/internal |

---

# Relationships

## Inheritance

```mermaid
classDiagram
    Animal <|-- Dog
```

## Association

```mermaid
classDiagram
    Customer --> Order
```

## Aggregation

```mermaid
classDiagram
    Team o-- Player
```

## Composition

```mermaid
classDiagram
    House *-- Room
```

## Dependency

```mermaid
classDiagram
    Controller ..> Service
```

---

# Interfaces

```mermaid
classDiagram
    class Flyable {
        <<interface>>
        fly()
    }

    Bird --|> Flyable
```

---

# Multiplicity

```mermaid
classDiagram
    Customer "1" --> "*" Order
```

Examples:

* `"1"` = exactly one
* `"*"` = many
* `"0..1"` = optional
* `"1..*"` = one or more

---

# Labels

```mermaid
classDiagram
    Customer --> Order : places
```

---

# Full Example

```mermaid
classDiagram

    class User {
        +String id
        +String email
        +login()
        +logout()
    }

    class Admin {
        +manageUsers()
    }

    class Product {
        +String sku
        +float price
    }

    class Order {
        +Date createdAt
        +calculateTotal()
    }

    User <|-- Admin
    User "1" --> "*" Order : places
    Order "*" --> "*" Product : contains
```
