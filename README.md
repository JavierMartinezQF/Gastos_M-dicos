# Gastos_Medicos
Análisis de un dataset de gastos médicos
# 🏥 Predicción de Gastos Médicos con Regresión Lineal

Este proyecto analiza el clásico dataset de **insurance.csv** con el objetivo de **predecir los costos médicos** de personas aseguradas utilizando técnicas de **regresión lineal**, exploración de datos y un enfoque interpretativo basado en ciencia de datos y actuaría.

El análisis se realizó íntegramente en Python (pandas, seaborn, scikit-learn) y está diseñado para formar parte de un portafolio profesional de Machine Learning aplicado.

---

# 📂 Contenido del Proyecto

- `notebooks/`
  - Exploración de Datos (EDA)
  - Modelos de regresión lineal simple
  - Regresión lineal múltiple
  - Evaluación del modelo y análisis de residuos
- `data/`
  - insurance.csv (datos originales)
- `src/`
  - Funciones auxiliares (si decides modularizar)
- `README.md`
- `requirements.txt`

---

# 🎯 Objetivo

Construir un modelo capaz de **predecir los costos médicos (`costos`)** a partir de variables demográficas y de estilo de vida:

- Edad (`edad`)
- Sexo (`sexo`)
- Índice de masa corporal (`imc`)
- Número de hijos (`niños`)
- Tabaquismo (`fumador`)
- Región geográfica (`región`)

El análisis incluye regresiones lineales simples y una **regresión lineal múltiple completa**, junto con evaluación gráfica y cuantitativa.

---

# 🔍 Exploración de Datos (EDA)

Se realizó un análisis exploratorio para entender la estructura del dataset:

- Distribución de variables numéricas (edad, IMC, costos)
- Distribución categórica (sexo, fumador, región)
- Boxplots de costos por fumador, región y sexo
- Correlaciones entre las variables numéricas
- Scatterplots (edad vs costos, IMC vs costos, coloreados por fumador)

### Principales hallazgos del EDA:

- La distribución de `costos` es **asimétrica con cola derecha**, típica en gastos médicos.
- Ser **fumador** incrementa de manera muy marcada los costos.
- IMC y edad muestran relación positiva con los costos.
- La región no tiene un efecto visualmente tan fuerte como el tabaquismo o el IMC.

---

# 📈 Regresión Lineal Simple

Se entrenaron modelos simples:

- `edad → costos`
- `imc → costos`
- `fumador → costos`

Hallazgos clave:

- Edad e IMC predicen costos de manera individual, aunque con error considerable.
- El efecto del tabaquismo es masivo incluso en regresión simple.
- La línea de ajuste de `fumador` muestra una diferencia notable entre fumadores y no fumadores.

---

# 🤖 Regresión Lineal Múltiple
Se entrenó un modelo completo utilizando:

edad + imc + niños + sexo + fumador + región ~ costos


Tras aplicar **one-hot encoding** a las categóricas, el modelo se entrenó con un 80% del dataset (train) y se evaluó en el 20% restante (test).

### 📌 Métricas del modelo

- **MAE:** ~4,000  
- **RMSE:** ~6,000  
- **R²:** ~0.78  

Esto indica que el modelo explica cerca del **78%** de la variabilidad en los gastos médicos.

---

# 🧠 Interpretación de Coeficientes

### 🔥 Fumador (`fumador_yes`)
El predictor más importante del modelo.  
Aumenta los costos médicos en **más de 20,000 unidades**, dominando completamente al resto de variables.

### 📈 Edad (`edad`)
Aporta un aumento lineal constante a los costos.  
Personas de mayor edad incurren en más gastos médicos.

### 📈 IMC (`imc`)
Incremento moderado pero claro: a mayor IMC, mayores costos.

### 👶 Número de hijos (`niños`)
Efecto positivo pequeño, consistente pero no dominante.

### 👤 Sexo y región
Coeficientes pequeños → influencia reducida en comparación con edad, IMC y tabaquismo.

---

# 📉 Evaluación y Análisis de Residuos

Se generaron:

- Gráfico de valores reales vs predichos
- Gráfico de residuos vs predicciones
- Histograma de residuos
- QQ-plot (normalidad de residuos)

### Resultados:

- El modelo funciona bien, pero los **casos extremos** generan errores grandes.
- Existe **heterocedasticidad** (variabilidad de residuos mayor en valores altos).
- Los residuos no siguen distribución normal → comportamiento típico en datos médicos.

---

# 🔮 Recomendaciones y Trabajo Futuro

Para mejorar el modelo:

- Transformar la variable objetivo: `log(costos)`
- Incluir interacciones como `imc × fumador`
- Probar modelos no lineales (Random Forest, XGBoost)
- Analizar outliers y perfiles de riesgo alto
- Aplicar técnicas actuariales para ajuste de distribuciones (Gamma, Lognormal)

---

# 🚀 Conclusión

El proyecto demuestra cómo un análisis de regresión lineal, bien estructurado, permite:

- Identificar factores clave en los gastos médicos  
- Construir modelos interpretables  
- Detectar perfiles de riesgo  
- Establecer una base sólida para modelos más avanzados  

Tabaquismo, edad e IMC emergen como los predictores más fuertes.  
Este notebook representa un **baseline profesional** para modelar costos médicos y sirve como práctica de machine learning interpretativo.

---

# 💻 Tecnologías utilizadas

- Python 3.10+
- pandas
- numpy
- seaborn
- matplotlib
- scikit-learn
- scipy

---

# 👤 Autor

Proyecto realizado por **Javier Martínez Gon´zlez** .  





