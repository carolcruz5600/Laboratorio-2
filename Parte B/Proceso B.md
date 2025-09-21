# Parte B - Resultados

Al igual que en la parte B se necesitan el uso de librerias para poder realizar los vectores de manera matemática, las gráficas, WFDB para leer señales médicas, SciPy para estadísticas avanzadas y Seaborn se emplea para generar visualizaciones estadísticas claras y estilizadas.

<p align="center">
<img width="805" height="221" alt="image" src="https://github.com/user-attachments/assets/68cd83af-da99-4794-b43c-d39980a7d110" />
</p>

## Definición de Vectores

En esta parte  del código se definen las señales discretas que se utilizaran en la correlación cruzada. Primero se activa la impresión en formato matemático con el ``init_printing(use_latex=True)``, esto permite mostrar las expresiones de forma más clara, ordenada y en manera de vector, luego se declara la variable ``n``, junto con el período de muestreo ``Ts=1.25*10**-3s`` que se utilizaran para las muestras de las funciones trigonométricas.

Posterior, se definen las funciones ``x1`` y ``x2``, cada una con nueve muestras. La señal ``x1[n]`` corresponde a un coseno definido como ``cos (2*π*100*n*Ts)`` para n en un rango de ``0 <= n < 9``, mientras que la señal ``x2[n]`` corresponde a un seno definido ``sen (2*π*100*n*Ts)``. Al finalizar con las funciones de  ``Matrix(x1)`` y  ``Matrix(x2)`` se muestran los resultados de las funciones en formato de vector, lo que facilita su visualización. 

<p align="center">
<img width="793" height="588" alt="image" src="https://github.com/user-attachments/assets/2cf6a5dc-b5b3-4fda-b534-fe41a91d7620" />
</p>

### Resultados funciones
``x1`` y ``x2``
<p align="center">
<img width="169" height="335" alt="image" src="https://github.com/user-attachments/assets/838c6a55-ae1c-4131-ac05-c29ceaa37ebc" />
<img width="169" height="336" alt="image" src="https://github.com/user-attachments/assets/d7c216fc-32d5-4909-b4a0-624ddf537ab0" />
</p>

## Gráfica de las funciones

Para esta parte se realiza las conversiones de los valores que se tenian en simbolos por **SymPy** a valores numéricos udando **NumPy** para que se puedan graficar las señales. Transformando primero las funciones ``x1`` y ``x2`` y guardandolas en un arreglo con las definiciones de ``x1_numeric`` y ``x2_numeric`` a la vez se hace un arreglo numérico ``n_numeric`` que corresponde a los numeros de las muestras ya luego se realizan las funciones necesarias para obdervar las dos funciones con diferentes tipos de lineas y colores.

<p align="center">
<img width="587" height="257" alt="image" src="https://github.com/user-attachments/assets/90bfbed9-f38d-4362-9f4d-fdd71e18d508" />
</p>

Como se puede observar en la gráfica las señales tienen un desfase de ``π/2`` lo que sirve para analizar que cuando alcanzan los valores mínimos y máximos no son al mismo tiempo. Cuando ``x1`` alcanza sus valores maximos ``x2`` se encuentra en cero y de manera viceversa comprobando la separación de las señales.

<p align="center">
<img width="587" height="457" alt="image" src="https://github.com/user-attachments/assets/8e37c6b2-cfb4-4a5c-b4f9-240befab4b57" />
</p>

## Correlación Cruzada Manual

La correlación se utiliza para saber la similitud que se encuentran en dos señales a partir de que una de las señales se desplace respecto a un retardo k. Se define mediante la sumatoria:

<p align="center">
<img width="379" height="90" alt="image" src="https://github.com/user-attachments/assets/5233bdea-0247-474f-aeaa-984aa13fa498" />
</p>

En esta parte del código se implementa el cálculo manual para la correlación cruzada de las dos señales, mediante un ciclo for se logra calcular la sumatoria que multiplica y va acumulando las muestras de cada señal en el desplazamiento. De esta forma se obtuvo la secuencia de ``r12[k]``, esto es importante ya que ayuda a identificar patrones o desfases en as señales.

### Resultados 

``x1[n]`` ``x2[n]`` ``Correlación Cruzada``
<p align="center">
<img width="169" height="335" alt="image" src="https://github.com/user-attachments/assets/79ee4667-e335-4a37-b24f-9d6fca4eb94d" />
<img width="169" height="335" alt="image" src="https://github.com/user-attachments/assets/20736cd2-cef1-42e9-ac58-5604cd196d92" />
<img width="169" height="335" alt="image" src="https://github.com/user-attachments/assets/e3338aab-a0b4-4597-8423-f5af531e25d3" />
</p>

## Gráfica Correlación 

Ya aqui se utilizan las funciones de MatPlot para poder mostrar la grafica, se representan primero la secuencia de los valores de acuerdo al retardo, luego se definen los nombres de los ejes X y Y a la vez se le agrega el titulo y se muestra la gráfica.
<p align="center">
<img width="793" height="588" alt="image" src="https://github.com/user-attachments/assets/52bf31bb-a1ad-4818-a595-8c20a1028297" />
</p>

Se observa que los valores de la correlación toman tanto positivos como negativos, lo que indica que las señales tienen momentos de alta similitud (picos positivos) y momentos de oposición (picos negativos) según el desplazamiento aplicado. El hecho de que la gráfica no tenga un valor máximo pronunciado en k=0 se debe a que coseno y seno son funciones ortogonales, es decir, no coinciden en fase y su similitud inmediata es baja. Los valores más altos aparecen en retardos distintos de cero, lo que significa que al desplazar una señal respecto a la otra, en ciertos puntos se alinean parcialmente generando correlación positiva, mientras que en otros se encuentran en oposición, resultando en correlación negativa. Esto refleja cómo la correlación cruzada permite analizar la relación de fase y semejanza entre señales.

<p align="center">
<img width="565" height="455" alt="image" src="https://github.com/user-attachments/assets/34162c59-7cf7-4951-810e-96ee19f6543d" />
</p>

## Conclusiones

Los resultados obtenidos en el cálculo de la correlación cruzada muestran que las señales seno y coseno que se utilizaron son ortogonales entre sí. Esto se observa debido a que, al evaluar los valores de la correlación, no se obtiene un máximo en el retardo cero, sino que los valores se distribuyen de manera positiva y negativa en los diferentes desplazamientos. Este resultado muestra que las señales no presentan una similitud directa, pero sí mantienen una relación matemática.

La gráfica  de la correlación evidencia cómo la similitud entre las señales varía con el retardo que se aplica. La muestra de valores positivos y negativos indica que en ciertos desplazamientos las señales se alinean parcialmente y en otros se encuentran en oposición. Esto sirve para saber que la correlación cruzada no solo mide la similitud, sino también la forma en que esta cambia dependiendo del desfase, dando información importante sobre la relación temporal entre ambas señales.
