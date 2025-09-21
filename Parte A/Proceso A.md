# **Parte A - Resultados**
## **Configuración Inicial**
Esta sección importa las librerías esenciales: NumPy para cálculos numéricos, Matplotlib para gráficos, WFDB para leer señales médicas, SciPy para estadísticas avanzadas y Seaborn se emplea para generar visualizaciones estadísticas claras y estilizadas.

<img width="587" height="167" alt="image" src="https://github.com/user-attachments/assets/a387e201-4d30-4a6a-9b8a-1b8072c14a0c" />

## **Convoluciones**
## 1. Cálculo Manual
> ### **Laura**
En este apartado se implementa el cálculo manual de la convolución discreta entre las secuencias ``ℎ(𝑛)`` (respuesta al impulso del sistema) y ``𝑥(𝑛)`` (señal de entrada). Se utilizó el método matricial: cada elemento de ``𝑥(𝑛)`` multiplica a todos los elementos de ``ℎ(𝑛)`` generando productos desplazados (columnas diagonales en la tabla). Posteriormente, se suman los valores sobre cada diagonal para obtener la secuencia resultante ``𝑦(𝑛)``.

<img width="1012" height="369" alt="image" src="https://github.com/user-attachments/assets/2bcd7b95-81f4-43fa-ac00-5b41be2a09a3" />

> ### **Carol**
Se aplica el mismo proceso de convolución discreta con un conjunto distinto de secuencias ``ℎ(𝑛)`` y ``𝑥(𝑛)``. El uso de la tabla permite visualizar la propiedad de linealidad y superposición del sistema: cada fila corresponde a ``ℎ(𝑛)`` ponderada por una muestra de ``𝑥(𝑛)``, y la alineación diagonal muestra cómo se acumulan los aportes en distintos instantes 𝑛. El resultado ``𝑦(𝑛)`` permite verificar manualmente el comportamiento del sistema, siendo útil para contrastar con implementaciones computacionales.

<img width="1065" height="321" alt="image" src="https://github.com/user-attachments/assets/21e04f77-6bb5-4efb-9f7e-dd7a26c6a403" />

> ### **Carlos**
En este caso, aunque cambian los valores de ``ℎ(𝑛)`` y ``𝑥(𝑛)``, la longitud 𝑛 de las secuencias permanece constante, por lo que la cantidad de operaciones no se incrementa, solo varían los resultados obtenidos en cada posición.

<img width="1371" height="374" alt="image" src="https://github.com/user-attachments/assets/d764861c-af2c-4ed0-af9f-578140c6a125" />

<br>
<br>

> [!IMPORTANT]  
> En esta sección se realizó el cálculo manual de la convolución discreta de señales, utilizando el método tabular (multiplicación y suma diagonal) para verificar el resultado de forma analítica. Este cálculo manual servirá como referencia para comparar y validar los resultados obtenidos posteriormente mediante Python.

## 2. Representación Gráfica Manual

Para esta sección se utilizaron los datos correspondientes al código y la cédula de cada estudiante para generar dos señales discretas. Posteriormente, se representaron gráficamente ambas señales de entrada, evidenciando la distribución de amplitudes en función del índice n. Finalmente, se obtuvo y graficó la señal resultante de la convolución, mostrando sus amplitudes correspondientes. 

> ### **Laura**
> <p align="center">
  <img width="45%" height="585" alt="image" src="https://github.com/user-attachments/assets/b038be6b-1f06-44af-8604-ad0c7a2e02b9" />
   &nbsp;&nbsp;
  <img width="53%" height="640" alt="image" src="https://github.com/user-attachments/assets/57d83c90-6e9f-4871-a56a-d2f4e76654c2" />
</p>
<br>
<br>
<p align="center">
<img width="530" height="506" alt="image" src="https://github.com/user-attachments/assets/d4181d95-2985-496d-8a24-001ad6720320" />
</p>

<br>

> ### **Carol**
> <p align="center">
 <img width="45%" height="538" alt="image" src="https://github.com/user-attachments/assets/c6c914d2-93de-4755-9e3d-472c213d26c1" />
   &nbsp;&nbsp;
 <img width="50%" height="639" alt="image" src="https://github.com/user-attachments/assets/afd95075-c8bf-4856-994b-53a1f9fcce96" />
</p>
<br>
<br>
<p align="center">
<img width="532" height="567" alt="image" src="https://github.com/user-attachments/assets/d6c17e28-104b-4c68-8fb2-f8e4db6fbc60" />
</p>

<br>

> ### **Carlos**
> <p align="center">
 <img width="44%" height="584" alt="image" src="https://github.com/user-attachments/assets/4f4e8d42-909b-4970-9455-4727a8f5c2bb" />
   &nbsp;&nbsp;
