# Procesamiento de datos mediante PROFFAST 2

El procesamiento de los datos con PROFFAST 2 es diferente al de su antecesor pues mejora la eficiencia de la lectura y análisis de datos. Se requiere de un solo __input_file__ (en formato `.yml`)que va a contener toda la información necesaria para correr este algoritmo de recuperación. Además, dentro de este archivo, se va a poder: especificar el rango de días que se quieran medir o incluso procesaro todas las mediciones que se encuentren en una carpeta especificada, definir la ruta de los interferogramas, de los _map.files_, de los datos de presión; especificar la ruta donde se van a almacenar los resultados.

PROFFAST 2 provee de un `InputfileGenerator`, el cuál prepara un único inputfile para un instrumento y un lugar de medición en específico.


## Primera parte del procesamiento

Hace falta crear todo el ambiente en las computadoras de las estaciones de medición, es decir, todas las carpetas y alcualización de Python con las librerias correspondientes. Es importante poner aquí un diagrama de la estructura de las carpetas para que se sepan las rutas que se tienen sobre los archivos y scripts que se ejecutan.

En PROFFAST 1 no fue posible hacer esto debido a que había muchas carpetas de pormedio e incluso varios discos duros.

## Segunada parte del procesamiento

En la siguiente ruta es donde se realiza esta parte del procesamiento

```
/home/D3_EM27/PROFFAST/PROFFAST_2
```
