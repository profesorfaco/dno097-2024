### DESARROLLO WEB Y DISEÑO VISUAL DE INFORMACIÓN → Clase 07 → 17/04/2023


# Gráficas y datos en diseño web responsive: SVG

### Teoría (para la casa)

Partamos con un código largo, para repasar lo visto en clases previas:

```
<!DOCTYPE html>
<html lang="es">
    <head>
        <meta charset="utf-8" />
        <meta name="viewport" content="width=device-width, initial-scale=1" />
        <title>Partiendo la sexta clase</title>
        <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.3/dist/css/bootstrap.min.css" rel="stylesheet" integrity="sha384-QWTKZyjpPEjISv5WaRU9OFeRpok6YctnYmDr5pNlyT2bRjXh0JMhjY6hW+ALEwIH" crossorigin="anonymous" />
        <style>
            body {color: #06122c;}
            em {font-style: normal; font-weight: bold; text-decoration: underline;}
            span {font-weight: bold;}
        </style>
    </head>
    <body>
        <svg xmlns="http://www.w3.org/2000/svg" class="d-none">
            <symbol id="pdf" viewBox="0 0 16 16">
                <path fill-rule="evenodd" d="M14 4.5V14a2 2 0 0 1-2 2h-1v-1h1a1 1 0 0 0 1-1V4.5h-2A1.5 1.5 0 0 1 9.5 3V1H4a1 1 0 0 0-1 1v9H2V2a2 2 0 0 1 2-2h5.5zM1.6 11.85H0v3.999h.791v-1.342h.803q.43 0 .732-.173.305-.175.463-.474a1.4 1.4 0 0 0 .161-.677q0-.375-.158-.677a1.2 1.2 0 0 0-.46-.477q-.3-.18-.732-.179m.545 1.333a.8.8 0 0 1-.085.38.57.57 0 0 1-.238.241.8.8 0 0 1-.375.082H.788V12.48h.66q.327 0 .512.181.185.183.185.522m1.217-1.333v3.999h1.46q.602 0 .998-.237a1.45 1.45 0 0 0 .595-.689q.196-.45.196-1.084 0-.63-.196-1.075a1.43 1.43 0 0 0-.589-.68q-.396-.234-1.005-.234zm.791.645h.563q.371 0 .609.152a.9.9 0 0 1 .354.454q.118.302.118.753a2.3 2.3 0 0 1-.068.592 1.1 1.1 0 0 1-.196.422.8.8 0 0 1-.334.252 1.3 1.3 0 0 1-.483.082h-.563zm3.743 1.763v1.591h-.79V11.85h2.548v.653H7.896v1.117h1.606v.638z"/>
            </symbol>
        </svg>
        <div class="container">
            <div class="row">
                <div class="col-md-10 col-lg-9 col-xl-8 my-5 mx-auto">
                    <h1 class="ms-2">DISEÑO UC</h1>
                    <p class="ms-2">Considerando sólo <em>memorias de Proyecto de Título</em>:</p>
                    <ul class="mb-5 ms-2">
                        <li>clasificada en ámbitos que incluyan los caracteres "<span id="criterio"></span>";</li>
                        <li>con PDF disponible; y</li>
                        <li>con nota de título que sea igual o mayor a 6.</li>
                    </ul>
                    <h2 class="fs-4 ms-2 mb-3"><a href="https://www.visual-literacy.org/periodic_table/periodic_table.html" title="Data Visualization → Structure Visualization → Detail AND Overview → Convergente thinking" target="_blank" class="link-dark">Tabla</a></h2>
                    <div class="table-responsive">
                        <table class="table table-light table-hover small">
                            <thead class="table-primary">
                                <tr>
                                    <th scope="col" class="text-center">#</th>
                                    <th scope="col" style="width: 20%;">Autor(a)</th>
                                    <th scope="col">Año</th>
                                    <th scope="col" style="width: 40%;">Título</th>
                                    <th scope="col">Ámbito</th>
                                    <th scope="col">Prof. Guía</th>
                                    <th scope="col" class="text-center">Nota</th>
                                </tr>
                            </thead>
                            <tbody></tbody>
                        </table>
                    </div>
                    <h2 class="fs-4 mt-5 ms-2 mb-3"><a href="https://www.visual-literacy.org/periodic_table/periodic_table.html" title="Data Visualization → Structure Visualization → Overview → Convergent thinking" target="_blank" class="link-dark">Barras</a></h2>
                    <p class="ms-2">Se toman los datos de la tabla de arriba para calcular una nota promedio para los títulos guiados por cada Profesor(a) Guía. A continuación sólo se muestran las notas promedios que están en o por sobre el promedio general de <span id="corte"></span></p>
                    <svg id="aqui"></svg>
                    <h2 class="fs-4 mt-5 ms-2 mb-3">Palabras</h2>
                    <p class="ms-2">Ahora se reúnen todos los "para qué" de los proyectos en la tabla y se buscan en lo reunido las palabras más repetidas (descartando artículos, adverbios, preposiciones y conjunciones).</p>
                    <ul id="palabreo"></ul>
                </div>
            </div>
        </div>
        <script>
            //Puede cambiar el criterio
            const criterio = "Bienestar";
            document.querySelector("#criterio").innerHTML = criterio;
            //Para tomar el tbody
            const aqui = document.querySelector("tbody");
            //Para tomar el svg
            const visualizacion = document.querySelector("#aqui");
            //Para jugar un poco con los datos
            var seleccion = [];
            var profes = [];
            var nombres = [];
            var barras = [];
            //Todo lo que sigue es una función
            async function datos() {
                const consulta = await fetch("https://raw.githubusercontent.com/profesorfaco/dno097-2024/main/clase-06/data.json");
                const data = await consulta.json();
                console.log("Lo que sigue son todos los datos:");
                console.log(data);
                //Trabajando con 1400 elementos en el arreglo
                data.forEach((d) => {
                    d.nota_titulo = parseFloat(d.nota_titulo.replace(",", "."));
                    d.nota_pga = parseFloat(d.nota_pga.replace(",", "."));
                    d.nota_seminario = parseFloat(d.nota_seminario.replace(",", "."));
                    d.year = Number(d.year);
                    d.pdf_ok = Number(d.pdf_ok);
                    if (d.ambito.includes(criterio) && d.pdf_ok == 1 && d.nota_titulo >= 6) {
                        seleccion.push(d);
                    }
                });
                console.log("Lo que sigue es una selección de los datos:");
                console.log(seleccion);
                //Trabajando con una selección
                seleccion.forEach((s, i) => {
                    aqui.innerHTML += `<tr><td class="text-center">${i + 1}</td><td>${s.nombre_paterno} ${s.nombre_materno}, ${s.nombre_pila[0]}.</td><td>${s.year}</td><td><a href="https://diseno.uc.cl/memorias/pdf/${s.nombre_pdf}" class="link-dark">${s.nombre_proyecto}</a> <svg width="1em" height="1em"><use href="#pdf"></use></svg></td><td>${s.ambito}</td><td>${s.nombre_guia}</td><td class="text-center">${s.nota_titulo.toFixed(1)}</td></tr>`;
                    let obj = {};
                    obj["prof"] = `${s.nombre_guia}`;
                    obj["nota"] = `${s.nota_titulo.toFixed(1)}`;
                    profes.push(obj);
                    nombres.push(s.nombre_guia);
                });
                /*
                    En el seleccion.forEach hago 3 cosas
                    1ra. lleno el tbody
                    2da. empujo objetos a la variable profes
                    3ra. empujo strings a la variable nombres
                */
                console.log("Lo que sigue son nombres de profes y notas asociadas en la selección:");
                console.log(profes);
                nombres = [...new Set(nombres)].sort();
                console.log("Lo que sigue son sólo los nombres, sin repetir, de los profes:");
                console.log(nombres);
                //Basándome en nombres, trabajo con profes 
                nombres.forEach((x) => {
                    //prof sin repetir
                    let unProf = profes.filter((p) => p.prof === x);
                    //promedio de notas de cada prof
                    let average = unProf.reduce((a, b) => a + Number(b.nota), 0) / unProf.length;
                    let obj = {};
                    obj["prof"] = x;
                    obj["promedio"] = Number(average);
                    barras.push(obj);
                });
                console.log("Lo que sigue son promedios para cada nombre:");
                console.log(barras);
                //Forma más "clásica" de sacar promedio
                var i = 0;
                var total = 0;
                barras.forEach(barra => {total += barra.promedio; i++;});
                var corte = total / i;
                document.querySelector("#corte").innerHTML = corte.toFixed(2);
                var ajuste = 0;
                let mayor = 0;
                barras.forEach((x) => {
                    mayor = Math.max(mayor, x.promedio);
                    if (x.promedio >= corte) {
                        visualizacion.innerHTML += `<g transform="translate(0 ${ajuste * 3})"><rect x="0" y="0" height="2" width="70" fill="#eee"></rect><rect x="0" y="0" height="2" width="${x.promedio.toFixed(1) * 10}" fill="#3274d7"></rect><text fill="white" font-size="1.2" x="0.5" y="1.4">${x.prof}</text><text fill="#06122c" font-size="1.2" x="${x.promedio.toFixed(1) * 10 - 2.5}" y="1.4">${x.promedio.toFixed(1)}</text></g>`;
                        ajuste++;
                    }
                });
                visualizacion.innerHTML += `<line x1="${mayor.toFixed(1) * 10}" y1="0" x2="${mayor.toFixed(1) * 10}" y2="${ajuste * 3}" stroke="white" stroke-width="0.1"/>`;
                var proporcion = "0 0 70 " + ajuste * 3;
                visualizacion.setAttribute("viewBox", proporcion);
                //Buscando las palabras frecuentes del "para qué" en su selección 
                var words = "";
                seleccion.forEach(s => words = words + " " + s.para_que);
                var palabras = words.split(" ");
                palabras = palabras.sort();
                const nopalabras = ["","a","al","como","con","de","del","desde","e","el","en","entre","esta","este","esto","hacia","la","las","lo","los","más","mediante","no","o","para","por","que","se","sobre","su","sus","tanto","través","un","una","unas","unos","y"];
                const sacaPalabras = (arreglo, sacar) => {
                    return arreglo.filter((palabra) => {
                        return !sacar.includes(palabra);
                    });
                };
                var palabrasAcotadas = sacaPalabras(palabras, nopalabras);
                const cuentaRepeticiones = (arreglo = []) => {
                    const resultado = [];
                    arreglo.forEach((el) => {
                        const index = resultado.findIndex((obj) => {
                            return obj["name"] === el;
                        });
                        if (index === -1) {
                            resultado.push({
                                name: el,
                                count: 1,
                            });
                        } else {
                            resultado[index]["count"]++;
                        }
                    });
                    return resultado;
                };
                var total = cuentaRepeticiones(palabrasAcotadas);
                total.forEach((x) => {
                    if (x.count > 2) {
                        document.querySelector("#palabreo").innerHTML += `<li>${x.name} (${x.count})</li>`;
                    }
                });
            }
            //Acá se echa a correr la función
            datos().catch((error) => console.error(error));
        </script>
    </body>
</html>
```

