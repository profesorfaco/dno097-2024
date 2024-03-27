### DESARROLLO WEB Y DISEÑO VISUAL DE INFORMACIÓN → Clase 04 → 27/03/2023

# Formatos ligeros de intercambios de datos en la creación de gráficas: CSV

### Teoría (para la casa)

CSV es sigla de Comma Separated Values (Valores separados por comas en castellano), y resulta de exportar los datos de una Tabla, Hoja de Cálculo o Planilla de Excel.

En el ejemplo del artículo de Wikipedia para [Valores separados por comas](https://es.wikipedia.org/wiki/Valores_separados_por_comas), tenemos los siguientes datos:

| Año | Marca | Modelo | Descripción | Precio |
|:----|:-------|:-------|:------------|:-------|
| 1997	| Ford	| E350	| ac, ABS, moon	| 3000.00 |
| 1999	| Chevy	| Venture	| Extended Edition | 4900.00 |
| 1999 | Chevy | Venture | Extended Edition, Very Large	| 5000.00 |
| 1996 | Jeep | Grand Cherokee | MUST SELL! air, moon roof, loaded	| 4799.00 |

Los mismos datos en CSV:

```
Año,Marca,Modelo,Descripción,Precio
1997,Ford,E350,"ac, ABS, moon",3000.00
1999,Chevy,Venture,Extended Edition,4900.00
1999,Chevy,Venture,"Extended Edition, Very Large",5000.00
1996,Jeep,Grand Cherokee,"MUST SELL! air, moon roof, loaded",4799.00
```

Las filas siguen siendo filas. Las columnas son reemplazadas por la separación de las comas.

Si nos quedamos con la primera fila (de arriba hacia abajo) podemos notar su función de encabezado de columna: Le da sentido a lo que sigue abajo, sean años, marcas, modelos, descripciones o precios.

Así mismo podríamos leer un CSV con más datos: 

https://raw.githubusercontent.com/profesorfaco/dno097-2024/main/clase-04/sietes.csv

Siendo tantos datos, conviene aprovecharnos de una manera en que GitHub muestra los CSV dentro de los repositorios:

https://github.com/profesorfaco/dno097-2024/blob/main/clase-04/sietes.csv

Lo que tenemos entre los datos es una consulta parcial de https://diseno.uc.cl/memorias/all.php

La pregunta que le podemos hacer al CSV es: ¿Cuántos sietes hay registrados entre los años 2010 y 2022? 

¡Pero no los contemos a mano! Contémoslos con JavaScript, y mostremos el resultado con SVG.

Primero necesitamos hacer un *fetch* y un *parser* de los datos en [sietes.csv](https://raw.githubusercontent.com/profesorfaco/dno097-2024/main/clase-04/sietes.csv). Para hacer lo que necesitamos muy rápido y [sin dolores de cabeza](https://youtu.be/RfMkdvN-23o?feature=shared), podríamos usar un atajo: [Papa Parse –The powerful, in-browser CSV parser for big boys and girls](https://www.papaparse.com/).

Para usar el atajo, podríamos partir con algo como lo que sigue:

```
<script src="https://cdnjs.cloudflare.com/ajax/libs/PapaParse/5.4.1/papaparse.min.js" integrity="sha512-dfX5uYVXzyU8+KHqj8bjo7UkOdg18PaOtpa48djpNbZHwExddghZ+ZmzWT06R5v6NSk3ZUfsH6FNEDepLx9hPQ==" crossorigin="anonymous" referrerpolicy="no-referrer"></script>
<script>
Papa.parse("https://raw.githubusercontent.com/profesorfaco/dno097-2024/main/clase-04/sietes.csv", {
	download: true,
	header: true,
	dynamicTyping: true,
	complete: function(results) {
		console.log(results);
	}
});
</script>
```

Noten cómo vamos por un recurso en línea, y luego el *script* muestra una estructura bastante particular: Eso nos revela que este atajo es una bibliteca de JavaScript.

- - - - - - - - - - - - - - 

### Práctica (para la clase)

Pendiente.

- - - - - - - 

###### [← CLASE PREVIA](https://github.com/profesorfaco/dno097-2024/tree/main/clase-03) • [SIGUIENTE CLASE →](https://github.com/profesorfaco/dno097-2024/tree/main/clase-05)
