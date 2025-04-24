
## Anotações

### Modificadores de Acesso

 - Em Java, quando existe mais de uma classe dentro do mesmo pacote,
 e em uma dessas classes há um método sem um modificador de acesso (private, protected ou public),
 a visibilidade deste método é considerada a visibilidade default, ou seja, este método estará visível
 para todas as outras classes do mesmo pacote em que a classe que este método foi declarado está.
 
 Exemplo:
 
 ```
 package com.meusistema.service
 
 public class Cliente {
	//Método sem modificador de acesso. Portanto, visibilidade default.
	void salvarCliente() {
		
	}
	
	//Método com modificador de acesso private.
	private void adicionarCliente() {
		
	}
 }
 ```
 
 No código acima, a classe Cliente possui o método `salvarCliente`, que ficará visível para a classe Produto abaixo, pois está no mesmo pacote que a classe Cliente (`package com.meusistema.service`):
  
 ```
 package com.meusistema.service
 
 public class Produto {
	//Método com modificador de acesso private.
	private void salvarCliente() {
		
	}
	
	//Método com modificador de acesso private.
	private void adicionarCliente() {
		
	}
 }
 ```
### Getters e Setters

Podem ser criados:
1 - Manualmente;

2 - No Elipse, através das teclas `Ctrl + Barra de Espaço`, digitando parte do nome antes;

3 - `Botão direito do mouse -> Source -> Generate Getters and Setters...`.

```
public class Student {
	private String name;

	public String getName() {
		return name;
	}

	public void setName(String newValue) {
		name = newValue;
	}
}
```

### Construtores

Em Java, funcionam de maneira parecida com C#. Exemplo:

```
public class Pessoa {
	private String nome;
	private String cpf;

	public Pessoa(String nome, String cpf) {
		this.nome = nome;
		this.cpf = cpf;
	}
}
```
### Enums

Funcionam de forma bem diferente do C#. Exemplo:

```
// Criando o enum EstadoBrasileiro para ser usado em toda a aplicação.
public enum EstadoBrasileiro {
	SAO_PAULO ("SP","São Paulo"),
	RIO_JANEIRO ("RJ", "Rio de Janeiro"),
	PIAUI ("PI", "Piauí"),
	MARANHAO ("MA","Maranhão") ;
	
	private String nome;
	private String sigla;
	
	private EstadoBrasileiro(String sigla, String nome) {
		this.sigla = sigla;
		this.nome = nome;
	}
	public String getSigla() {
		return sigla;
	}
	public String getNome() {
		return nome;
	}
	public String getNomeMaiusculo() {
		return nome.toUpperCase();
	}
	
}
```

Exemplo de classe que utiliza o enum criado acima:

```
// qualquer classe do sistema poderá obter os objetos de EstadoBrasileiro
public class SistemaIbge {
	public static void main(String[] args) {
		//imprimindo os estados existentes no enum
		for(EstadoBrasileiro uf: EstadoBrasileiro.values() ) {
		   System.out.println(uf.getSigla() + "-" + uf.getNomeMaiusculo());
		}
		
		//selecionando um estado a partir das opções disponíveis
		EstadoBrasileiro ufSelecionado = EstadoBrasileiro.PIAUI;
		
		System.out.println("O estado selecionado foi: " + ufSelecionado.getNome());
	}
}
```

### Herança

- Herança em Java é muito simples. Basta utilizar a palavra reservada extends

Exemplo:

```
public class Moto extends Veiculo {
}
```

### Abstração

- Na classe abstrata, inserir a palavra reservada `abstract` para a classe e para o método abstrato, caso possua. Na classe derivada, utilizar também a palavra reservada `extends`. No método da classe derivada que será implementado (sobrescrito), utilizar anotação `@Override` acima de sua declaração

Exemplo:

```
//Classe abstrata
public abstract class Veiculo {
	public abstract void ligar();
}

public class Moto extends Veiculo {
	@Override
	public void ligar() {
		//some code here
	}
}
```

### Polimorfismo

- A abstração por si só, já é um exemplo de polimorfismo. Basicamente entende-se por porlimorfismo vários procedimentos que possuem a mesma finalidade, mas possuem maneiras específicas (diferentes) de realizá-lo. Uma moto e um carro são dois veículos que você pode dirigir, mas você não dirige uma moto da mesma maneira que dirige um carro

Exemplo:

```
public abstract class Veiculo {
	public abstract void dirigir();
}

public class Carro extends Veiculo {
	@Override
	public void dirigir() {
		System.out.println("Acelerando veículo com o pé");
	}
}

public class Moto extends Veiculo {
	@Override
	public void dirigir() {
		System.out.println("Acelerando veículo com a mão");
	}
}
```

### Interfaces

- Java não permite herança múltipla, mas uma classe A pode implementar uma classe B e uma classe C. Interfaces servem justamente para que você possa herdar em sua classe filha atributos e comportamentos de mais de uma classe pai.

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

### Records

 - Entrou no Java na versão 14 (não LTS) e na versão 17 (LTS). Funcionam de forma semelhante a uma classe, mas só permitem criação de atributos não estáticos informados no seu construtor. A própria declaração da classe já é o construtor

Exemplo 1:

```
public record Person() {
	//Criando atributo estático público
	public static String name;
}

public class Main {
	public static void main (String[] args) {
		Person.name = "João";
		System.out.println(Person.name);
		//Não vai encontrar a propriedade name, mesmo sendo pública
	}
}
```

Exemplo 2:

```
//Criando atributo no construtor da record
public record Person(String name) {
}

public class Main {
	public static void main (String[] args) {
		Person person = new Person("João");
		System.out.println(person);
		//Saída: Person[name=João]

		System.out.println(person.name);
		//A linha acima vai dar erro, pois a propriedade name definida no construtor da record, é por padrão private e final. Para acessar a propriedade há um getter já implícito, que pode ser acessado conforme abaixo
		System.out.println(person.name());

		//Para modificar o valor do atributo name, nenhuma das formas abaixo funciona, pois o setter não é criado automaticamente.
		person.name = "Maria";
		person.name("Maria");

		//O record serve para trabalhar com valores imutáveis, por isso, é impossível modificar seus valores
	}
}
```

É possível declarar um construtor sem argumentos na record (compact constructor), onde o código dentro dele será executado antes de qualquer outra utilização do objeto instanciado. O compact constructor pode ser usado para fazer validação de valores, trabalhar com exceção, etc.

Exemplo:

```
public record Person(String name) {

	public Person {
		System.out.prinln("Eu serei executado antes");
	}
}

public class Main {
	public static void main (String[] args) {
		Person person = new Person("João");
		System.out.println(person.name());
		//Saída:
		//# Eu serei executado antes
		//# João
	}
}
```

É possível também trabalhar com mais de um construtor nos Records. Porém, é necessário chamar o construtor padrão dele. Confira o exemplo abaixo:

```
public record Person(String name, int age) {

	public Person {
	}

	public Person(String name) {
		//Chamando construtor padrão
		this(name, 1)
	}
}
```
