# **Parte C - Análisis de la Señal EOG**
## **1 y 2. Parámetros y Digitalización**
Al fijarse en algún objeto, el ojo humano realiza movimientos simultáneos que generan un potencial de acción entre el epitelio pigmentario y la córnea. Estas señales suelen tener un ancho de banda característico de 0.5 a 50 Hz (Pérez et al., 2023). Por consiguiente, siguiendo el criterio de Nyquist:

$$f_{max}=50Hz$$\
$$f_N = 2f_{max}$$\
$$f_N=100 Hz$$

Así, de acuerdo con la guía de laboratorio, si se digitaliza la señal con una frecuencia de muestreo de 4 veces la frecuencia de Nyquist:

$$f_s=4f_N$$\
$$f_s=400Hz$$

Sin embargo, se optó por usar una frecuencia de muestreo $f_s=800Hz$ para evitar conflictos con otros parámetros previamente definidos. La captura de la señal EOG originada del generador de señales biológicas se realizó empleando la librería ``nidaqmx``. Para su uso fuera del laboratorio, la señal se guardo en formato ``.txt`` con la ayuda de ``np.savetxt``.

<img width="727" height="437" alt="image" src="https://github.com/user-attachments/assets/d856963a-95b2-443a-b426-f72d488a4db0" />

Los otros parámetros de la captura fueron:\
$$n=5000$$\
$$T=n/f_s$$

Posteriormente, se grafica la señal no sin antes cargar el archivo ``.txt`` a la variable ``data``.

<img width="532" height="161" alt="image" src="https://github.com/user-attachments/assets/f91d7fb8-a417-4110-8e14-b8dc955299ab" />

<img width="525" height="360" alt="image" src="https://github.com/user-attachments/assets/181fc423-d0f2-46e4-9a31-b54e91562156" />

## **3. Caracterización de la Señal**
Se obtuvieron los estadísticos de la señal EOG empleando librerías de ``NumPy``.

<img width="475" height="235" alt="image" src="https://github.com/user-attachments/assets/132ebb16-478a-4cff-bb99-0fe91a766741" />

### Estadísticos
* **Media:** -0.038
* **Mediana:** 0.002
* **Desviación Estándar:** 0.223
* **Máximo:** 0.879
* **Mínimo:** -0.836

#### Discusión

Estos valores de *media* y *mediana* muy cercanos a cero permite resaltar una característica típica de las señales biológicas como la variación alrededor de un valor de referencia, que la señal no presenta un sesgo hacia valores positivos o negativos, y una distribución bastante simétrica de los datos capturados. Una *desviación estándar* baja de 0.223 indica que los datos se distribuyen dentro de un rango estrecho con poca intervención de señales de gran amplitud atípicas, validando una buena captura de la misma. El *máximo* y *mínimo* confirman lo anteriormente mencionado, pues picos de 0.879 y -0.836 respectivamente reflejan los movimientos oculares más notorios, que se encuentran dentro de los valores esperados.

### Clasificación
> Aleatoria

Depende del movimiento de los ojos, un fenómeno variable. No se puede predecir con exactitud ni se puede extraer mediante una tabla de datos. Es necesario un análisis estadístico para comprenderla.

> Aperiódica

Los movimientos oculares no siguien un patrón específico que se repite en un intervalo de tiempo definido. 

> Analógica luego Digital

Inicialmente es de carácter analógico, el generador de señales biológicas entrega voltajes característicos. Posteriormente, se convierte en una señal digital gracias al DAQ, para poder manipularla.

## **4. Transformada de Fourier y PSD**
En ``Python`` existen varias librerías capaces de realizar una Transformada Rápida de Fourier (FFT) y calcular la Densidad Espectral de Potencia (PSD). En este caso se utilizó ``SciPy``, más específicamente los módulos ``scipy.fft`` y ``signal``. 

<img width="483" height="162" alt="image" src="https://github.com/user-attachments/assets/062b8794-13a3-4561-94b9-d72e1374b319" />

Para la FFT, ``fft(data)`` devuelve la transformada en su forma compleja y ``fftfreq(n, 1/fs)`` crea el eje de las frecuencias de tamaño $n$ y de paso temporal $1/f_s=T_s$. Para la magnitud de la FFT, se usa ``np.abs(fourier)``. Para tomar sólo la mitad positiva de estos arrays se emplea ``:n//2``. El cálculo de la PSD se realizó mediante el método ***Welch***, el cual la estima aplicando una ventana de Hann, calculando la FFT y promediando sus espectros (``f_psd,psd=signal.welch(data, fs, window="hann", nperseg=256)``). Este método reduce considerablemente el ruido al usar un número de muestras por segmento ``nperseg=256`` mucho menor al tamaño de la señal $n=5000$. La PSD se guarda en ``psd`` y el eje de frecuencias en ``f_psd``.

<img width="296" height="124" alt="image" src="https://github.com/user-attachments/assets/aca39e8c-3746-405c-be0f-57cfd310920f" /> \
<img width="525" height="370" alt="image" src="https://github.com/user-attachments/assets/89de6d8f-11ed-4a4e-b8ec-c5d6aee7f6e0" />


