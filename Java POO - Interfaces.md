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

