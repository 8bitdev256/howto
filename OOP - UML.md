# OOP - UML (Made with [Mermaid](https://mermaid.js.org/))

## Association

Relationship between two objects

### Simple Association

A person has an address

```mermaid
classDiagram
    class Person {

    }

    class Address {

    }

    Person --> Address
```

### Bidirectional Association

Owners feed pets, pets please owners

```mermaid
classDiagram
    class Owner {
        +feed
    }

    class Pet {
        +please
    }

    Owner <--> Pet
```
## Aggregation

Implies a relationship where the child can exist independently of the parent. Example: Class (parent) and Student (child). Delete the Class and the Students still exist.

```mermaid
classDiagram
    class Class {

    }

    class Student {

    }

    Class o-- Student
```

## Composition

Implies a relationship where the child cannot exist independent of the parent. Example: House (parent) and Room (child). Rooms don't exist separate to a House.

```mermaid
classDiagram
    class House {

    }

    class Room {

    }

    House *-- Room
```

## Cardinality / Multiplicity on relations

 - 1 Only 1
 - 0..1 Zero or One
 - 1..* One or more
 - * Many
 - n n (where n>1)
 - 0..n zero to n (where n>1)
 - 1..n one to n (where n>1)

```
classDiagram
    Customer "1" --> "*" Ticket
    Student "1" --> "1..*" Course
    Galaxy --> "many" Star : Contains
```

# Other Example

```mermaid
classDiagram
    class ReprodutorMusical {
        +exemploMetodo1()
        +exemploMetodo2(String exemplo)
    }

    class AparelhoTelefonico {
        +exemploMetodo1()
        +exemploMetodo2(String exemplo)
    }

    class NavegadorInternet {
        +exemploMetodo1()
        +exemploMetodo2(String exemplo)
    }

    class iPhone {
    }

    iPhone --> ReprodutorMusical
    iPhone --> AparelhoTelefonico
    iPhone --> NavegadorInternet
```