<img width="423" height="125" alt="image" src="https://github.com/user-attachments/assets/0294a700-8e1c-47f0-a79d-b4aec6e7a8fc" /> \
<img width="525" height="370" alt="image" src="https://github.com/user-attachments/assets/19d0ab79-a3d0-43e9-8dd0-1605e849768d" />

#### Discusión

La Transformada de Fourier permite ver los componentes de frecuencia de una señal. En este caso particular, es posible observar que las frecuencias bajas cercanas a 0 Hz dominan la señal, coincidiendo con las características descritas al inicio de esta sección. La Densidad Espectral de Potencia muestra cómo se distribuye la potencia de una señal en el dominio de la frecuencia. Bajo estas condiciones, su comportamiento revela una tendencia bastante similar a la de la FFT, reflejando nuevamente que la mayor parte de la potencia de la señal capturada se encuentra en las frecuencias cercanas a 0 Hz.

### Análisis Estadístico en el Dominio de la Frecuencia
Para poder adquirir los estadísticos relacionados con el eje de la frecuencia, es necesario ponderarlo teniendo en cuenta la PDS. Cada componente de frecuencia en la señal tiene un peso diferente, pues no podemos considerar que las frecuencias cercanas a 0 Hz afectan de la misma manera a la señal que las de 100 Hz. En este caso, se creó un array de probabilidades ``prob``, que contiene el peso relatvo de cada frecuencia, así como ``sumprobfreq``, que es la suma del array de probabilidad para encontrar valores relevantes más adelante.

<img width="541" height="315" alt="image" src="https://github.com/user-attachments/assets/9d575b2e-801e-4901-9994-b5f6f0c90027" />

> Frecuencia Media

Se calcula el promedio ponderado de ``f_psd`` con ``np.average()``. Los pesos se definen con ``weights=prob``.

> Frecuencia Mediana

Mediante ``np.interp()`` se hace una interpolación lineal para encontrar el punto donde la suma de probabilidades ``sumprobfreq`` alcanza el $50$%. La función arroja la posición ``f_pds[i]`` en donde se llega a ese punto, que coincide con la frecuencia media.

> Desviación Estándar

Se calcula la varianza con respecto a la frecuencia mediana con ``(f_psd - f_mediana)**2``. Posteriormente, ``np.average(..., weights=prob)`` promedia y pondera la varianza, generando una varianza ponderada. Para obtener la desviación estándar, se calcula la raiz cuadrada de lo anterior.

### Estadísticos
* **Media de Frecuencias:** 16.084
* **Mediana de Frecuencias:** 3.257
* **Desviación Estándar:** 48.268

#### Discusión
Una *media de frecuencias* de 16.084 Hz representa que esas componentes de frecuencia son las de mayor peso en la señal, un valor ligeramente alejado al esperado cercano a los 0 Hz. No obstante, la *media de frecuencias* de 3.257 Hz simboliza que la mitad de la energía acumulada en la señal está por debajo de esa frecuencia, lo que es coherente con la naturaleza de las señales EOG. La *desviación estándar* de 48.268 Hz indica que, a pesar de que la energía de la señal se concentra en las frecuencias más bajas, todavía hay algunas señales que se dispersan hasta casi el borde del ancho de banda (50 Hz). De forma general, son llamativos los resultados de la *media de frecuencias* y la *desviación estándar*, ya que sus inconsistencias podrían deberse a contaminación por ruido. Sin embargo, al haber sido extraída directamente del generador de señales biológicas, teóricamente éste debería de ser casi inexistente.

### Histograma de Frecuencias
<img width="478" height="108" alt="image" src="https://github.com/user-attachments/assets/1d5a276a-7669-4c41-b462-45be774973d4" />
<img width="525" height="370" alt="image" src="https://github.com/user-attachments/assets/287c466a-bf7d-4c7f-8154-40a821e1a0cb" /> 

Pese a que la tendencia y forma del gráfico del histograma corresponde al anteriormente visto en la FFT y la PSD, se están analizando parámetros distintos. Mientras que en la FFT y la PSD vemos la distribución de la energía en el dominio de la frecuencia, en el histograma se muestra la frecuencia de aparición de los componentes de frecuencia en la señal. Sirve como herramienta para entender el comportamiento estadístico en el dominio del tiempo.

## **5. Conclusiones**
La Señal EOG capturada desde el generador de señales biológicas presenta una naturaleza aleatoria, aperiódica y de baja frecuencia, típica de este tipo de señales. Su análisis en el dominio del tiempo permite observar valores importantes que moldean su comportamiento, lo que facilita su interpretación. La Transformada de Fourier y la Densidad Espectral de Potencia se presentan como mecanismos clave en la identificación de las componentes frecuenciales de la señal y su peso sobre la misma, permitiendo validar experimentalmente que la gran parte de señales de la EOG son de baja frecuencia cercana a los 0 Hz. Finalmente, el histograma de frecuencias aporta una visión estadística de su distribución en la señal, ayudando a comprender de mejor forma su composición.

## **6. Archivo Python - Spyder**
Documento `.py`: [Lab 2 Parte C.py](https://github.com/user-attachments/files/22457176/Lab.2.Parte.C.py)
