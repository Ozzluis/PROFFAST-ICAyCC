# Procesamiento de datos

La obtención y manipulación de los datos se divide en dos partes: una parte in situ y otra de manera remota. 
Se optó hacerlo de esta manera ya que el _preprocess_ no requiere de mucho recurso computacional a comparación de los otros dos procesos: _pcxs_ y _invers_.

## Primera parte de procesamiento

Esta parte consiste en la obtención de los datos físicamente y la ejecución del __preprocess__ de PROFFAST. A cpmtinuación se muestra un diagrama de flujo que representa gráficamente esta parte del procesamiento. 

![primer_diagrama](/PROFFAST-ICAyCC/images/primer_diagrama.png)

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

Esta parte se realiza en los servidores del ICAyCC y consiste en la obtención de los cortes transversales y la ejecución de la inversión para obtener las concentraciones. (MUCHA MÁS INFORMACIÓN)

__IMPORTANTE: Para acceder al servidor se requiere tener una cuanta en el mismo. El Dr. Alejandro Bezanilla puede proporcionala.__

Se ejecutan NUMEROS de scripts para ejecutar el _pcxs_ y el _invers_ de PROFFAST.
