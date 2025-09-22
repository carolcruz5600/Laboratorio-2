# Laboratorio 2: Convolución correlación y transformada de Fourier

## Integrantes
* Laura Valentina Velásquez Castiblanco (5600846)
* Carol Valentina Cruz Becerra (5600845)
* Carlos Felipe Moreno Guzmán (5600881)
  
## Objetivos 
* Comprender la convolución como una operación que permite obtener la respuesta de un sistema discreto ante una entrada determinada.
* Analizar la correlación como medida de similitud entre dos señales.
* Aplicar la Transformada de Fourier como herramienta de análisis en eldominio de la frecuencia.

## Diagramas 

[Diagrama A](https://github.com/carolcruz5600/Laboratorio-2/blob/b72f20bfcba8161f8cfee12ca44652cfe5fb9744/Diagramas/Lab%202%20-%20PDS%20-%20Diagrama%20A.jpg)

[Diagrama B](https://github.com/carolcruz5600/Laboratorio-2/blob/b72f20bfcba8161f8cfee12ca44652cfe5fb9744/Diagramas/Lab%202%20-%20PDS%20-%20Diagrama%20B.jpg)

[Diagrama C](https://github.com/carolcruz5600/Laboratorio-2/blob/b72f20bfcba8161f8cfee12ca44652cfe5fb9744/Diagramas/Lab%202%20-%20PDS%20-%20Diagrama%20C.jpg)

## Parte A
En la parte A del laboratorio se desarrolló un código para implementar manualmente el algoritmo de convolución discreta. Para ello, se definieron las señales ``ℎ[𝑛]``, asociada al código estudiantil de cada integrante, y ``𝑥[𝑛]``, correspondiente a la cédula, como arreglos. Luego se programó la operación de convolución usando bucles anidados para calcular cada muestra ``𝑦[𝑛]=∑ℎ[𝑘]⋅𝑥[𝑛−𝑘]``. El código incluyó la implementación de la lógica para manejar los índices y límites de las sumatorias. Posteriormente, se generaron las gráficas de las señales originales ``ℎ[𝑛]`` y ``𝑥[𝑛]``, así como de la señal resultante ``𝑦[𝑛]`` de la convolución, utilizando matplotlib para visualizar tanto las señales de entrada como la respuesta del sistema, permitiendo analizar gráficamente el comportamiento temporal de la convolución.

[Parte A](https://github.com/carolcruz5600/Laboratorio-2/blob/main/Parte%20A/Proceso%20A.md)

## Parte B

Para esta parte del laboratorio se desarrolla el codigo necesario para poder calcular la correlación cruzada entre dos señales discretas. Para esto, se definireron las señales ``x[1]`` como una función coseno y ``x[2]`` relacionada con una función seno, ambas con nueve muestras y un periodo de 1.25ms. Estas señales se representaron en forma inicial como un vector y se graficaran en una sola figura. Luego se implementa en la programación un ciclo ``for`` para poder evaluar la sumatoria de la correlación cruzada dada por ``r12[𝑛]=∑ x1[n]⋅𝑥2[𝑛+𝑘]`` donde los diferentes retardos son representados por k que se aplican a la segunda señal. Los resultados obtenidos se organizan en vectores que a la vex fueron graficados para poder su análisis.

[Parte B](https://github.com/carolcruz5600/Laboratorio-2/blob/4c8f13584dadae05fd38445f36fef5a0659ee82e/Parte%20B/Proceso%20B.md)

## Parte C

En la parte C del laboratorio se trabajó con una señal EOG (electrooculografía) adquirida mediante el generador de señales biológicas. Con la ayuda del **NIDAQMX**, se digitalizó la señal con una frecuencia de muestreo $f_s=800 Hz$ para poder manipularla en el compilador de `Python`. Posteriormente, se caracterizó la señal en el dominio del tiempo mediante el cálculo de su media, mediana, desviación estándar y la determinación de su máximo y mínimo. Por último, se aplico la Transformada de Fourier (FFT), se determinó su Densidad Espectral de Potencia (PSD) y se realizaron sus respectivas gráficas para realizar un análisis en el dominio de la frecuencia, apoyado de estadísticos como la frecuencia media, la frecuencia mediana, la desviación estándar y el histograma de frecuencias.

[Parte C](https://github.com/carolcruz5600/Laboratorio-2/blob/main/Parte%20C/Proceso%20C.md)
