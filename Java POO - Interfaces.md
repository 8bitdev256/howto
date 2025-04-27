### Interfaces

Java não permite herança múltipla, mas uma classe A pode implementar uma classe B e uma classe C. Interfaces servem justamente para que você possa herdar em sua classe filha atributos e comportamentos de mais de uma classe pai. Todas as propriedades (variáveis) que vamos declarar em uma interface são por padrão `public`, `static` e `final`. Por tanto, usar estas palavras reservadas para declarar uma propriedade dentro de uma interface é redundante. Já os métodos, por padrão são abstratos. Quando uma interface herda uma interface, seus métodos não precisam ser implementados, pois quem herda é uma interface, e não uma classe. Records permitem o uso de interfaces através da palavra reservada `implements`. As interfaces permitem que você crie métodos com corpo, mas desde que eles sejam métodos `default`. Métodos default podem retornar qualquer tipo, mas precisam da palavra reservada `default` em sua declaração. Estes métodos não possuem implementação obrigatória na classe que herdará a interface, mas eles podem ser sobrescritos na classe. São utéis por exemplo se você tem um framework, quer disponibilizar um novo método, mas não quer quebrar a aplicação para quem já a utiliza.

Exemplo: 

```
public interface Impressora {
	public void imprimir();
}

public interface Copiadora {
	public void copiar();
}

public interface Digitalizadora {
	public void digitalizar();
}

public class EquipamentoMultifuncional implements Impressora, Copiadora, Digitalizadora {
	@Override
	public void imprimir() {
		System.out.println("Imprimindo");
	}

	@Override
	public void copiar() {
		System.out.println("Copiando");
	}

	@Override
	public void digitalizar() {
		System.out.println("Digitalizando");
	}
}
```

### Interfaces funcionais

São a base para criação do lambda. Só podem possuir um método obrigatório para implementar, mas podem possuir vários métodos `default`.

```
public class Main {
	public static void main(String[] args) {
		List<User> users = List.of(new User("Maria", 21), new User("João", 32));
		
		//Esta interface Consumer é do próprio Java

		//Module java.base
		//Package java.util.function
		//Interface Consumer<T>
		//
		//    Type Parameters:
		//      T - the type of the input to the operation
		//
		//    All Known Subinterfaces:
		//        Stream.Builder<T>
		//
		//    Functional Interface:
		//        This is a functional interface and can therefore be used as the assignment target for a lambda expression or method reference.
		//
		//    @FunctionalInterface
		//    public interface Consumer<T>
		//
		//    Represents an operation that accepts a single input argument and returns no result. Unlike most other functional interfaces, Consumer is expected to operate via side-effects.
		//
		//    This is a functional interface whose functional method is accept(Object).

		//Classe anônima de nome consumer que implementa a interface Consumer do Java
		var consumer = new Consumer<User>() {
			@Override
			public void accept(final User user) {
				System.out.println(user);
			}
		};

		users.foreach(consumer);
	}
}
```

O código acima pode ser simplificado para o código abaixo: 

```
public class Main {
	public static void main(String[] args) {
		List<User> users = List.of(new User("Maria", 21), new User("João", 32));
		
		users.foreach((User user) -> {
			System.out.println(user);
		});
	}
}
```

Pode ser mais simplificado ainda:

```
public class Main {
	public static void main(String[] args) {
		List<User> users = List.of(new User("Maria", 21), new User("João", 32));
		
		users.foreach(user -> {
			System.out.println(user);
		});
	}
}
```

Como o código acima vai executar apenas uma linha dentro do `foreach` (`System.out.println(user);`), podemos simplificar mais uma vez:

```
public class Main {
	public static void main(String[] args) {
		List<User> users = List.of(new User("Maria", 21), new User("João", 32));
		
		users.foreach(user -> System.out.println(user));
	}
}
```

Ou, se você preferir, pode ser simplificado ainda mais usando method reference:


```
public class Main {
	public static void main(String[] args) {
		List<User> users = List.of(new User("Maria", 21), new User("João", 32));
		
		users.foreach(System.out::println);
	}
}
```
