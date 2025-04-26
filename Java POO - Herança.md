### Herança

- Herança em Java é muito simples. Basta utilizar a palavra reservada extends

Exemplo:

```
public class Moto extends Veiculo {
}
```

### Sealed, Non-Sealed e Final

Vamos supor que você deseje que uma classe seja a última da hierarquia a ser herdada e, portanto, deseje que nenhuma outra classe possa estendê-la (herdar seus atributos e métodos).

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

Mas e as subclasses? Bom, aí já vai depender de como você deseja que elas se comportem, mas uma das palavras reservadas a seguir elas precisam possuir caso sua classe pai seja `sealed`:

`Final`: As subclasses `Manager` e `Salesman` não podem ser herdadas por outras classes, conforme visto anteriormente;

`Non-sealed`: As subclasses `Manager` e `Salesman` podem ser herdadas por outras classes;

`Sealed`: As subclasses `Manager` e `Salesman` podem ser instanciadas por outras classes, desde que você as informe depois da palavra reservada `permits`.

### Instance of

Palavra reservada utilizada para descobrir se a variável é uma instância de uma classe espeífica:

```
public abstract class Employee {
  //...Propriedades e métodos...
}

public class Manager extends Employee {
  //...Propriedades e métodos...
}

public class Main {
  public static void Main(String[] args) {
  }

  public static void printEmployee(Employee employee) {
  
    System.out.prinln(employee.getClass().getCanonicalName())
    
    if (employee instanceof Manager) {
      employee.setName("João");
      ((Manager) employee).setLogin("joao");
      ((Manager) employee).setPassword("123456");
    }
  }

}
```

No Java 16 (não LTS) e no 17 (LTS) e também em versões acima, você não precisa mais fazer o casting conforme código acima do método `printEmployee`. Basta fazer como o código abaixo:

```
public static void printEmployee(Employee employee) {

  System.out.prinln(employee.getClass().getCanonicalName())
  
  if (employee instanceof Manager manager) {
    employee.setName("João");
    manager.setLogin("joao");
    manager.setPassword("123456");
  }
}
```

Quando a variável é uma instância de uma subclasse (`Salesman` ou `Manager`), mas esta subclasse herda de uma superclasse (`Employee`) e você tenta verificar se ela é uma instância da superclasse, será retornado True também. Só para o contrário que ela retornará False, pois a superclase não herda nada de uma subclasse:

```
public abstract class Employee {
  //...Propriedades e métodos...
}

public class Manager extends Employee {
  //...Propriedades e métodos...
}

public class Main {
  public static void Main(String[] args) {
    Employee employee = new Employee();
    Employee manager = new Manager();
    System.out.prinln(manager instanceof Manager); //retorna True
    System.out.prinln(manager instanceof Employee); //retorna True
    System.out.prinln(employee instanceof Manager); //retorna False
  }

  public static void printEmployee(Employee employee) {
  
    System.out.prinln(employee.getClass().getCanonicalName())
    
    if (employee instanceof Manager) {
      employee.setName("João");
      ((Manager) employee).setLogin("joao");
      ((Manager) employee).setPassword("123456");
    }
  }

}
```

### Switch

Apenas uma observação sobre as classes `sealed`, é que se você utilizar um switch em uma variável que é do tipo da classe pai (`Employee`, por exemplo) que é `sealed`, mas pode ser uma instância de alguma subclasse (`Manager` ou `Salesman`, por exemplo), não há a necessidade de uso da palavra reservada `default` no switch, pois na classe pai já foram definidas as classes permitidas para herança. Portanto, essa variável só pode ser uma instância das classes permitidas (`Manager` ou `Salesman`). O switch só vai exigir que você implemente o case das classes permitidas neste caso.

### Super

Palavra reservada utilizada geralmente em herança/abstração. Serve geralmente para chamar o construtor da classe pai. Quando você trabalha com classes seladas (sealed), e cria um construtor na classe pai que possui argumentos, você precisa criar também um construtor nas classes filhas, que chamará o construtor da classe pai, conforme abaixo:

```
public sealed abstract class Employee permits Manager, Salesman {
  //Propriedades

  public Employee(String code, String name) {
    this.code = code;
    this.name = name;
  }

  //Métodos
}

public non-sealed class Manager extends Employee {
  //Propriedades

  public Manager(String code, String name) {
    super(code, name);
  }

  //Métodos
}

public non-sealed class Salesman extends Employee {
  //Propriedades

  public Salesman(String code, String name) {
    super(code, name);
  }

  //Métodos
}
```

Referente ao exemplo das nossas classes Employee, Manager e Salesman, vamos supor que você queira adicionar um prefixo ao código do funcionário quando ele for vendedor ou gerente, como 'MN' para Manager e 'SL' para Salesman:

```
public sealed abstract class Employee permits Manager, Salesman {
  //Propriedades

  public Employee(String code, String name) {
    this.code = code;
    this.name = name;
  }

  public String getCode() {
    return this.code;
  }

  //Métodos
}

public non-sealed class Manager extends Employee {
  //Propriedades

  public Manager(String code, String name) {
    super(code, name);
  }

  @Override
  public String getCode() {
    return "MN" + super.getCode();
  }

  //Métodos
}

public non-sealed class Salesman extends Employee {
  //Propriedades

  public Salesman(String code, String name) {
    super(code, name);
  }

  @Override
  public String getCode() {
    return "SL" + super.getCode();
  }

  //Métodos
}
```
