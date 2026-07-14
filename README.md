# Análisis y Predicción del Abandono de Clientes (*Churn*) en Banca Minorista

## Descripción del Proyecto
Este proyecto fue desarrollado en el marco del **Seminario en Ciencia de Datos I (1°C 2026)** de la **Universidad CAECE**. 

El objetivo principal es resolver un problema crítico en la banca minorista: la fuga de clientes (*churn*). A través de un enfoque metodológico riguroso, el proyecto abarca desde el Análisis Exploratorio de Datos (EDA) hasta la implementación de modelos de aprendizaje supervisado y técnicas de Inteligencia Artificial Explicable (XAI) para interpretar las decisiones del modelo.

* **Caso de estudio:** Dataset histórico de 10.000 clientes de una entidad bancaria europea (Francia, Alemania y España).
* **Tasa de abandono base:** 20,37% (Clases desbalanceadas).

## Principales Hallazgos (Negocio)
A través del análisis descriptivo y predictivo, se logró identificar el perfil de alto riesgo de fuga:
* **Efecto No Lineal de Productos:** Los clientes con 2 productos contratados son los más estables (7,58% de churn). Sin embargo, poseer 3 o 4 productos dispara el abandono al 82,71% y 100% respectivamente.
* **Concentración Geográfica:** Alemania casi duplica la tasa de abandono de Francia y España (32,44% vs. ~16%).
* **Edad:** El riesgo se incrementa de forma no monótona, alcanzando su pico en el rango de 50-59 años (56,04% de churn).
* **Estado:** Los clientes inactivos duplican la propensión de fuga frente a los activos.

## Stack Tecnológico
* **Lenguaje:** Python (Google Colab)
* **Manipulación de Datos:** Pandas, NumPy
* **Visualización:** Mattplotlib, Seaborn, Plotly (Tablero interactivo)
* **Machine Learning:** Scikit-learn (Regresión Logística, Random Forest)
* **IA Explicable (XAI):** SHAP (SHapley Additive exPlanations)

## Evaluación y Comparación de Modelos
Dado el desbalance de clases, la evaluación se centró en el **Recall** y el **F1-Score** sobre el conjunto de prueba (20% de los datos), priorizando la reducción de falsos negativos (clientes en riesgo no detectados).

| Métrica | Regresión Logística (Baseline) | Random Forest |
| :--- | :---: | :---: |
| **Accuracy** | 0.8080 | 0.8610 |
| **Precision** | 0.5891 | 0.7670 |
| **Recall (Sensibilidad)** | 0.1867 | **0.4520** |
| **F1-Score** | 0.2836 | **0.5690** |
| **AUC-ROC** | 0.7748 | **0.8560** |

*El modelo Random Forest superó ampliamente a la línea base lineal, duplicando la capacidad de detección de clientes en riesgo (Recall de 45.2%).*

## Inteligencia Artificial Explicable (XAI) con SHAP
Para evitar un modelo de "caja negra", se utilizaron valores SHAP. Esto permitió:
1. Confirmar que la **Edad** y la **Cantidad de Productos** son los principales impulsores del abandono.
2. **Corregir sesgos algorítmicos:** El análisis tradicional por impureza de Random Forest posicionaba al salario estimado como una variable importante por ser continua. SHAP demostró que su impacto real en la predicción del negocio es marginal, aportando transparencia y auditoría ética al modelo.

##  Estructura del Repositorio
* `/notebooks`: Contiene el código fuente documentado paso a paso.
* `/dashboard`: Incluye el tablero interactivo exportado en HTML.
* `/reports`: Contiene el informe técnico detallado y el paper científico con formato académico.

##  Integrantes del Proyecto
* Frati, Gianluca
* Libutzki, Lucila
* Suárez, Dante
* **Docente:** Ing. Fabiana B. Taboada — Universidad CAECE
