### DESARROLLO WEB Y DISEÑO VISUAL DE INFORMACIÓN → Clase 06 → 10/04/2023

# Formatos ligeros de intercambios de datos en la creación de gráficas: JSON (segunda parte)

### Teoría

Como es la segunda parte del JSON, en esta ocasión no tenemos teoría. Vamos directo a la práctica.

- - - - - - - - - - - - - - 

### Práctica (para la clase)

Partamos con un código, que se pega en un `index.html`:

```
<!DOCTYPE html>
<html lang="es">
    <head>
        <meta charset="utf-8" />
        <meta name="viewport" content="width=device-width, initial-scale=1" />
        <title>Partiendo la quinta clase</title>
        <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.3/dist/css/bootstrap.min.css" rel="stylesheet" integrity="sha384-QWTKZyjpPEjISv5WaRU9OFeRpok6YctnYmDr5pNlyT2bRjXh0JMhjY6hW+ALEwIH" crossorigin="anonymous" />
        <style>
            image {
                filter: grayscale(1);
                opacity: 0.3;
            }
        </style>
    </head>
    <body>
        <div class="container">
            <div class="row">
                <div class="col">
                    <!--hagamos una tabla-->
                </div>
            </div>
        </div>
        <script>
            var seleccion = [];
            async function datos() {
                const consulta = await fetch("https://raw.githubusercontent.com/profesorfaco/dno097-2024/main/clase-06/data.json");
                const data = await consulta.json();
                console.log(data);
                data.forEach(d => {
                    if(d.ambito == "Educación" && d.pdf_ok !== "0"){
                        seleccion.push(d)
                    }
                });
                console.log(seleccion);
            }
            datos().catch((error) => console.error(error));
        </script>
    </body>
</html>
```

Nótese que hay un `if()` que tiene un `&&` que significa "y", de esto y esto también.

- - - - - - - 

###### [← CLASE PREVIA](https://github.com/profesorfaco/dno097-2024/tree/main/clase-05) • [SIGUIENTE CLASE →](https://github.com/profesorfaco/dno097-2024/tree/main/clase-07)
