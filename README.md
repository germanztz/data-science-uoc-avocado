# Análisis del Conjunto de Datos de Precios de Aguacate

**Conjunto de Datos de Precios de Aguacate**: El conjunto de datos "Precios de Aguacate", obtenido de Kaggle, es un conjunto de datos ampliamente utilizado para proyectos de análisis de datos y aprendizaje automático. Proporciona datos históricos sobre precios y ventas de aguacates en varias regiones de los Estados Unidos. Este conjunto de datos es valioso para entender las tendencias en los precios de los aguacates, los volúmenes de ventas y su relación con diferentes factores.

## Atributos Clave

- **Columnas**: El conjunto de datos incluye varias columnas de información. Algunas de las columnas clave típicamente encontradas en este conjunto de datos incluyen:
    - **Fecha** (`Date`): La fecha de observación.
    - **Precio Promedio** (`AveragePrice`): El precio promedio de los aguacates.
    - **Volumen Total** (`Total Volume`): El volumen total de aguacates vendidos.
    - **4046**: Volumen de aguacates Hass pequeños vendidos.
    - **4225**: Volumen de aguacates Hass grandes vendidos.
    - **4770**: Volumen de aguacates Hass extra grandes vendidos.
    - **Bolsas Totales** (`Total Bags`): Total de bolsas de aguacates vendidas.
    - **Bolsas Pequeñas** (`Small Bags`): Bolsas de aguacates pequeños vendidas.
    - **Bolsas Grandes** (`Large Bags`): Bolsas de aguacates grandes vendidas.
    - **Bolsas Extra Grandes** (`XLarge Bags`): Bolsas de aguacates extra grandes vendidas.
    - **Tipo** (`Type`): El tipo de aguacates, generalmente categorizados como convencionales u orgánicos.
    - **Región** (`Region`): La región o ciudad dentro de los Estados Unidos donde se registraron los datos.

- **Rango de Fechas**: El conjunto de datos abarca un rango de fechas, lo que permite el análisis de series de tiempo. Puedes examinar cómo cambian los precios y ventas de aguacates a lo largo de diferentes estaciones y años.

- **Regiones**: Se proporciona información para varias regiones o ciudades a través de los Estados Unidos, lo que permite el análisis de variaciones de precios y ventas en diferentes mercados.

- **Tipos**: El conjunto de datos distingue entre diferentes tipos de aguacates, como convencionales y orgánicos, lo que puede ser útil para comparar tendencias de precios entre estas categorías.

- **Volumen**: Están disponibles datos sobre el volumen total de aguacates vendidos. Esta métrica de volumen se utiliza a menudo para analizar la demanda del mercado.

- **Precio Promedio**: El conjunto de datos contiene el precio promedio de los aguacates, una métrica fundamental para entender las tendencias de precios.

## Casos de Uso

- Este conjunto de datos se utiliza comúnmente para aprender y practicar el análisis de datos, visualización de datos y modelado de regresión en proyectos de ciencia de datos y aprendizaje automático.

- Sirve como un recurso valioso para entender cómo trabajar con datos del mundo real, extraer conocimientos y tomar decisiones basadas en datos.

---

## Actividades de Análisis

### 1. **Análisis de Series Temporales**
**Resumen:** El análisis de series temporales permite identificar patrones, tendencias y estacionalidades en los precios y volúmenes de ventas de aguacates a lo largo del tiempo.

1. **Descomposición de Series Temporales de Precios:** 
   - **Uso de Datos:** Usa la columna `AveragePrice` y `Date`.
   - **Esperado:** Utiliza la función `seasonal_decompose` de la librería `statsmodels` para descomponer la serie temporal de precios en componentes de tendencia, estacionalidad y ruido. 
     - Convierte `Date` a tipo datetime usando `pd.to_datetime()`.
     - Agrupa los datos por `Date` y calcula el promedio de `AveragePrice` utilizando `groupby()` si es necesario.
     - Visualiza los componentes descompuestos usando `matplotlib` para cada uno de ellos.

