#Explicación del procesamiento de datos

La obtención y manipulación de los datos se divide en dos partes: una parte in situ y otra de manera remota. 
En la siguiente imagen se puede apreciar un diagrama de flujo esto mismo.

##Primera parte de procesamiento

Esta parte consiste en la obtención de los datos físicamente y la ejecución del __preprocess__ de PROFFAST.

El EM2/SUN realiza mediciones cada minuto utilizando el programa OPUS; software que viene junto con dicho instrumento.
Dentro de OPUS se ejecuta un _macro_ que realiza tres funciones mediante scripts de pyhton:

* _pt_intraday_diaanterior.py_
    Este srcipt genera los archivos _pt_intraday_ los cuales INFORMACIÓN.
    Además, sube dichos archivos al servidor del ICAyCC junto con datos de  la latitud, longitud, altitud y nombre del sitio de medición.
    
* _preprocesscript.py_
    Ejecuta el _preprocess_ de PROFFAST, lo cuál hace que se creen los archivos ___.bin___ que son los espectros calibrados. (INFORMACIÓN)    
    
* _mandarOPUS.py_
    Manda los espectros calibrados al servidor del ICAyCC
