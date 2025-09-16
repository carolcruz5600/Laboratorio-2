# **Parte A - Resultados**
## **Configuración Inicial**
Esta sección importa las librerías esenciales: NumPy para cálculos numéricos, Matplotlib para gráficos, WFDB para leer señales médicas, SciPy para estadísticas avanzadas y Seaborn para visualizaciones elegantes. Es la base técnica que permite procesar y analizar señales ECG de manera correcta.

<img width="60%" alt="image" src="https://github.com/user-attachments/assets/a4a25afc-724f-4265-8f3c-a49a7d6a4f4a" />


## **Convoluciones**
## 1. Cálculo Manual

> ### **Laura**

> ### **Carol**

> ### **Carlos**

## 2. Representación Gráfica y Secuencial Manual
> ### **Laura**

> ### **Carol**

> ### **Carlos**

## 3. Cálculo usando Python

> ### **Definición de las Señales**
En esta implementación se definieron tres conjuntos de señales personalizadas utilizando NumPy. Las señales del sistema (cf1, l1, c1) tienen una longitud de 7 elementos, con valores basados en los códigos estudiantiles, mientras que las señales de entrada (cf2, l2, c2) cuentan con 10 elementos cada una de manera uniforme. Esta configuración facilita el análisis comparativo de la convolución discreta. 

<img width="40%" alt="image" src="https://github.com/user-attachments/assets/e05edd25-6bb1-4074-9031-af87c33fe86d" />


> ### **Convolución de las Señales**
Los resultados de la convolución muestran tres secuencias de salida de 16 elementos cada una, confirmando la propiedad teórica N+M-1. La convolución Lau alcanza un pico máximo de 184, Carol presenta un máximo de 147, y Charlie llega a 149. Estas diferencias en amplitud y distribución temporal reflejan cómo las características específicas de cada par de señales influyen en la respuesta del sistema, demostrando la sensibilidad de la operación de convolución a las variaciones en las señales de entrada y del sistema.

<img width="647" height="443" alt="image" src="https://github.com/user-attachments/assets/5a9ce4f1-86e5-48ac-92c9-ffbbfcabb78f" />




## 4. Representación Gráfica y Secuencial usando Python 
En esta sección se implementa la visualización gráfica a de los resultados obtenidos para los tres casos analizados. La metodología emplea la creación de vectores de índices temporales mediante np.arange() y la configuración de subplots múltiples organizados verticalmente, utilizando gráficas de barras discretas (plt.stem()) apropiadas para la representación de señales digitales. Cada conjunto gráfico muestra secuencialmente la señal del sistema código, la señal de entrada cédula y su convolución resultante, incorporando títulos descriptivos, etiquetas de ejes, rejillas de referencia y ajuste del espaciado entre gráficas para facilitar la comparación visual directa y el análisis cuantitativo de los resultados de convolución.

> ### **Laura**

<img width="315" height="592" alt="image" src="https://github.com/user-attachments/assets/91b84bc8-2683-4756-ae8f-fb0f6ecf3b28" />

<br>
<br>

La gráfica alcanza una amplitud máxima de aproximadamente 184 en la muestra 9, presentando la respuesta más robusta de los tres casos analizados. Su señal de código incluye un elemento adicional que extiende la longitud del sistema, mientras que la señal correspondiente a la cédula muestra patrones únicos con valores concentrados en posiciones específicas que contribuyen a generar la convolución de mayor amplitud entre los casos estudiados.

<img width="695" height="682" alt="image" src="https://github.com/user-attachments/assets/d5f4250a-ba5c-4c30-a98d-afedfa283571" />


> ### **Carol**

<img width="335" height="596" alt="image" src="https://github.com/user-attachments/assets/a61fb407-077a-44ec-9777-c80b0bc47927" />

<br>
<br>

La gráfica demuestra un comportamiento con pico máximo de 147 alrededor de la muestra 8. Su señal de código mantiene la estructura característica con ceros en posiciones centrales y valores significativos en los extremos, mientras que la señal correspondiente a la cédula exhibe una secuencia diferente que genera una respuesta convolucionada con múltiples picos secundarios y energía distribuida de manera distintiva a lo largo de la secuencia temporal.

<img width="695" height="682" alt="image" src="https://github.com/user-attachments/assets/b10e95cc-9d3a-414c-9756-9bbea1049f63" />

> ### **Carlos**

<img width="330" height="600" alt="image" src="https://github.com/user-attachments/assets/fa57cc13-5625-41f9-a645-0b804a53d853" />

<br>
<br>

Se evidencia una convolución con pico máximo de aproximadamente 149 en la posición 9, exhibiendo una distribución asimétrica con valores significativos concentrados entre las muestras 4 y 12. La señal de código muestra impulsos principales en las posiciones 0, 1, 4 y 5 con valores de 5, 6, 8 y 1 respectivamente, mientras que la señal correspondiente a la cédula presenta una distribución dispersa con picos notables que generan la respuesta convolucionada observada.

<img width="695" height="682" alt="image" src="https://github.com/user-attachments/assets/de03174b-3658-4983-a444-68fb6aed6a46" />

Las representaciones gráficas muestran la correspondencia directa entre las señales de entrada y los resultados obtenidos mediante convolución discreta. Las señales basadas en códigos presentan estructuras dispersas, con valores significativos concentrados en pocas posiciones, mientras que las señales de cédula exhiben distribuciones más densas y variaciones considerables en amplitud y ubicación temporal. Esta diferencia en la naturaleza de las señales determina las características distintivas observadas en cada resultado de la convolución.

Los gráficos de convolución evidencian la expansión temporal esperada de 16 muestras, mostrando patrones de respuesta que reflejan la interacción específica de cada par de señales. La concentración de amplitudes máximas en la región central de las secuencias, seguida de decaimientos asimétricos hacia los extremos, confirma el comportamiento esperado de la operación matemática.
