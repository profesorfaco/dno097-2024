### DESARROLLO WEB Y DISEÑO VISUAL DE INFORMACIÓN → Clase 05 → 03/04/2023

# Formatos ligeros de intercambios de datos en la creación de gráficas: JSON (primera parte)

### Teoría (para la casa)

JSON es sigla de JavaScript Object Notation (notación de objetos en JavaScript), sigla que refiere a su origen, pero no a su actual uso como formato de intercambio de datos. Es que el formato no es idéntico a la notación de Javascript y muchos otros lenguajes de programación pueden aprovecharlo.

Por ejemplo, puedo tener una variable en JavaScript como la que sigue:

```
const ejemplo = [
    {
        student: "AGUIRRE ULLOA MANUELA",
        title: "Design For Dignity",
        tutor: "GONZÁLEZ, A.",
        what: "safety blanket…",
        what_for: "s.i.",
        year: 2012,
    },
    {
        student: "ARAOS ANDUEZA TRINIDAD",
        title: "EL NOGAL, ROPA ORGÁNICA PARA BEBÉS",
        tutor: "MORENO, P.",
        what: "Vestuario sustentable para babés…",
        what_for: "Crear vestimenta para bebés…",
        year: 2015,
    },
]
```

Si los mismos datos fueran intercambiados mediante un `ejemplo.json`, sería:

```
[
	{
		"student": "AGUIRRE ULLOA MANUELA",
		"title": "Design For Dignity",
		"tutor": "GONZÁLEZ, A.",
		"what": "safety blanket…",
		"what_for": "s.i.",
		"year": 2012
	},
	{
		"student": "ARAOS ANDUEZA TRINIDAD",
		"title": "EL NOGAL, ROPA ORGÁNICA PARA BEBÉS",
		"tutor": "MORENO, P.",
		"what": "Vestuario sustentable para babés…",
		"what_for": "Crear vestimenta para bebés…",
		"year": 2015
	}
]
```

Pueden copiar el código del ejemplo y revisarlo con servios tales como https://jsonlint.com/ o https://jsonformatter.curiousconcept.com/

El parecido entre lo que es, originalmente, una *JavaScript Object Notation* y el formato JSON, hace que no necesitemos simplicar *fetch* ni *parsing* con alguna biblioteca de Javascript. Nos basta con: 

```
async function dale() {
  const consulta = await fetch("…");
  const data = await consulta();
  console.log(data);
}
dale().catch((error) => console.error(error));
```
PENDIENTE



- - - - - - - - - - - - - - 

### Práctica (para la clase)

Pendiente.

- - - - - - - 

###### [← CLASE PREVIA](https://github.com/profesorfaco/dno097-2024/tree/main/clase-04) • [SIGUIENTE CLASE →](https://github.com/profesorfaco/dno097-2024/tree/main/clase-06)
