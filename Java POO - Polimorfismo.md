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