<img width="53%" height="639" alt="image" src="https://github.com/user-attachments/assets/df61123f-8e0c-4a48-8a25-c3b06e77cec1" />
</p>
<br>
<br>
<p align="center">
<img width="532" height="505" alt="image" src="https://github.com/user-attachments/assets/2135358b-cb42-4662-bf17-df04aa4df86c" />
</p>

> [!IMPORTANT]  
> Los resultados obtenidos de forma gráfica fueron comparados y validados con las representaciones generadas mediante la implementación en Python, confirmando la correcta ejecución de la convolución discreta en todos los casos analizados.

## 3. Cálculo usando Python

> ### **Definición de las Señales**
En la implementación se definieron tres conjuntos de señales personalizadas mediante NumPy. Cada conjunto está compuesto por una señal del sistema ``(cf1, l1, c1)`` y su correspondiente señal de entrada ``(cf2, l2, c2)``. Las señales del sistema tienen una longitud de 7 elementos y fueron construidas a partir de los códigos estudiantiles, mientras que las señales de entrada poseen 10 elementos cada una, con valores distribuidos de manera uniforme. Esta configuración permite aplicar la operación de convolución discreta en diferentes ejemplos y facilita el análisis comparativo entre las señales generadas.

<img width="361" height="216" alt="image" src="https://github.com/user-attachments/assets/1e2c9a22-9823-436e-9db7-2e02b197cd7a" />

> ### **Convolución de las Señales**
Los resultados de la convolución muestran tres secuencias de salida de 16 elementos cada una, confirmando la propiedad teórica ``N+M-1``. La convolución Lau alcanza un pico máximo de 184, Carol presenta un máximo de 147, y Charlie llega a 149. Estas diferencias en amplitud y distribución temporal reflejan cómo las características específicas de cada par de señales influyen en la respuesta del sistema, demostrando la sensibilidad de la operación de convolución a las variaciones en las señales de entrada y del sistema.

<img width="639" height="434" alt="image" src="https://github.com/user-attachments/assets/9cf6cf3b-bfa5-496b-b376-fe97ce286ed9" />

## 4. Representación Gráfica usando Python 
En esta sección se implementa la visualización gráfica a de los resultados obtenidos para los tres casos analizados. La metodología emplea la creación de vectores de índices temporales mediante ``np.arange()`` y la configuración de subplots múltiples organizados verticalmente, utilizando gráficas de barras discretas ``(plt.stem())`` apropiadas para la representación de señales digitales. Cada conjunto gráfico muestra secuencialmente la señal del sistema código, la señal de entrada cédula y su convolución resultante, incorporando títulos descriptivos, etiquetas de ejes, rejillas de referencia y ajuste del espaciado entre gráficas para facilitar la comparación visual directa y el análisis cuantitativo de los resultados de convolución.

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

## 5. Conclusiones
El desarrollo de la convolución discreta mediante el método tabular presentó concordancia total con los resultados computacionales obtenidos en Python. Durante el proceso manual se observó que la organización matricial facilita la comprensión del mecanismo de superposición y desplazamiento que caracteriza esta operación, mientras que la implementación computacional corrobora estos mismos principios de manera más eficiente.
En los tres casos estudiados se cumplió la relación fundamental ``N + M - 1`` para la longitud de la señal resultante. Las señales de entrada de 7 y 10 elementos generaron consistentemente salidas de 16 elementos, lo cual constituye una verificación práctica de esta propiedad teórica. 

Las amplitudes máximas obtenidas fueron 184 para Laura, 147 para Carol y 149 para Carlos. Estas variaciones se explican por la particular distribución de valores en cada par de señales, donde la concentración de magnitudes altas en posiciones específicas produce respuestas de mayor amplitud. Por el contrario, valores dispersos tienden a distribuir la amplitud a lo largo de toda la secuencia temporal.
La representación gráfica mediante stem plots demostró ser apropiada para señales discretas, permitiendo una lectura clara de los valores y posiciones temporales. Esta visualización reveló patrones característicos en cada convolución y facilitó la identificación de los puntos de máxima respuesta del sistema.

El contraste entre ambos métodos evidenció sus respectivas ventajas: el cálculo manual promueve la comprensión profunda de los mecanismos matemáticos involucrados, mientras que la implementación en Python proporciona exactitud y rapidez para el manejo de señales de mayor complejidad. 
Los resultados muestran que la convolución discreta es útil para la caracterización de sistemas lineales e invariantes en el tiempo.

## 6. Archivo Google Colab 
Enlace Archivo: [Práctica 2](https://colab.research.google.com/drive/1vqF47wZy_N09mnzz5e-S0ylZ8glOJxMO?usp=sharing)
