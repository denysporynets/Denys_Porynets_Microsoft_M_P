# Denys_Porynets_Microsoft_M_P
Modelo de Machine Learning para detección de malware basado en 9M de registros, procesados íntegramente en un portátil de 8 GB. Ingeniería de variables avanzada y validación estratificada, con AUC 0.7356.

# 🛡️ Microsoft Malware Prediction: Arquitectura DS-NEXUS

[![Python](https://img.shields.io/badge/Python-3.9+-blue.svg)](https://www.python.org/)
[![LightGBM](https://img.shields.io/badge/Model-LightGBM-green.svg)](https://lightgbm.readthedocs.io/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

## 📋 Resumen del Proyecto
Este proyecto aborda el desafío de predecir la infección por malware en 9 millones de dispositivos Windows, utilizando un dataset de **Big Data (14GB+)** procesado íntegramente en un entorno local con recursos restringidos (MacBook M2, 8GB RAM).

**Logro principal:** Implementación de un pipeline de ingeniería de datos que redujo el consumo de memoria en un **85%**, alcanzando un **AUC de 0.7356** sobre el conjunto de validación.

> **Sobre la comparación con Kaggle:** la competición original se movía en 0.67–0.71, pero ese número no es directamente comparable con este. Allí se puntuaba contra un conjunto de prueba desplazado en el tiempo; aquí la validación es un corte aleatorio estratificado del mismo fichero de entrenamiento, que es un examen más benévolo.

---

## 🧠 Metodología: El Protocolo DS-NEXUS
A diferencia de los enfoques tradicionales de "fuerza bruta", este proyecto se diseñó bajo el principio de **Ingeniería Incremental**:

1.  **Filtro 80/20:** Identificación de las variables críticas (20%) que generan el mayor impacto predictivo (80%).
2.  **Optimización Quirúrgica:** Tipado estricto de datos (`int8`, `category`) y carga selectiva de columnas desde disco.
3.  **Parsing Vectorial:** Deconstrucción de jerarquías de software (Versiones de Engine/App) en señales numéricas procesables.



---

## 🛠️ Stack Tecnológico
* **Lenguaje:** Python
* **Procesamiento:** Pandas (Vectorización), NumPy
* **Modelado:** LightGBM (Gradient Boosting)
* **Visualización:** Plotly (Gráficos interactivos de importancia y ROC)
* **Persistencia:** Joblib para serialización de modelos y reglas de limpieza.

---

## 📊 Hallazgos Clave

### Importancia de Variables (Feature Importance)
El modelo detectó que la **obsolescencia del software** es el mayor vector de riesgo. Las sub-versiones de las firmas del antivirus (`AvSigVersion`) resultaron ser más predictivas que la versión principal.

### Matriz de Confusión
Se logró un **punto de equilibrio operativo**:
* **Verdaderos Positivos:** ~589k amenazas interceptadas.
* **Equilibrio de Errores:** Simetría entre falsos positivos y negativos, garantizando seguridad sin penalizar la experiencia del usuario.



---

## 🚀 Cómo ejecutarlo
1.  Clona el repositorio: `git clone https://github.com/tu-usuario/malware-prediction.git`
2.  Instala las dependencias: `pip install -r requirements.txt`
3.  Ejecuta el notebook en `notebooks/0226_MLSup_Denys_Porynets.ipynb`

> **Nota sobre los datos:** Debido al tamaño del dataset original (Microsoft Malware Prediction - Kaggle), los archivos `.csv` no están incluidos en el repo. Deben descargarse y colocarse en la carpeta `/data`.

---

**Autor:** Denys Porynets  
**Contacto:** www.linkedin.com/in/denys-porynets
