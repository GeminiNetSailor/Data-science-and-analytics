
# EDA (Exploratory Data Analysis)

## Objective
Describe the data using statistical and visualization techniques to understand its patterns or trends, detect errors, and find relevant relationships between variables.

## Instructions

In this activity, you will use a dataset related to credit risk containing the following columns:

- _person_age:_ Age of the person
- _person_income:_ Annual income
- _person_home_ownership:_ Home ownership
- _person_emp_length:_ Length of employment (in years)
- _loan_intent:_ Loan intent
- _loan_grade:_ Loan grade
- _loan_amnt:_ Loan amount
- _loan_int_rate:_ Interest rate
- _loan_status:_ Loan status (0 non-default, 1 default or delinquent)
- _loan_percent_income:_ Loan-to-income ratio
- _cb_person_default_on_file:_ Historical default
- _cb_person_cred_hist_length:_ Length of credit history

**Use the notebook** [Actividad4EDA.ipynb](Actividad4EDA.ipynb "Actividad4EDA.ipynb") and follow these steps:

Download the file: [credit_risk_dataset.csv](credit_risk_dataset.csv "credit_risk_dataset.csv") and store all its records in a dataframe (_df_).

#### **PART 1.** Descriptive Analysis (univariate)

1. Use the `info()` method of the dataframe to get a summary of the data types.
   - How many columns are numeric and how many are qualitative?
2. Determine the percentage of missing values by column.
3. Obtain the following descriptive statistics for all numerical variables:
   - Central tendency (mean, median)
   - Dispersion or variability (min, max, standard deviation, quartiles)
   - Shape (skewness and kurtosis)
   - Classify the variables _person_age_ and _loan_int_rate_ based on the observed values of skewness and kurtosis.
   **Note.** Remember that many of these statistics can be obtained using the `describe()` function and that the median is represented in the second quartile (50%).

4. Use histograms to determine the distribution of values in each variable.
   - Does it correspond to what was obtained in the skewness calculation? As you will see, real data is more complex than theory. For this reason, always accompany the skewness analysis with a graph such as a histogram.
   **Note.** For this, you can also use kernel density estimation (KDE) graphs which create a continuous and smooth curve, expanding the idea of the histogram.

5. Use boxplots to show the data distribution through its quartiles.
   - As you can observe, there are outliers in all variables. Execute the following code to identify outliers in the variable _person_age_

```pytnon
percentile_25 = df["person_age"].quantile(0.25)
percentile_75 = df["person_age"].quantile(0.75)
iqr = percentile_75 - percentile_25
upper_limit = percentile_75 + 1.5 * iqr
lower_limit = percentile_25 - 1.5 * iqr
IQR_outliers = df[(df["person_age"] <= lower_limit) | (df["person_age"] >= upper_limit)]
IQR_outliers
```


6. Obtain the following descriptive statistics for all text type variables:
   - Central tendency (mode)
   - Cardinality (number of unique values)
   - Unique counts (number of occurrences for each unique value)
   **Note.** A summary of these statistics can be obtained by indicating in the `describe()` function that only object-type variables will be included: `describe(include='object')`. For the counts, use the function `df['column'].value_counts()`

7. Use bar graphs for each variable to represent the frequency of each category.
   **Note.** Seaborn has a count plot for object-type variables, which calculates the frequency of each category without needing to use the `value_counts()` function. To generate it, indicate the column: `sns.countplot(x='column', data=df)`

#### **PART 2.** Correlation Analysis (bivariate and multivariate)

The variable _loan_status_ will be the output variable (or to be predicted in an ML model). Analyze its relationship with the rest of the variables through the following graphs:

8. A box plot, to visualize the distribution of _loan_percent_income_ according to _loan_status_. Interpret the result.
9. In the bar graphs you obtained in exercise 7, separate the count according to _loan_status_, using the _hue_ parameter.

10. A heatmap, with the correlation values of all variables in the dataframe.
    - Which variable has the highest correlation with _loan_status_?

