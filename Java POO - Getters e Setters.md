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