2. **Análisis de Estacionalidad por Región:** 
   - **Uso de Datos:** Usa las columnas `AveragePrice`, `Date` y `Total Volume`.
   - **Esperado:** Utiliza gráficos de líneas para visualizar cómo varían los precios de aguacates por región a lo largo de diferentes estaciones del año.
     - Agrupa los datos por `region` y `Date` utilizando `groupby()`.
     - Calcula el promedio de `AveragePrice` para cada región.
     - Representa gráficamente las tendencias utilizando `plt.plot()` de `matplotlib`.

![image](https://github.com/user-attachments/assets/05725bf5-7dd3-47b7-bf31-b6c2f0b9586f)

-La caída en los precios durante los meses de Julio y Septiembre del 2015 en wide_region, se atribuye a un error en la codificación de los datos.

-Lo más importante que vemos en la gráfica es que los precios de los aguacates suben y bajan de manera regular cada año. Esto se debe a varias razones, como el clima, la cantidad de aguacates que se producen y la demanda de los consumidores.


![image](https://github.com/user-attachments/assets/a6411127-4a1c-4dbb-81ad-9bf6210aeea1)

-Al comparar las estaciones, el invierno y la primavera parecen tener precios promedio ligeramente más bajos y consistentes en comparación con el verano y el otoño, donde los precios tienden a ser más variables y en algunos casos, más altos.
Esto podría sugerir que la demanda de aguacates aumenta en los meses de verano y otoño, o que hay una menor disponibilidad de productos en esas estaciones, lo cual afecta los precios.

-Si bien los precios en general muestran un comportamiento similar en todas las ciudades, algunas áreas exhiben tendencias más marcadas en ciertos momentos. Por ejemplo:
Algunas ciudades (como California, que está más cerca de las principales áreas productoras de aguacates) podrían tener precios más estables y bajos debido a la proximidad a la fuente.
Ciudades en el noreste o áreas más alejadas de las zonas productoras (como Nueva York o Boston) podrían experimentar mayores variaciones debido a los costos adicionales de transporte y logística.

-La estacionalidad en los precios podría estar reflejando patrones de consumo también. Si se sabe que la demanda de aguacates tiende a aumentar en ciertas estaciones (como verano y otoño debido a las ensaladas y recetas de temporada), entonces las fluctuaciones en el precio podrían ser una respuesta directa a esta demanda. Otras causas también son por el clima o eventos.

3. **Comparación de Precios Promedio Mensuales:**
   - **Uso de Datos:** Usa las columnas `AveragePrice` y `Date`.
   - **Esperado:** Calcula y compara los precios promedio mensuales.
     - Agrupa los datos por mes usando `pd.Grouper` con `freq='M'`.
     - Calcula el promedio de `AveragePrice` para cada mes con `mean()`.
     - Visualiza los resultados con un gráfico de líneas usando `plt.plot()`.

4. **Tendencia de Ventas a lo Largo del Tiempo:**
   - **Uso de Datos:** Usa las columnas `Total Volume` y `Date`.
   - **Esperado:** Analiza cómo varía el volumen total de ventas a lo largo del tiempo.
     - Agrupa los datos por `Date` y suma el `Total Volume` usando `groupby()`.
     - Visualiza los resultados usando un gráfico de líneas con `plt.plot()` para mostrar la tendencia.

![image](https://github.com/user-attachments/assets/e5f8cd84-05d9-4791-82df-ceb6599c3765)

-La gráfica muestra picos recurrentes en ciertas épocas del año, probablemente debido a eventos de alta demanda como el Super Bowl, cuando el consumo de aguacates aumenta notablemente. Esto sugiere una estacionalidad en la demanda.

-Aunque hay fluctuaciones, se observa una ligera tendencia ascendente en el volumen total de ventas hacia finales de 2017 y principios de 2018, lo que podría estar relacionado con el creciente interés en el aguacate como alimento saludable.

-Existen caídas abruptas en las ventas en algunos periodos, posiblemente causadas por factores externos como problemas en la cadena de suministro o la disponibilidad limitada de aguacates debido a cuestiones climáticas o estacionales.

-La variabilidad constante en el volumen de ventas podría reflejar una demanda sensible a cambios en la oferta y el precio del aguacate, indicando una demanda flexible en función de estos factores.

5. **Análisis de Cambios en Precios Anuales:**
   - **Uso de Datos:** Usa las columnas `AveragePrice` y `year`.
   - **Esperado:** Observa las diferencias anuales en los precios promedio.
     - Agrupa los datos por `year` utilizando `groupby()`.
     - Calcula el promedio de `AveragePrice` para cada año.
     - Representa los resultados en un gráfico de barras usando `plt.bar()` que compare los precios de cada año.

### 2. **Gráficos para Visualización de Datos**
**Resumen:** La visualización de datos es clave para identificar patrones y relaciones entre diferentes variables. Los gráficos apropiados pueden proporcionar información valiosa sobre el comportamiento de los precios y volúmenes de ventas.

1. **Gráfico de Violín de Volumen de Ventas por Región:**
   - **Uso de Datos:** Usa las columnas `Total Volume` y `region`.
   - **Esperado:** Visualiza la distribución de ventas en diferentes regiones.
     - Utiliza la función `violinplot` de `seaborn` para crear gráficos de violín.
     - Configura los ejes para mostrar la relación entre `Total Volume` y `region`.
     - Añade etiquetas y títulos usando `plt.title()` y `plt.xlabel()` para facilitar la interpretación.

2. **Boxplot Comparativo de Precios entre Años:**
   - **Uso de Datos:** Usa las columnas `AveragePrice` y `year`.
   - **Esperado:** Genera boxplots para comparar la distribución de precios.
     - Utiliza `boxplot` de `seaborn` para crear boxplots que comparen `AveragePrice` entre diferentes años.
     - Asegúrate de que cada boxplot represente un año diferente.
     - Incluye etiquetas y títulos descriptivos usando `plt.title()`.
     - 
![image](https://github.com/user-attachments/assets/0ac68a5a-8626-4542-a9bb-b6757ed9d796)

-Se observa que desde 2015 a 2017, parece haber una tendencia al alza en el precio promedio de los aguacates, alcanzando su punto más alto en 2017.
-En 2018, se observa una disminución en el precio promedio, lo cual sugiere que el mercado pudo haberse estabilizado o que hubo una mayor disponibilidad de aguacates.

-El año 2017 muestra una variabilidad mayor en los precios promedio en comparación con los otros años, tanto en la amplitud de la caja como en la cantidad de outliers. Esto indica que 2017 fue un año inestable para el precio de los aguacates.
En cambio, 2018 muestra una variabilidad menor y menos outliers, sugiriendo que los precios fueron más consistentes en este año.

-La presencia de múltiples valores atípicos en los años 2016 y 2017 podría indicar la influencia de factores externos, como problemas en la cadena de suministro, variaciones climáticas, o un aumento en la demanda que impactaron los precios de forma significativa en esos períodos de tiempo.

3. **Histograma de Volumen Total de Ventas:**
   - **Uso de Datos:** Usa la columna `Total Volume`.
   - **Esperado:** Crea un histograma para mostrar la distribución del volumen total de ventas.
     - Utiliza `hist()` de `matplotlib` para crear el histograma.
     - Ajusta el número de bins para una visualización clara usando el parámetro `bins`.
     - Añade etiquetas y un título que describa lo que se muestra.

4. **Gráfico de Barras de Ventas por Tipo de Bolsa:**
   - **Uso de Datos:** Utiliza las columnas `Total Bags`, `Small Bags`, `Large Bags` y `XLarge Bags`.
   - **Esperado:** Compara las ventas de diferentes tipos de bolsas.
     - Suma los volúmenes de ventas por tipo de bolsa utilizando `sum()`.
     - Crea un gráfico de barras con `plt.bar()` para mostrar las diferencias en ventas.
     - Asegúrate de incluir etiquetas para cada tipo de bolsa.

![image](https://github.com/user-attachments/assets/2feea2ca-c199-40cc-9203-1810f9a6bf52)

-El gráfico muestra que el volumen total de ventas, Total Bags, está compuesto principalmente por Small Bags, lo que representa una correlación muy alta entre ambos, cercana a 0.99. Esto significa que cuando las ventas de Small Bags aumentan o disminuyen, el volumen de Total Bags sigue la misma tendencia, sugiriendo que las ventas de Small Bags son el principal contribuyente al volumen total.

-El tipo de bolsa más vendido es la Small Bag, que representa un volumen considerablemente mayor comparado con las Large Bags y XLarge Bags. Esto podría indicar una preferencia del consumidor por tamaños más pequeños, quizás debido a la comodidad de transporte o al precio.

-Las XLarge Bags muestran un volumen casi insignificante
![image](https://github.com/user-attachments/assets/002aed2a-47aa-449b-bfae-6218d366124e)

-Durante todos los años, las Small Bags y el total (Total Bags) son consistentemente las más vendidas. Esto reafirma que las Small Bags contribuyen en gran medida al volumen total, siendo la opción preferida de los consumidores.

-En 2016, se observa un incremento en el volumen de ventas en comparación con 2015, lo que podría indicar un aumento en la demanda de aguacates en ese año. Sin embargo, en 2018 hay una disminución en el volumen total, lo que sugiere un cambio en el mercado o en la oferta de producto.

5. **Gráfico de Líneas de Precios Promedios por Año:**
   - **Uso de Datos:** Utiliza las columnas `AveragePrice` y `year`.
   - **Esperado:** Visualiza la tendencia de precios promedio a lo largo de los años.
     - Agrupa los datos por `year` y calcula el promedio de `AveragePrice`.
     - Usa `plt.plot()` para crear un gráfico de líneas que muestre la evolución de precios.
     - Añade un título y etiquetas descriptivas a los ejes usando `plt.title()` y `plt.xlabel()`.

### 3. **Elasticidad del Precio**
**Resumen:** El análisis de elasticidad precio-demanda permite evaluar cómo los cambios en los precios afectan la demanda de aguacates. Comprender la elasticidad puede ayudar a formular estrategias de precios más efectivas.

La fórmula de elasticidad precio-demanda es:

$$
E_d = \frac{\% \text{Cambio en la cantidad demandada}}{\% \text{Cambio en el precio}} = \frac{\Delta Q / Q}{\Delta P / P}
$$

1. **Elasticidad Precio-Demanda por Año:**
   - **Uso de Datos:** Usa las columnas `AveragePrice` y `Total Volume`.
   - **Esperado:** Calcula la elasticidad del precio de la demanda para cada año.
     - Calcula la variación porcentual de `Total Volume` y `AveragePrice` utilizando `pd.pct_change()`.
     - Utiliza la fórmula de elasticidad para determinar la sensibilidad de la demanda respecto al precio.
     - Presenta los resultados en un gráfico de líneas usando `plt.plot()` para mostrar la elasticidad por año.

2. **Comparación de Elasticidad en Diferentes Mercados:**
   - **Uso de Datos:** Utiliza las columnas `Total Volume` y `AveragePrice`.
   - **Esperado:** Calcula la elasticidad del precio de la demanda en diferentes regiones.
     - Agrupa los datos por `region` y calcula la elasticidad para cada región utilizando `pd.pct_change()`.
     - Presenta un gráfico de barras que muestre la elasticidad por región usando `plt.bar()`.

![image](https://github.com/user-attachments/assets/da1f24f7-3932-4ae2-93ba-ad0c38b24814)

-La mayoría de las barras caen por debajo de cero, lo que indica una elasticidad precio-demanda negativa, es decir, un aumento en el precio generalmente resulta en una disminución en la demanda en esas regiones.

-También se observa que las elasticidades varían tanto en magnitud como en dirección entre estos tipos. En algunas regiones locales, la demanda es más inelástica (menos sensible al precio) que en regiones más amplias. Esto puede indicar que en áreas locales específicas, los consumidores son menos sensibles a los cambios en el precio de los aguacates.

-Algunas regiones, como "Albany" y "BaltimoreWashington", muestran elasticidades muy bajas, lo que sugiere que la demanda es más sensible a los cambios en el precio en estas áreas. Esto podría ser por la competencia o a la disponibilidad de aguacates en estas zonas.

-Hay algunas barras que superan el cero, lo cual es inusual en elasticidad precio-demanda. Esto puede deberse a comportamientos específicos del mercado o a factores externos, como cambios estacionales o percepciones de calidad en algunas regiones.

![image](https://github.com/user-attachments/assets/557a0b19-05e2-49fe-9ce4-fcf45a9e3671)

-La siguiente imagen es similar, pero está agrupado por tipo de región y muestra las fechas.

3. **Elasticidad a Nivel de Tipo de Bolsa:**
   - **Uso de Datos:** Usa las columnas `AveragePrice` y `Total Bags`.
   - **Esperado:** Calcula la elasticidad del precio de la demanda específica para cada tipo de bolsa.
     - Suma los volúmenes de ventas por tipo de bolsa utilizando `groupby()` y `sum()`.
     - Calcula la elasticidad para cada tipo y presenta los resultados en un gráfico comparativo usando `plt.bar()`.

4. **Análisis de Elasticidad Comparativa entre Orgánicos y Convencionales:**
   - **Uso de Datos:** Usa las columnas `AveragePrice`, `Total Volume` y `type`.
   - **Esperado:** Compara la elasticidad de la demanda entre aguacates orgánicos y convencionales.
     - Agrupa los datos por `type` y calcula la elasticidad utilizando `pd.pct_change()`.
     - Presenta un gráfico que muestre la diferencia en elasticidad entre los dos tipos usando `plt.bar()`.

![image](https://github.com/user-attachments/assets/524c1806-c20d-442d-a5f3-31c1d494e57b)

-Se observa que tanto los aguacates convencionales como los orgánicos tienen elasticidades negativas, lo que significa que, en general, un aumento en el precio lleva a una disminución en la demanda de ambos tipos.

-Observamos que la barra de los aguacates convencionales es más baja (alrededor de -1.9), lo cual indica una mayor elasticidad, es decir, la demanda es más sensible a los cambios de precio en este tipo de aguacate. Esto significa que si el precio de los aguacates convencionales sube, la demanda tiende a disminuir considerablemente, ya que los consumidores pueden ser más sensibles al precio en este tipo.

-La barra de los aguacates orgánicos está menos alejada de cero (aproximadamente -1.2), lo que indica que la demanda es menos sensible a los cambios de precio en comparación con los aguacates convencionales. Esto sugiere que los consumidores que compran aguacates orgánicos pueden estar menos influenciados por las variaciones de precio, probablemente debido a la percepción de calidad o el interés por productos orgánicos.

5. **Análisis de la Elasticidad Precios-Ventas:**
   - **Uso de Datos:** Usa las columnas `AveragePrice` y `Total Volume`.
   - **Esperado:** Examina cómo las variaciones en `AveragePrice` afectan a `Total Volume`.
     - Realiza un análisis de la relación entre estas dos variables calculando la elasticidad.
     - Presenta un gráfico de dispersión que muestre la relación y discute la tendencia observada utilizando `plt.scatter()` y `plt.plot()`.

### 4. **Análisis de Cohortes**
**Resumen:** El análisis de cohortes permite agrupar datos según características específicas y observar cómo se comportan a lo largo del tiempo. Se centra en cohortes de precios y ventas para entender las dinámicas del mercado.

1. **Cohortes Basadas en Precios Promedios Trimestrales:**
   - **Uso de Datos:** Usa las columnas `AveragePrice`, `Total Volume` y `Date`.
   - **Esperado:** Crea cohortes trimestrales y analiza cambios en precios y volúmenes.
     - Agrupa los datos por trimestre usando `pd.Grouper` con `freq='Q'`.
     - Calcula el promedio de `AveragePrice` y suma `Total Volume` para cada cohorte.
     - Visualiza los resultados en un gráfico de líneas que muestre la evolución de las cohortes.

2. **Cohortes por Región y Fecha:**
   - **Uso de Datos:** Utiliza las columnas `AveragePrice`, `Total Volume`, `region` y `Date`.
   - **Esperado:** Analiza cómo varían las cohortes de diferentes regiones.
     - Agrupa los datos por `region` y `Date` usando `groupby()`.
     - Calcula el promedio de precios y volumen para cada cohorte.
     - Presenta los resultados en gráficos de barras que muestren comparaciones entre regiones.

![image](https://github.com/user-attachments/assets/995a7074-f802-48ee-ad46-a01f162db76e)

-Este gráfico muestra que los precios tienden a ser más altos en las regiones locales, seguidos por las medias, y más bajos en las amplias. Además, hay patrones de estacionalidad en los precios, que son visibles en todas las regiones y podrían indicar que factores externos influyen en el precio del aguacate a lo largo del tiempo.

-Entre mediados de 2016 y principios de 2017, se observa un aumento en los precios en todas las cohortes, lo que podría estar relacionado con factores externos como la demanda creciente o la escasez estacional del producto. Los precios parecen ser algo estacionales, con ciertos picos y caídas en períodos consistentes cada año.

![image](https://github.com/user-attachments/assets/886cae77-01d1-48fa-a1c4-8b0782d52d0d)


3. **Análisis de Cohortes en Función del Tipo de Bolsa:**
   - **Uso de Datos:** Usa las columnas `Total Bags`, `Small Bags`, `Large Bags`, `XLarge Bags` y `Date`.
   - **Esperado:** Examina cómo se comportan las diferentes cohortes según el tipo de bolsa.
     - Agrupa los datos por tipo de bolsa y `Date`.
     - Calcula el volumen de ventas total y muestra los resultados en un gráfico de líneas.

4. **Cohortes de Clientes Basadas en Ventas:**
   - **Uso de Datos:** Usa las columnas `Total Volume`, `Date` y `region`.
   - **Esperado:** Analiza el comportamiento de las cohortes según el volumen de ventas.
     - Clasifica los clientes según su volumen de compras.
     - Visualiza las cohortes en gráficos de líneas o barras que muestren el comportamiento de compra a lo largo del tiempo.

5. **Evaluación de Retención de Ventas por Cohorte:**
   - **Uso de Datos:** Usa las columnas `Total Volume` y `Date`.
   - **Esperado:** Estudia cómo se retienen las ventas en cohortes a lo largo de un año.
     - Agrupa los datos por mes y cohortes.
     - Calcula la retención de ventas y visualiza los resultados en un gráfico de líneas que muestre las tasas de retención.


### 5. **Análisis de Correlación y Regresión**
**Resumen:** Se centra en la identificación de relaciones significativas entre las variables numéricas y el desarrollo de modelos de regresión para hacer predicciones basadas en esas relaciones.

1. **Matriz de Correlación:** 
   - **Uso de Datos:** Utiliza las columnas numéricas del DataFrame (p. ej., `AveragePrice`, `Total Volume`, `4046`, `4225`, `4770`, `Total Bags`).
   - **Esperado:** 
     - Importa las librerías necesarias: `import seaborn as sns` y `import matplotlib.pyplot as plt`.
     - Calcula la matriz de correlación usando el método `.corr()` del DataFrame.
     - Visualiza la matriz utilizando `sns.heatmap()`. 
     - Anota las correlaciones más significativas y discute su posible impacto en el análisis.

2. **Análisis de Dispersión entre Variables Clave:** 
   - **Uso de Datos:** Selecciona variables numéricas de interés como `AveragePrice` y `Total Volume`.
   - **Esperado:** 
     - Importa las librerías necesarias: `import seaborn as sns` y `import matplotlib.pyplot as plt`.
     - Crea un gráfico de dispersión con `sns.scatterplot()` para visualizar la relación entre `AveragePrice` y `Total Volume`.
     - Añade una línea de regresión utilizando `sns.regplot()` para ilustrar las tendencias.
     - Compara el ajuste de una regresión lineal frente a una polinómica.

3. **Predicciones Mensuales Usando Datos Trimestrales:**
   - **Uso de Datos:** Agrupa datos por trimestres y segmenta en meses utilizando `Date`, `AveragePrice`, y `Total Volume`.
   - **Esperado:** 
     - Convierte la columna `Date` a tipo datetime si es necesario.
     - Agrupa los datos por trimestre y calcula el promedio de `AveragePrice` y `Total Volume`.
     - Utiliza los datos de los primeros 2 meses de un trimestre para predecir el precio del tercer mes.
     - Compara los resultados de las predicciones con los precios reales.
     - Evalúa la precisión de tus predicciones utilizando métricas como R² y RMSE.

4. **Predicciones Trimestrales:**
   - **Uso de Datos:** Agrupa los datos en trimestres usando solo variables numéricas.
   - **Esperado:** 
     - Agrupa los datos por trimestres usando `pd.Grouper()` con `freq='Q'` para obtener promedios.
     - Usa los datos de 1 o 2 trimestres anteriores para predecir el siguiente trimestre ajustando modelos de regresión lineal y polinómica.
     - Compara los resultados de las predicciones con los precios reales.
     - Evalúa la precisión de tus predicciones utilizando métricas como R² y RMSE.

5. **Predicciones Anuales:**
   - **Uso de Datos:** Agrupa los datos en años, utilizando únicamente columnas numéricas.
   - **Esperado:** 
     - Agrupa los datos por año utilizando `pd.Grouper()` con `freq='Y'`.
     - Usa los datos de 1 o 2 años anteriores para predecir el siguiente año ajustando modelos de regresión lineal y polinómica.
     - Evalúa la precisión de tus predicciones utilizando métricas como R² y RMSE.

6. **Desarrollo de Modelos de Regresión Múltiple:** 
   - **Uso de Datos:** Selecciona varias variables numéricas como `Total Volume`, `4046`, `4225`, `4770`, y `Total Bags` para predecir `AveragePrice`.
   - **Esperado:** 
     - Define las variables independientes (X) y dependientes (y).
     - Ajusta modelos de regresión múltiple.
     - Compara su rendimiento utilizando métricas como R² y RMSE y discute las implicaciones de los resultados.

7. **Análisis de Coeficientes de Regresión Múltiple:**
   - **Uso de Datos:** Examina los coeficientes de los modelos de regresión múltiple ajustados.
   - **Esperado:** 
     - Extrae los coeficientes del modelo ajustado.
     - Interpreta los coeficientes para entender el impacto de cada variable numérica en `AveragePrice`.
     - Comenta sobre las variables más significativas y su relevancia.

8. **Modelos de Regresión para Diferenciar Volúmenes de Ventas:**
   - **Uso de Datos:** Usa `AveragePrice`, `Total Volume`, `4046`, `4225`, y `4770`.
   - **Esperado:** 
     - Ajusta modelos de regresión para analizar cómo los diferentes volúmenes de ventas afectan `AveragePrice`.
     - Compara los resultados de regresión lineal y polinómica.
     - Presenta las conclusiones de tus análisis.

9. **Análisis de la Influencia de las Ventas Totales en el Precio Promedio:**
   - **Uso de Datos:** Usa `Total Volume`, `AveragePrice`, y `Total Bags`.
   - **Esperado:** 
     - Ajusta un modelo de regresión lineal y polinómica para ver cómo varía `AveragePrice` en función del volumen total de ventas.
     - Evalúa la significancia de los coeficientes y discute su relevancia.

10. **Regresión para Predecir el Precio Promedio Según el Volumen de Aguacates por Tipo:**
    - **Uso de Datos:** Usa `AveragePrice`, `4046`, `4225`, `4770`, y `Total Volume`.
    - **Esperado:** 
      - Ajusta modelos de regresión lineal y polinómica.
      - Evalúa la efectividad de ambos modelos utilizando métricas como R² y RMSE.
      - Discute cuál modelo ofrece mejores predicciones y por qué, basándote en los resultados obtenidos.


