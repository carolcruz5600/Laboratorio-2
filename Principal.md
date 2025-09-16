# Laboratorio 2: Convolución correlación y transformada de Fourier

## Integrantes
* Laura Valentina Velásquez Castiblanco (5600846)
* Carol Valentina Cruz Becerra (5600845)
* Carlos Felipe Moreno Guzmán (5600881)
  
## Objetivos 
* Comprender la convolución como una operación que permite obtener la respuesta de un sistema discreto ante una entrada determinada.
* Analizar la correlación como medida de similitud entre dos señales.
* Aplicar la Transformada de Fourier como herramienta de análisis en eldominio de la frecuencia.
  
## Parte A
En la parte A del laboratorio se desarrolló un código para implementar manualmente el algoritmo de convolución discreta. Para ello, se definieron las señales ℎ[𝑛], asociada al código estudiantil de cada integrante, y 𝑥[𝑛], correspondiente a la cédula, como arreglos.Luego se programó la operación de convolución usando bucles anidados para calcular cada muestra 𝑦[𝑛]=∑ℎ[𝑘]⋅𝑥[𝑛−𝑘]. El código incluyó la implementación de la lógica para manejar los índices y límites de las sumatorias. Posteriormente, se generaron las gráficas de las señales originales ℎ[𝑛] y 𝑥[𝑛], así como de la señal resultante 𝑦[𝑛] de la convolución, utilizando matplotlib para visualizar tanto las señales de entrada como la respuesta del sistema, permitiendo analizar gráficamente el comportamiento temporal de la convolución.

[[Parte A](https://github.com/carolcruz5600/Laboratorio-2/blob/main/Parte%20A/Proceso%20A.md)