## Support Resources
- [Hands-On Exploratory Data Analysis with Python, Packt Publishing](https://learning.oreilly.com/library/view/hands-on-exploratory-data/9781789537253)
- [Python for Data Analysis (3rd ed.), O'Reilly Media](https://learning.oreilly.com/library/view/python-for-data/9781098104023/ch09.html)

**Note:** To access the eBooks, an active session on the [O’Reilly](https://biblioteca.tec.mx/oreilly) platform is required.



## Español
Descripción e instrucciones en español.

# EDA (Exploratory Data Analysis)

## Objetivo
Describir los datos utilizando técnicas estadísticas y de visualización para comprender sus patrones o tendencias, detectar errores y encontrar relaciones relevantes entre las variables.

## Instrucciones

En esta actividad usarás un conjunto de datos en relación con el riesgo crediticio que contiene las siguientes columnas:

- _person\_age:_ Edad de la persona
- _person\_income:_ Ingresos anuales
- _person\_home\_ownership:_ Propiedad de la vivienda
- _person\_emp\_length:_ Duración del empleo (en años)
- _loan\_intent:_ Intención de préstamo
- _loan\_grade:_ Grado de préstamo
- _loan\_amnt:_ Monto del préstamo
- _loan\_int\_rate:_ Tasa de interés
- _loan\_status:_ Estado del préstamo (0 no incumplimiento, 1 incumplimiento o en mora)
- _loan\_percent\_income:_ Relación préstamo-ingreso
- _cb\_person\_default\_on\_file:_ Incumplimiento histórico
- _cb\_preson\_cred\_hist\_length:_ Duración del historial de crédito

**Utiliza la libreta** [Actividad4EDA.ipynb](Actividad4EDA.ipynb "Actividad4EDA.ipynb") y sigue estos pasos:

Descarga el archivo: [credit\_risk\_dataset.csv](credit_risk_dataset.csv "credit_risk_dataset.csv") y guarda, en un dataframe (_df_), todos sus registros.

#### **PARTE 1.** Análisis descriptivo (univariante)

1\. Utiliza el método _info()_ del dataframe, para obtener el resumen de los tipos de datos.

- ¿Cuántas columnas son numéricas y cuántas cualitativas?
2. Determina el porcentaje de valores faltantes por columna.
3. Obtén las siguientes estadísticas descriptivas para todas las variables numéricas:
- Tendencia central (media, mediana)
- Dispersión o variabilidad (min, max, desviación estándar, cuartiles)
- Forma (asimetría y curtosis)
- Clasifica las variables _person\_age_ y _loan\_in\_rate_ según los valores observados de asimetría y curtosis
**Nota.** Recuerda que muchas de estas estadísticas, puedes obtenerlas utilizando la función _describe()_ y que la mediana está representada en el segundo cuartil (50%).

4. Utiliza histogramas para determinar la distribución de los valores representados en cada variable.
- ¿Se corresponde con lo obtenido en el cálculo de asimetría? Como verás, los datos reales son más complejos que la teoría. Por esta razón, recuerda siempre acompañar el análisis de la asimetría con algún gráfico como un histograma.
**Nota.** Para esto también puedes ocupar los gráficos kde (_[kernel density estimationLinks to an external site.](https://www.cienciadedatos.net/documentos/pystats02-kernel-density-estimation-kde-python.html)) que crean una curva continua y suave expandiendo_ la idea del histograma.

5. Emplea boxplots para mostrar la distribución de los datos a través de sus cuartiles.
-  Como podrás observar hay valores atípicos en todas las variables. Ejecuta el siguiente código para identificar los valores atípicos en la variable _person\_age_

```pytnon
percentile_25 = df["person_age"].quantile(0.25)
percentile_75 = df["person_age"].quantile(0.75)
iqr = percentile_75 - percentile_25
upper_limit = percentile_75 + 1.5 * iqr
lower_limit = percentile_25 - 1.5 * iqr
IQR_outliers = df[(df["person_age"] <= lower_limit) | (df["person_age"] >= upper_limit)]
IQR_outliers
```

6. Obtén las siguientes estadísticas descriptivas para todas las variables de tipo texto:
- Tendencia central (moda)
- Cardinalidad (cantidad de valores únicos)
- Recuentos únicos (número de ocurrencias para cada valor único)
**Nota.** Un resumen de estas estadísticas, puedes obtenerlas indicando en la función _describe()_ que se incluirán sólo las variables de tipo object: _describe(include = 'object')_. Para los recuentos utiliza la función _df\['columna'\].value\_counts()_

7. Utiliza gráficos de barras por variable para representar la frecuencia de cada categoría.
**Nota.** seaborn posee un gráfico de recuento, para variables de tipo object, que calcula la frecuencia de cada categoría sin necesidad de utilizar la función _value\_counts()_. Para generarlo debes indicar la columna: _sns.countplot(x='columna', data=df)_

#### **PARTE 2.** Análisis de correlación (bivariante y multivariante)

La variable _loan\_status_ será la variable de salida (o a predecir en un modelo de ML). Analiza su relación con el resto de las variables a través de los siguientes gráficos:

8. Un box plot, para visualizar la distribución de _loan\_percent\_income_ según el _loan\_status_. Interpreta el resultado.
9. En los gráficos de barras que obtuviste en el ejercicio 7, separa el conteo según el _load\_status_, utilizando el parámetro _hue_.

10\. Un mapa de calor, con los valores de correlación de todas las variables del dataframe.

- ¿Qué variable tiene mayor correlación con _loan\_status_?

## Recursos de Apoyo
- [Hands-On Exploratory Data Analysis with Python, Packt Publishing](https://learning.oreilly.com/library/view/hands-on-exploratory-data/9781789537253)
- [Python for Data Analysis (3rd ed.), O´Reilly Media](https://learning.oreilly.com/library/view/python-for-data/9781098104023/ch09.html)

**Nota:** Para acceder a los libros electrónicos es necesario tener una sesión activa en la plataforma [O’Reilly](https://biblioteca.tec.mx/oreilly).
