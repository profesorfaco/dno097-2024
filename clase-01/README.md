### DESARROLLO WEB Y DISEÑO VISUAL DE INFORMACIÓN → Clase 01 → 06/03/2023

# Datos e información

### Teoría (para la casa)

El título dice, entre paréntesis, “para la casa”. La razón de lo dicho está en la apuesta por el aprendizaje invertido. La explicación de la apuesta la encuentran en esta página del [Centro de Desarrollo Docente UC](https://desarrollodocente.uc.cl/servicios/asesorias-personalizadas/metodologias-innovadoras/aprendizaje-invertido/). Pero, en su apuesta, este optativo hace un ajuste: No se basa en videos de contenido, sino en hipertexto que, en algunas clases, podría vincular a videos.

--------

En este optativo es necesario que, en su partida, cada estudiante pueda leer-comprender lo que sigue: 

```
<!doctype html>
<html lang="es">
  <head>
    <meta charset="utf-8">
    <meta name="viewport" content="width=device-width, initial-scale=1">
    <title>Podríamos usar Bootstrap</title>
    <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.2/dist/css/bootstrap.min.css" rel="stylesheet" integrity="sha384-T3c6CoIi6uLrA9TneNEoa7RxnatzjcDSCmG1MXxSR1GAsXEV/Dwwykc2MPK8M2HN" crossorigin="anonymous">
  </head>
  <body>
    <div class="container-fluid m-0 p-0">
      <div class="row row-cols-2 g-0" style="height:100vh">
        <div class="h-100 bg-danger d-flex align-items-center justify-content-center">
          <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 100 100">
            <g id="primera"></g>
          </svg>
        </div>
        <div class="h-100 bg-success d-flex align-items-center justify-content-center">
          <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 100 100">
            <g id="segunda"></g>
          </svg>          
        </div>
      </div>
    </div>
    <script>
      const data = [50,10];
      let cero = document.querySelector("#primera");
      cero.innerHTML = `<circle cx="50" cy="50" r="${data[0]}" />`;
      let uno = document.querySelector("#segunda");
      uno.innerHTML = `<circle cx="50" cy="50" r="${data[1]}" />`;
    </script>
  </body>
</html>
```
Si se lo comprende, podremos dar el primer paso concentrándonos en la variable-constante `data`, a la que se le asigna un arreglo con **dos números enteros que, de momento, no tienen sentido**: No tenemos su origen ni su destino, pero los tenemos a la vista siendo el primero, convencionalmente, cinco veces el segundo.

Examinemos lo del párrafo anterior, partiendo por las primeras acepciones de Data, en inglés:

- [plural in form but singular or plural in construction] *factual information (such as measurements or statistics) used as a basis for reasoning, discussion, or calculation* —Merrian-Webster Dictionary.

- [uncountable, plural] *facts or information, especially when examined and used to find out things or to make decisions* —Oxford dictionary.

50 y 10 no nos permiten razonamiento, discusión, cálculo o toma de decisión más allá de la convencional multiplicación. Convencional porque nos exige adoptar convenios o pactos sobre símbolos como números y operaciones matemáticas. No es un hecho (*fact*) que 50 sea 5 veces 10. Si es un convenio o pacto adoptado (ver convenional en [RAE](https://dle.rae.es/convencional)).

Falta conectar a 50 y 10 con un *fact* para tener *data*. Esa conexión exige un camino, y el camino debería tener un sentido tal como en el tránsito; hay un sentido en el estar dirigido para poder recortar “algo” que siempre está en el medio de algo más, que forma parte de un “campo” (Merleau-Ponty, 2010).

Pero no es tan conveniente profundizar ahora en cuestiones "fenomenológicas", como sí es conveniente revisar la idea del DIKW (Data → Information → Knowledge → Wisdom) con dos artículos:

- van Meter, H. J. (2020). Revising the DIKW pyramid and the real relationship between data, information, knowledge, and wisdom. Law, Technology and Humans, 2(2), 69–80. https://search.informit.org/doi/10.3316/agispt.20210112042035

- McDowell, K. (2021). Storytelling wisdom: Story, information, and DIKW. JASIST, Journal of the ASsociation for Information Science and Technology, 72 (10), 1223-1233. https://asistdl.onlinelibrary.wiley.com/doi/full/10.1002/asi.24466

Allí está la base para comenzar a trabajar un concepto propio de información, que es lo que cada estudiante diseñará visualmente con herramientas como las que ya se muestran en el código de más arriba.

- - - - - - - - - - - - - - 

### Práctica (para la clase)

Conectemos los números de arriba con un *fact* para tener *data*. Los números pueden cambiar (no es necesario que sea 50 y 10).

Luego aprovechemos: 

- el código fuente de la página de https://www.guemil.info/meaning/ 

- las instrucciones en https://heyoka.medium.com/scratch-made-svg-donut-pie-charts-in-html5-2c587e935d72

para convertir los números en porcentajes (partes de un total de 100) que se muestre en un [Gráfico de Dónut](https://datavizcatalogue.com/ES/metodos/grafico_de_donut.html), reconociendo sus ventajas y desventajas.

Los resultados deben publicarse en un repositorio de GitHub, para el que se debe activar la GitHub Pages.

Luego ingrese datos a https://cursos.canvas.uc.cl/courses/73175/discussion_topics/742764

Con lo ingresado, se rellena la siguiente tabla:

| N° | Nombre | Github | Primer ejercicio |
|:----:|:------|:------|:------|
| 1 | ISIDORA ARRIAGADA | https://github.com/isidjan/ | https://isidjan.github.io/dnoweb097/ |
| 2 | TRINIDAD FORSTER | https://github.com/Trinidad-Forster/ | https://trinidad-forster.github.io/C1_06-03/ |
| 3 | TAHIS FUENTES | https://github.com/tafucita/ | https://tafucita.github.io/clase-1/ |
| 4 | SARA GOLDZVEIG | https://github.com/saragoldzveig/ | https://saragoldzveig.github.io/clase-01/ |
| 5 | JOSEFINA IMSCHENETZKY | https://github.com/jimschenetzky/ | https://github.com/jimschenetzky/DNOWEB_01 |
| 6 | JAVIERA MOLIN | https://github.com/javimolin-uc/ | https://javimolin-uc.github.io/C1/ |
| 7 | ISIDORA MUÑOZ | https://github.com/Isidoramunoz/ | https://isidoramunoz.github.io/dnoweb/ |
| 8 | VALENTINA NAVARRETE | https://github.com/valenavarrete/ | https://valenavarrete.github.io/Clase-1/ |
| 9 | TRINIDAD RODRÍGUEZ | https://github.com/trinirodriguez/ | https://trinirodriguez.github.io/dno-01/ |
| 10 | CATALINA SEGUEL | https://github.com/cataseguel/ | https://cataseguel.github.io/Clase-01-DNO097/ |
| 11 | FRANCISCA SOTO | — | - |
| 12 | MARÍA ANGÉLICA VALDÉS | — | - |
| 13 | CAMILA VALLEJO | https://github.com/Camivallejo | https://camivallejo.github.io/clase_01_web/ |

- - - - - - - 

###### [SIGUIENTE CLASE →](https://github.com/profesorfaco/dno097-2024/tree/main/clase-02)
