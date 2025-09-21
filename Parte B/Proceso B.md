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

Como se puede observar en la gráfica las señales tienen un desfase de ``π/2`` lo que sirve para analizar que cuando alcanzan los valores mínimos y máximos no son al mismo tiempo.

<p align="center">
<img width="587" height="457" alt="image" src="https://github.com/user-attachments/assets/8e37c6b2-cfb4-4a5c-b4f9-240befab4b57" />
</p>
