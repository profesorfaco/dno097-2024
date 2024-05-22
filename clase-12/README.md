### DESARROLLO WEB Y DISEÑO VISUAL DE INFORMACIÓN → Clase 12 → 22/05/2023

# Gráficas y datos en diseño web responsive SVG, HTML, CSS y JavaScript (primera parte)

### Teoría (para la casa)

Pendiente.

- - - - - - - - - - - - - - 

### Práctica (para la clase)

```
<!DOCTYPE html>
<html lang="es">
    <head>
        <meta charset="utf-8" />
        <meta name="viewport" content="width=device-width, initial-scale=1" />
        <title>Clase 12</title>
        <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.3/dist/css/bootstrap.min.css" rel="stylesheet" integrity="sha384-QWTKZyjpPEjISv5WaRU9OFeRpok6YctnYmDr5pNlyT2bRjXh0JMhjY6hW+ALEwIH" crossorigin="anonymous" />
        <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/chartist/0.11.4/chartist.min.css" integrity="sha512-V0+DPzYyLzIiMiWCg3nNdY+NyIiK9bED/T1xNBj08CaIUyK3sXRpB26OUCIzujMevxY9TRJFHQIxTwgzb0jVLg==" crossorigin="anonymous" referrerpolicy="no-referrer"/>
        <style>
            .ct-series-a .ct-bar,
            .ct-series-a .ct-line,
            .ct-series-a .ct-point,
            .ct-series-a .ct-slice-donut {
                stroke: rgb(158, 1, 66);
            }
            .ct-series-a .ct-area,
            .ct-series-a .ct-slice-donut-solid,
            .ct-series-a .ct-slice-pie {
                fill: rgb(158, 1, 66);
            }
            .ct-series-b .ct-bar,
            .ct-series-b .ct-line,
            .ct-series-b .ct-point,
            .ct-series-b .ct-slice-donut {
                stroke: rgb(219, 73, 74);
            }
            .ct-series-b .ct-area,
            .ct-series-b .ct-slice-donut-solid,
            .ct-series-b .ct-slice-pie {
                fill: rgb(219, 73, 74);
            }
            .ct-series-c .ct-bar,
            .ct-series-c .ct-line,
            .ct-series-c .ct-point,
            .ct-series-c .ct-slice-donut {
                stroke: rgb(248, 142, 83);
            }
            .ct-series-c .ct-area,
            .ct-series-c .ct-slice-donut-solid,
            .ct-series-c .ct-slice-pie {
                fill: rgb(248, 142, 83);
            }
            .ct-series-d .ct-bar,
            .ct-series-d .ct-line,
            .ct-series-d .ct-point,
            .ct-series-d .ct-slice-donut {
                stroke: rgb(254, 210, 129);
            }
            .ct-series-d .ct-area,
            .ct-series-d .ct-slice-donut-solid,
            .ct-series-d .ct-slice-pie {
                fill: rgb(254, 210, 129);
            }

            .ct-series-e .ct-bar,
            .ct-series-e .ct-line,
            .ct-series-e .ct-point,
            .ct-series-e .ct-slice-donut {
                stroke: rgb(251, 248, 176);
            }
            .ct-series-e .ct-area,
            .ct-series-e .ct-slice-donut-solid,
            .ct-series-e .ct-slice-pie {
                fill: rgb(251, 248, 176);
            }
            .ct-series-f .ct-bar,
            .ct-series-f .ct-line,
            .ct-series-f .ct-point,
            .ct-series-f .ct-slice-donut {
                stroke: rgb(213, 238, 159);
            }
            .ct-series-f .ct-area,
            .ct-series-f .ct-slice-donut-solid,
            .ct-series-f .ct-slice-pie {
                fill: rgb(213, 238, 159);
            }
            .ct-series-g .ct-bar,
            .ct-series-g .ct-line,
            .ct-series-g .ct-point,
            .ct-series-g .ct-slice-donut {
                stroke: rgb(137, 207, 165);
            }
            .ct-series-g .ct-area,
            .ct-series-g .ct-slice-donut-solid,
            .ct-series-g .ct-slice-pie {
                fill: rgb(137, 207, 165);
            }
            .ct-series-h .ct-bar,
            .ct-series-h .ct-line,
            .ct-series-h .ct-point,
            .ct-series-h .ct-slice-donut {
                stroke: rgb(70, 150, 179);
            }
            .ct-series-h .ct-area,
            .ct-series-h .ct-slice-donut-solid,
            .ct-series-h .ct-slice-pie {
                fill: rgb(70, 150, 179);
            }
            .ct-series-i .ct-bar,
            .ct-series-i .ct-line,
            .ct-series-i .ct-point,
            .ct-series-i .ct-slice-donut {
                stroke: rgb(94, 79, 162);
            }
            .ct-series-i .ct-area,
            .ct-series-i .ct-slice-donut-solid,
            .ct-series-i .ct-slice-pie {
                fill: rgb(94, 79, 162);
            }
        </style>
        <script src="https://cdnjs.cloudflare.com/ajax/libs/chartist/0.11.4/chartist.min.js" integrity="sha512-9rxMbTkN9JcgG5euudGbdIbhFZ7KGyAuVomdQDI9qXfPply9BJh0iqA7E/moLCatH2JD4xBGHwV6ezBkCpnjRQ==" crossorigin="anonymous" referrerpolicy="no-referrer"></script>
    </head>
    <body>
        <div class="container">
            <div class="row align-items-center">
                <div class="col-lg-8 pe-5">
                    <h2>Highest grossing movies in history</h2>
                    <img src="viz.svg" class="w-100" />
                </div>
                <div class="col-lg-4">
                    <div class="row ps-5">
                        <div class="col-12 col-sm-6 col-lg-12 py-3">
                            <h2 class="text-center fs-5">ROI</h2>
                            <div class="ct-chart1 ct-minor-second"></div>
                        </div>
                        <div class="col-12 col-sm-6 col-lg-12 py-3">
                            <h2 class="text-center fs-5">BOX OFFICE</h2>
                            <div class="ct-chart2 ct-minor-second"></div>
                        </div>
                    </div>
                </div>
                <div class="col-12">
                    <h2>Comparación promedios</h2>
                    <div class="ct-chart3"></div>
                </div>
            </div>
        </div>
        <script>
            new Chartist.Pie(
                ".ct-chart1",
                {
                    labels: ["Acción", "Aventura", "Animación", "Biogrfía", "Crimen", "Drama", "Familia", "Horror", "Musical"],
                    series: [13.681, 147.625, 81.77, 34.9, 42.8, 37.525, 75.5, 36.8, 66.2],
                },
                {
                    donut: true,
                    donutWidth: 60,
                    donutSolid: true,
                    startAngle: 270,
                    showLabel: true,
                }
            );
        </script>
        <script>
            new Chartist.Pie(
                ".ct-chart2",
                {
                    labels: ["Acción", "Aventura", "Animación", "Biogrfía", "Crimen", "Drama", "Familia", "Horror", "Musical"],
                    series: [1284.43, 754.125, 834.27, 286, 246, 879.75, 793, 441, 397],
                },
                {
                    donut: true,
                    donutWidth: 60,
                    donutSolid: true,
                    startAngle: 270,
                    showLabel: true,
                }
            );
        </script>
        <script>
            new Chartist.Bar(
                ".ct-chart3",
                {
                    labels: ["Acción", "Aventura", "Animación", "Biogrfía", "Crimen", "Drama", "Familia", "Horror", "Musical"],
                    series: [
                        [13.681, 147.625, 81.77, 34.9, 42.8, 37.525, 75.5, 36.8, 66.2],
                        [1284.43, 754.125, 834.27, 286, 246, 879.75, 793, 441, 397],
                    ],
                },
                {
                    axisX: {
                        // On the x-axis start means top and end means bottom
                        position: "start",
                    },
                    axisY: {
                        // On the y-axis start means left and end means right
                        position: "end",
                    },
                }
            );
        </script>
    </body>
    <footer class="bg-light">
        <div class="container py-3">
            <div class="row">
                <div class="col-10 mx-auto text-center fw-lighter">
                    <p>Cambie su nombre | Pontificia Universidad Católica de Chile.</p>
                </div>
            </div>
        </div>
    </footer>
</html>
```
- - - - - - - 

###### [← CLASE PREVIA](https://github.com/profesorfaco/dno097-2024/tree/main/clase-11) • [SIGUIENTE CLASE →](https://github.com/profesorfaco/dno097-2024/tree/main/clase-13)
