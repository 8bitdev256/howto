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
