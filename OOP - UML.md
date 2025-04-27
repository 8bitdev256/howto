# OOP - UML (Made with [Mermaid](https://mermaid.js.org/))

## Association

Relationship between two objects

### Simple Association

```mermaid
classDiagram
    class ClassA {

    }

    class ClassB {

    }

    ClassA <-- ClassB
```

### Bidirectional Association

owners feed pets, pets please owners

```mermaid
classDiagram
    class Owner {
        +feed
    }

    class Pet {
        +please
    }

    ClassA <--> ClassB
```
## Aggregation

Aggregation implies a relationship where the child can exist independently of the parent.

```mermaid
classDiagram
    class ClassA {

    }

    class ClassB {

    }

    ClassA o-- ClassB
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
