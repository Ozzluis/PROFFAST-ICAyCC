# Funcionamiento de PROFFAST v2.0.1

PROFFAST es un código de recuperación basado en el ajuste de mínimos cuadrados que ajusta las cantidades de gases traza escalando perfiles atmosféricos _a priori_. Este código está diseñado para espectros de absorción solar de baja resolución. 

Se divide en tres partes: PREPROCESS, PCXS y INVERS. Cada una de ellas tiene funciones distintas pero todas son necesarias para obtener los resultados deseados.

A continuación se muestra un diagrama de flujo sobre su funcionamiento. (ADJUNTAR DIAGRAMA, HACERLO.)

## PREPROCESS

Es la primera parte del procesamiento de datos, consiste en una precalibración de los espectros además de realizar correciones del DC (INFO), correciones de la Transformada de Fourier y correcciones de fase. 

Los inputs que requiere son: los interferogramas generados por OPUS, el parámetro ILS (_Instrumental Line Shape_), el nombre del sitio de mediciones*, datos del tiempo en que se realizó la medición, latitud, longitud y altitud de la estación de medición.

El producto que arroja son justamente los espectros pre-calibrados en su formato ___.bin___ que se almacenan en dos carpetas __SM__ y __SN__, donde el primero corresponde a los espectros en la región media del infrarrojo (_Mid-Infrared_) y el segundo a la región cercana (_Near-Infrared_). 


## PCXS

Se trata de un pre-cálculo de los cortes transversales de los gases que se quieran analizar (H2O, HDO, CO2, CH4, N2O, CO, O2, y HF). 

Los inputs que requiere son: 
  * los archivos VMR 
  * los archivos .map 
  * los datos de altitud, latitud, longitud y de presión
  * el archivo pT
    En este caso, el archivo pT coincide con el archivo _.map_ (ESCLARECER)
  * los espectros pre-calibrados del PREPROCESS

El producto que arroja es el archivo ___abscos.bin___, el cuál se requiere para ejecutar el código de INVERS.

## INVERS

Es la última parte del código de recuperación y consiste en la inversión para obtener los parámetros de los gases. (ESPECIFICAR)

Los inputs que requiere son:
  * los espectros SN pre-calibrados del PREPROCESS
  * el ___abscos.bin___ que se generó en el PCXS
  * la fecha y el nombre de la estación de medición
  * el pT file





* En ICAyCC se tienen diversos sitios de mediciones y están identificados por sus siglas: Vallejo, VAL; ICAyCC, CCA; Altzomoni, ALTZ; (COMPLETAR)
