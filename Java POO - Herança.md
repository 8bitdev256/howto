### Herança

- Herança em Java é muito simples. Basta utilizar a palavra reservada extends

Exemplo:

```
public class Moto extends Veiculo {
}
```

Vamos supor que você queira que uma classe sua seja a última da hierarquia a ser herdada e portanto, deseje que nenhuma outra classe possa estendê-la (herdar seus atributos e métodos).

Para que isso seja possível, vamos usar o cenário abaixo como exemplo.

Supondo que você possua uma classe `Employee` (Funcionário), e esta seja a sua classe pai. E supondo também que essa classe possa ser instanciada, ou seja, é uma classe abstrata, você possuirá um código parecido com o código abaixo:

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