Se recomienda que peguen y copien el código fuente en un `index.html`, lo guarden y revisen el resultado en su navegador web, con atención a lo que se imprime en la consola de JavaScript.

Después de ver el resultado, vuelvan al código fuente e intenten leerlo de principio a fin, diferenciando:

- HTML
- SVG
- CSS
- JavaScript

Haciendo esa diferencia no habría problemas con la siguiente instrucción: En la primera línea del script, cambie el contenido de la variable-constante de nombre `criterio` por la cadena de caracteres que utilizó en el ejercicio de la clase recién pasada.

Aprovechando la diferencia hecha, y manteniéndonos en el script, resulta evidente de que la parte más extensa del código está escrita en JavaScript, el único lenguaje de programación entre los que diferenciamos en la página; porque fueron necesarias muchas instrucciones después del [`fetch()`](https://developer.mozilla.org/es/docs/Web/API/Fetch_API/Using_Fetch) de un único [JSON](https://www.json.org/json-es.html) con demasiados "datos duros" que acotamos con ciertos criterios, para luego llenar nuevas variables, limpiar redundancias, sacar promedios, etc.

Pero no siempre serán necesarias tantas instrucciones. Pueden ser muchas menos si preparamos conjuntos de datos acotados, para luego intercambiar mediante formatos tales como JSON o CSV. 

La manera de acotar los conjuntos de datos puede estar en función de las visualizaciones por generar y modo de uso como conjunto, hasta tomar dos vías distintas que podríamos caracterizar como:

- Infografías digitales, interactivas y dinámicas, como las de https://www.reuters.com/graphics/; o

- Tableros de información (dashboards), como los de https://themes.getbootstrap.com/product-category/admin-dashboard/

Las primeras ofrecen títulos, subtítulos y párrafos, que se intercalan con visualizaciones figurativas o no figurativas, para desplegar un asunto en la medida que se hace *scroll down*. 

Las segundas reducen al mínimo el uso de textos, para ofrecer visualizaciones no figurativas en las que se despliega el estado de las variables necesarias para evaluar cierto asunto *at a glance* y sin *scroll*.

Un trabajo de infografía digital sobre las memorias clasificadas en un determinado ámbito podría verse distinto de un tablero de información para la elección de Prof. Guía. Pero los lenguajes, dialectos y formatos utilizados en el desarrollo de ambas pueden ser los mismos: HTML, CSS y JavaScript serían los lenguajes; SVG el dialecto; CSS y JSON los formatos.

- - - - - - - - - - - - - - 

### Práctica (para la clase)

En el mismo código de la teoría, pongamos atención a la parte que dice 

```
<svg xmlns="http://www.w3.org/2000/svg" class="d-none">
<symbol id="pdf" viewBox="0 0 16 16">
<path fill-rule="evenodd" d="M14 4.5V14a2 2 0 0 1-2 2h-1v-1h1a1 1 0 0 0 1-1V4.5h-2A1.5 1.5 0 0 1 9.5 3V1H4a1 1 0 0 0-1 1v9H2V2a2 2 0 0 1 2-2h5.5zM1.6 11.85H0v3.999h.791v-1.342h.803q.43 0 .732-.173.305-.175.463-.474a1.4 1.4 0 0 0 .161-.677q0-.375-.158-.677a1.2 1.2 0 0 0-.46-.477q-.3-.18-.732-.179m.545 1.333a.8.8 0 0 1-.085.38.57.57 0 0 1-.238.241.8.8 0 0 1-.375.082H.788V12.48h.66q.327 0 .512.181.185.183.185.522m1.217-1.333v3.999h1.46q.602 0 .998-.237a1.45 1.45 0 0 0 .595-.689q.196-.45.196-1.084 0-.63-.196-1.075a1.43 1.43 0 0 0-.589-.68q-.396-.234-1.005-.234zm.791.645h.563q.371 0 .609.152a.9.9 0 0 1 .354.454q.118.302.118.753a2.3 2.3 0 0 1-.068.592 1.1 1.1 0 0 1-.196.422.8.8 0 0 1-.334.252 1.3 1.3 0 0 1-.483.082h-.563zm3.743 1.763v1.591h-.79V11.85h2.548v.653H7.896v1.117h1.606v.638z"/>
</symbol>
</svg>
```

Y cambiemos el path contenido en tal tal símbolo por uno distinto, que pueden tomar de https://icons.getbootstrap.com/, https://feathericons.com/, https://www.svgrepo.com/ o, incluso, https://www.guemil.info/icons/ 

Al hacer el cambio, pongan mucha atención a la diferencia que podría haber entre el `viewBox` del SVG que toman y el `viewBox` del `<symbol></symbol>`.

**Una vez hecho el cambio, demos un salto con atención a las siguientes instrucciones**:

Dentro del `<head></head>`, agregar:

```
<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/chartist/0.11.4/chartist.min.css" />
<script src="https://cdnjs.cloudflare.com/ajax/libs/chartist/0.11.4/chartist.min.js"></script>
```
        
Dentro del `<style></style>`, que está dentro de `<head></head>`, agregar:

```
.ct-series-a .ct-bar {stroke: #3274d7;}
```

Justo debajo del `<svg></svg>` de identidad `aqui`, agregar:

```
<div class="ct-chart"></div>
```

Y después del cierre del largo `<script></script>`, agregar un segundo, mucho más breve:

```
<script>
    new Chartist.Bar(
        ".ct-chart",
        {
            labels: ["Cancino", "Duran", "Ulibarri", "Villela"],
            series: [[7.0, 6.7, 6.6, 6.8]],
        },
        {
            reverseData: true,
            horizontalBars: true,
            axisY: {
                offset: 75,
            },
        }
    );
</script>
```

**El resultado debería mostrarles un gráfico de barras construido con [Chartist.js](https://gionkunz.github.io/chartist-js/index.html)**


- - - - - - - 

###### [← CLASE PREVIA](https://github.com/profesorfaco/dno097-2024/tree/main/clase-06) • [SIGUIENTE CLASE →](https://github.com/profesorfaco/dno097-2024/tree/main/clase-08)
