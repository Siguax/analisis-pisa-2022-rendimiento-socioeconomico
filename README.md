# Análisis Comparativo del Rendimiento Educativo y su Relación con Factores Socioeconómicos (PISA)

![R](https://img.shields.io/badge/R-276DC3?style=for-the-badge&logo=r&logoColor=white)
![PISA](https://img.shields.io/badge/PISA-2022-blue?style=for-the-badge)
![Status](https://img.shields.io/badge/Status-Completado-success?style=for-the-badge)

## 📖 Introducción

El Programa para la Evaluación Internacional de los Estudiantes (PISA), coordinado por la OCDE, evalúa las habilidades de estudiantes de 15 años en matemáticas, lectura y ciencias. Este proyecto analiza comparativamente el rendimiento educativo y su relación con factores socioeconómicos en cuatro países: **Argentina (ARG), Irlanda (IRL), Corea del Sur (KOR) y Nueva Zelanda (NZL)**.

Los datos provienen del paquete de R **"Learning Towers"** (reproducción de PISA 2022), con una muestra de **613,744 observaciones** y 22 variables.

## 🎯 Preguntas de Investigación

1. ¿Cuál es el nivel de rendimiento en las áreas evaluadas en cada país?
2. ¿Existe una relación lineal entre el nivel socioeconómico y cultural (ESCS) y el rendimiento académico? ¿Qué tan fuerte es?
3. Identificando el área y país con la relación más fuerte, ¿cuál de los factores (ESCS, internet, computadora, habitación propia, género) influye más simultáneamente?
4. ¿Existe una diferencia estadísticamente significativa entre el rendimiento en matemáticas de 2015 y 2022?

## 📊 Hallazgos Principales

### 1. Rendimiento por País
* **Corea del Sur** lidera en las tres áreas evaluadas (Matemática: 531, Lectura: 519, Ciencia: 531).
* **Irlanda** y **Nueva Zelanda** muestran rendimientos similares en ciencias (~505), con ventaja de Irlanda en matemáticas y lectura.
* **Argentina** presenta los puntajes más bajos, con una brecha pronunciada en matemáticas (388.8).

### 2. Relación ESCS-Rendimiento
Existe una **correlación positiva** consistente entre el índice ESCS y el rendimiento en todos los países. La relación más fuerte se encontró en **Argentina**, específicamente en **Matemáticas** (r = 0.424), lo que motivó un análisis profundo con regresión múltiple.

### 3. Modelo de Regresión Múltiple (Argentina - Matemáticas)
El modelo confirmó que el **ESCS es el predictor más sólido** (+25.02 puntos por unidad). El acceso a **internet** (+21.81) y **computadora** (+9.83) tienen impacto positivo. Se identificó una brecha de género a favor de los hombres (+10.60). Sorprendentemente, tener **habitación propia** mostró un efecto negativo (-7.37), lo que amerita mayor investigación.

### 4. Prueba de Hipótesis (2015 vs 2022)
Mediante la prueba de **Wilcoxon** (dado que los datos no siguen una distribución normal), se confirmó que existe una diferencia estadísticamente significativa entre los puntajes de matemáticas de 2015 y 2022.

## 🔬 Metodología Aplicada

1. **Análisis Exploratorio de Datos (EDA):** Visualización de distribuciones mediante box plots y gráficos de densidad por país y área.
2. **Análisis de Correlación:** Matriz de correlación entre puntuaciones y estatus socioeconómico.
3. **Regresión Lineal Simple:** Modelado de la relación ESCS-Matemáticas en Argentina (R² ajustado = 0.18).
4. **Regresión Múltiple:** Inclusión de variables de contexto (internet, computadora, habitación, género) para aislar efectos (R² ajustado = 0.1943).
5. **Evaluación de Supuestos:**
   * **Normalidad:** Prueba de Anderson-Darling, histograma y QQ-plot.
   * **Linealidad:** Test RESET de Ramsey y gráficos de residuos vs ajustados.
   * **Homocedasticidad:** Prueba de White.
   * **Independencia:** Análisis gráfico de residuos.
6. **Transformaciones:** Aplicación de transformaciones logarítmicas y polinomiales para corregir la falta de linealidad.
7. **Test de Hipótesis:** Pruebas de normalidad (**Shapiro-Wilk** y **Anderson-Darling**) y comparación de medianas mediante **Wilcoxon rank-sum test**.

## 🛠️ Requisitos y Estructura

### Paquetes de R necesarios

```r
install.packages(c("learningtowers", "dplyr", "tidyr", "ggplot2", 
                   "car", "lmtest", "nortest", "corrplot"))


## 📁 Estructura del repositorio

├── data/               # Datos fuente (Learning Towers)
├── scripts/            # Scripts de R del análisis
│   ├── 01_eda.R
│   ├── 02_correlacion.R
│   ├── 03_regresion_simple.R
│   ├── 04_regresion_multiple.R
│   ├── 05_supuestos_transformaciones.R
│   └── 06_test_hipotesis.R
├── outputs/            # Gráficos y resultados generados
├── Trabajo_Practico_Final.pdf   # Informe final en PDF
└── README.md
└── LICENSE                            # Licencia MIT
```

## ▶️ Cómo visualizar el proyecto

1. Descargá o cloná este repositorio:
  ```bash
  git clone https://github.com/Siguax/analisis-pisa-2022-rendimiento-socioeconomico.git
  ```
2. Abrí el archivo Trabajo_Practico_Final.pdf en cualquier visor de PDF (Adobe Acrobat, navegador web, etc.).
  -No necesitás instalar R para ver los resultados.
3. (Opcional) Si querés reproducir el análisis, abrí el archivo .Rmd en RStudio y ejecutá Knit para regenerar el PDF.

## ✅ Conclusión Final
En síntesis, esta investigación evidencia la profunda influencia del contexto socioeconómico en los resultados educativos, con variaciones significativas entre países. Los hallazgos subrayan la necesidad de políticas educativas que aborden las desigualdades de base y aprovechen el potencial de la tecnología como herramienta de equidad. El caso de Argentina resalta la urgencia de intervenciones focalizadas para mitigar el impacto de la desventaja socioeconómica en el desempeño académico, particularmente en matemáticas.

## ▶️ Ver el análisis completo
👉 [Hacé clic acá para ver el trabajo renderizado en PDF](https://github.com/Siguax/analisis-pisa-2022-rendimiento-socioeconomico/blob/main/Trabajo-Final-del-M%C3%B3dulo-4.pdf)

## 📄 Licencia
Distribuido bajo la licencia **MIT**. Consultá [`LICENSE`](LICENSE) para más detalles.

## 👩‍💻 Autora
Silvia Prevettoni

GitHub: @Siguax

LinkedIn: silvia-prevettoni

Email: silvia.prevettoni@gmail.com
