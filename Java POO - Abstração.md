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
