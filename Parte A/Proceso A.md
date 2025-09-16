# **Parte A - Resultados**
## **Configuración Inicial**
Esta sección importa las librerías esenciales: NumPy para cálculos numéricos, Matplotlib para gráficos, WFDB para leer señales médicas, SciPy para estadísticas avanzadas y Seaborn para visualizaciones elegantes. Es la base técnica que permite procesar y analizar señales ECG de manera correcta.

<img width="587" height="167" alt="image" src="https://github.com/user-attachments/assets/a387e201-4d30-4a6a-9b8a-1b8072c14a0c" />


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

<img width="361" height="216" alt="image" src="https://github.com/user-attachments/assets/1e2c9a22-9823-436e-9db7-2e02b197cd7a" />

> ### **Convolución de las Señales**
Los resultados de la convolución muestran tres secuencias de salida de 16 elementos cada una, confirmando la propiedad teórica N+M-1. La convolución Lau alcanza un pico máximo de 184, Carol presenta un máximo de 147, y Charlie llega a 149. Estas diferencias en amplitud y distribución temporal reflejan cómo las características específicas de cada par de señales influyen en la respuesta del sistema, demostrando la sensibilidad de la operación de convolución a las variaciones en las señales de entrada y del sistema.

<img width="639" height="434" alt="image" src="https://github.com/user-attachments/assets/9cf6cf3b-bfa5-496b-b376-fe97ce286ed9" />

## 4. Representación Gráfica y Secuencial usando Python 
En esta sección se implementa la visualización gráfica a de los resultados obtenidos para los tres casos analizados. La metodología emplea la creación de vectores de índices temporales mediante np.arange() y la configuración de subplots múltiples organizados verticalmente, utilizando gráficas de barras discretas (plt.stem()) apropiadas para la representación de señales digitales. Cada conjunto gráfico muestra secuencialmente la señal del sistema código, la señal de entrada cédula y su convolución resultante, incorporando títulos descriptivos, etiquetas de ejes, rejillas de referencia y ajuste del espaciado entre gráficas para facilitar la comparación visual directa y el análisis cuantitativo de los resultados de convolución.

> ### **Laura**

<img width="310" height="596" alt="image" src="https://github.com/user-attachments/assets/fc766d19-92a3-4b6a-9157-86a08b17bf11" />

<br>
<br>

La gráfica alcanza una amplitud máxima de aproximadamente 184 en la muestra 9, presentando la respuesta más robusta de los tres casos analizados. Su señal de código incluye un elemento adicional que extiende la longitud del sistema, mientras que la señal correspondiente a la cédula muestra patrones únicos con valores concentrados en posiciones específicas que contribuyen a generar la convolución de mayor amplitud entre los casos estudiados.

<img width="695" height="682" alt="image" src="https://github.com/user-attachments/assets/6e559452-8e18-4f43-ac0c-c1cc58655e23" />

> ### **Carol**

<img width="312" height="596" alt="image" src="https://github.com/user-attachments/assets/ce4e36c2-9bf1-4985-81b3-61dd705db7a4" />

<br>
<br>

La gráfica demuestra un comportamiento con pico máximo de 147 alrededor de la muestra 8. Su señal de código mantiene la estructura característica con ceros en posiciones centrales y valores significativos en los extremos, mientras que la señal correspondiente a la cédula exhibe una secuencia diferente que genera una respuesta convolucionada con múltiples picos secundarios y energía distribuida de manera distintiva a lo largo de la secuencia temporal.

<img width="695" height="682" alt="image" src="https://github.com/user-attachments/assets/ee70e78c-80cb-46b6-84a8-4346555cc58e" />

> ### **Carlos**

<img width="327" height="594" alt="image" src="https://github.com/user-attachments/assets/57c25e03-2696-4443-94e8-7e9eac395e95" />

<br>
<br>

Se evidencia una convolución con pico máximo de aproximadamente 149 en la posición 9, exhibiendo una distribución asimétrica con valores significativos concentrados entre las muestras 4 y 12. La señal de código muestra impulsos principales en las posiciones 0, 1, 4 y 5 con valores de 5, 6, 8 y 1 respectivamente, mientras que la señal correspondiente a la cédula presenta una distribución dispersa con picos notables que generan la respuesta convolucionada observada.

<img width="695" height="682" alt="image" src="https://github.com/user-attachments/assets/56de7562-2e93-4c55-9112-00c72ac87197" />

Las representaciones gráficas muestran la correspondencia directa entre las señales de entrada y los resultados obtenidos mediante convolución discreta. Las señales basadas en códigos presentan estructuras dispersas, con valores significativos concentrados en pocas posiciones, mientras que las señales de cédula exhiben distribuciones más densas y variaciones considerables en amplitud y ubicación temporal. Esta diferencia en la naturaleza de las señales determina las características distintivas observadas en cada resultado de la convolución.

Los gráficos de convolución evidencian la expansión temporal esperada de 16 muestras, mostrando patrones de respuesta que reflejan la interacción específica de cada par de señales. La concentración de amplitudes máximas en la región central de las secuencias, seguida de decaimientos asimétricos hacia los extremos, confirma el comportamiento esperado de la operación matemática.
