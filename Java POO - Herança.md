### Herança

- Herança em Java é muito simples. Basta utilizar a palavra reservada extends

Exemplo:

```
public class Moto extends Veiculo {
}
```

### Sealed, Non-Sealed e Final

Vamos supor que você queira que uma classe sua seja a última da hierarquia a ser herdada e portanto, deseje que nenhuma outra classe possa estendê-la (herdar seus atributos e métodos).

Para que isso seja possível, vamos usar o cenário abaixo como exemplo.

Supondo que você possua uma classe `Employee` (Funcionário), e esta seja a sua classe pai. E supondo também que essa classe não possa ser instanciada, ou seja, é uma classe abstrata, você possuirá um código parecido com o código abaixo:

```
public abstract class Employee {
  //...Propriedades e métodos...
}
```

Além dessa classe, você possui mais duas: `Manager` (Gerente) e `Salesman` (Vendedor). Estas duas classes herdam da classe `Employee`, conforme abaixo:

```
public class Manager extends Employee {
  //...Propriedades e métodos...
}

public class Salesman extends Employee {
  //...Propriedades e métodos...
}
```

Caso você deseje que tanto a classe `Manager` como a classe `Salesman` não sejam herdadas por outras classes, ou seja, sejam as últimas classes na hierarquia de herança, utilize a palavra reservada `final` em suas declarações para atingir esse objetivo, conforme abaixo:

```
public final class Manager extends Employee {
  //...Propriedades e métodos...
}

public final class Salesman extends Employee {
  //...Propriedades e métodos...
}
```

Um outro cenário que também pode ocorrer, é que você deseje que a classe pai `Employee` só possa ser herdada por classes específicas. Neste caso, você deve adicionar a palavra reservada `sealed` na classe pai, além da palavra reservada `permits`, informando em seguida o nome das classes permitidas:

```
public sealed abstract class Employee permits Manager, Salesman {
  //...Propriedades e métodos...
}
```

Mas e as subclasses? Bom, aí já vai depender de como você deseja que elas se comportem, mas uma das palavras reservadas a seguir elas precisam possuir caso usa classe pai seja `sealed`:

`Final`: As subclasses `Manager` e `Salesman` não podem ser herdadas por outras classes, conforme visto anteriormente;
`Non-sealed`: As subclasses `Manager` e `Salesman` podem ser herdadas por outras classes;
`Sealed`: As subclasses `Manager` e `Salesman` podem ser instanciadas por outras classes, desde que você as informe depois da palavra reservada `permits`.
