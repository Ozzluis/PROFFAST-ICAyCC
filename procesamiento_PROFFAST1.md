# Procesamiento de datos

La obtención y manipulación de los datos se divide en dos partes: una parte in situ y otra de manera remota. 
Se optó hacerlo de esta manera ya que el _preprocess_ no requiere de mucho recurso computacional a comparación de los otros dos procesos: _pcxs_ y _invers_.

## Primera parte de procesamiento

Esta parte consiste en la obtención de los datos físicamente y la ejecución del __preprocess__ de PROFFAST. A cpmtinuación se muestra un diagrama de flujo que representa gráficamente esta parte del procesamiento. 

![primer_diagrama](https://github.com/Ozzluis/PROFFAST-ICAyCC/blob/main/images/Diagrama_de_flujo_primera_parte.png)

El EM2/SUN realiza mediciones cada minuto utilizando el programa OPUS; software que viene junto con dicho instrumento.
Dentro de OPUS se ejecuta un _macro_ que realiza tres funciones mediante scripts de pyhton:

* _pt_intraday_diaanterior.py_

    Este srcipt genera los archivos _fecha_pT_intraday.inp_ los cuales proveen de información de la variabilidad del intradía de la presión y temperatura para el _invers_code_.
    También, sube al servidor los archivos _.dat_ que contienen información sobre las coordenadas del GPS y la hora de la medición en formato UTC.
    
* _preprocesscript.py_

    Ejecuta el _preprocess_ de PROFFAST, lo cuál hace que se creen los archivos ___.bin___ que son los espectros pre-calibrados y manda dichos archivos al servidor.   
    
* _mandarOPUS.py_

    Manda los espectros calibrados al servidor del ICAyCC
    
## Segunda parte del procesamiento

Esta parte se realiza en los servidores del ICAyCC y consiste en la obtención de los cortes transversales y la ejecución de la inversión para obtener las columnas promediadas de los gases.

__IMPORTANTE: Para acceder al servidor se requiere tener una cuanta en el mismo. El Dr. Alejandro Bezanilla puede proporcionala.__

![segundo_diagrama](https://github.com/Ozzluis/PROFFAST-ICAyCC/blob/main/images/Diagrama_de_flujo_segunda_parte.png)

En la siguiente ruta del servidor se ejecuta esta parte del procesamiento de datos:

```
/home/D3_EM27/PROFFAST
```
Para procesar un día de mediciones se corre el script `run_oneday_arg.sh`, cuyas variables de entrada son: [1] método, [2] sitio de la medición, [3] fecha (AAMMDD), [4] instrumento con el que se midió. Un ejemplo de dichas variables de entrada sería: `COCCON CCA 220325 EM27_62`. Donde COCCON es el método, CCA el sitio de medición, 220325 la fecha de la medición y EM27_62 es el instrumento con el que se midió. 

Este script va a preparar los input files __pcxs10.inp__ y __invers10.inp__ (mediante los sripts `setup_pcx10.py` y `setup_invers10.py` respectivamente) y va a ejecutar los programas __pcx10.exe__ y __invers10.exe__. El sript `setup_oneday.py` va a preparar todas las carpetas para almacenar los resultados que se generen de los programas PCX10 e INVERS.  

Además, se corren los scripts: `readresultproffast2h5.py`, `readcolsens.py` y `readspc2h5.py`. Éstos están diseñados para que los resultados generados se pasen a formato h5f, que es un formato binario de python.


