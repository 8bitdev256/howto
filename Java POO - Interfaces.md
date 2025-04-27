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

Todas as propriedades (variáveis) que vamos declarar em uma interface são por padrão `public`, `static` e `final`. Por tanto, usar estas palavras reservadas para declarar uma propriedade dentro de uma interface é redundante.

