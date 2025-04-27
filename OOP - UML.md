# OOP - UML (Made with [Mermaid](https://mermaid.js.org/))

More information about Mermaid/UML check [Mermaid](https://mermaid.js.org/) website

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
