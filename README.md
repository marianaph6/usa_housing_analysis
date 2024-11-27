
# README: USA Housing Analysis

Este proyecto realiza el análisis de datos de precios de viviendas en los Estados Unidos y utiliza modelos de Machine Learning para predecir los precios basados en sus características. El análisis se ejecuta completamente desde un único archivo **Jupyter Notebook**.

---

## **Requisitos Previos**

### **1. Python**
Asegúrate de tener Python instalado (preferiblemente 3.8 o superior).

### **2. Instalar Poetry**
**Poetry** se utiliza para gestionar dependencias y entornos virtuales. Instálalo con:
```bash
curl -sSL https://install.python-poetry.org | python3 -
```

Confirma la instalación:
```bash
poetry --version
```

### **3. Instalar Jupyter Notebook**
Aunque Jupyter se incluye en las dependencias, asegúrate de tenerlo correctamente configurado en tu sistema.

### **4. Instalar Git**
Clona el proyecto desde un repositorio utilizando Git.

---

## **Estructura del Proyecto**

Dado que el proyecto está en un solo archivo, su estructura es simple:

```plaintext
usa_housing_analysis/
├── usa_housing_analysis.ipynb  # Notebook principal
├── pyproject.toml              # Configuración de 
├── poetry.lock                 # Archivo de bloqueo de 
└── mlruns/                     # Carpeta de tracking de MLFlow (se crea al usar MLFlow)
```

---

## **Instrucciones de Instalación**

1. **Clona el Proyecto**
   ```bash
   git clone https://github.com/<tu-usuario>/usa_housing_analysis.git
   cd usa_housing_analysis
   ```

2. **Instala las Dependencias**
   Usa **Poetry** para instalar todas las dependencias necesarias:
   ```bash
   poetry install
   ```

3. **Activa el Entorno Virtual**
   Para trabajar dentro del entorno del proyecto, activa el shell de Poetry:
   ```bash
   poetry shell
   ```

---

## **Ejecución del Proyecto**

### **1. Iniciar el Notebook**
Ejecuta el archivo Jupyter Notebook para comenzar el análisis:
```bash
cd usa_housing_analysis
poetry run jupyter notebook usa_housing_analysis.ipynb
```

Esto abrirá el notebook en tu navegador.

### **2. Visualizar Experimentos en MLFlow**
Para revisar los resultados de los modelos y las métricas registradas, inicia el servidor de MLFlow:
```bash
mlflow ui
```

Accede a la interfaz en `http://127.0.0.1:5000` para explorar los experimentos.

---

## **Contenido del Notebook**

El archivo **usa_housing_analysis.ipynb** incluye las siguientes secciones:

### **1. Carga de Datos**
Carga y exploración de los datos de precios de viviendas, incluyendo estadísticas descriptivas y visualización.

### **2. Limpieza de Datos**
- Manejo de valores nulos en columnas numéricas y categóricas.
- Eliminación de columnas irrelevantes como `Id`.
- Imputación basada en mediana (para numéricas) y moda (para categóricas).

### **3. Creación de Nuevas Características**
Nuevas columnas diseñadas para mejorar la predicción:
- `YearsSinceBuilt`: Años desde la construcción.
- `YearsSinceRemodel`: Años desde la última remodelación.
- `LotAreaPerGrLivArea`: Proporción entre el área del lote y el área habitable.
- Indicadores binarios (`HasGarage`, `HasPool`, `HasFireplace`).

### **4. Análisis Exploratorio**
- Matriz de correlación para identificar relaciones entre variables.
- Visualización de distribuciones de las características más relevantes.

### **5. Entrenamiento de Modelos**
- **Random Forest Regressor:** Entrenamiento y ajuste de hiperparámetros con GridSearchCV.
- **XGBoost Regressor:** Entrenamiento para comparación con Random Forest.

### **6. Evaluación de Modelos**
Se evalúan ambos modelos usando:
- **RMSE (Root Mean Squared Error):** Error promedio cuadrático.
- **R² (Coeficiente de Determinación):** Medida de ajuste del modelo.

### **7. Registro de Modelos con MLFlow**
- Ambos modelos (Random Forest y XGBoost) son registrados en **MLFlow** con sus métricas y parámetros.
- Los modelos entrenados se almacenan como artefactos en `mlruns`.

### **8. Análisis de Residuos**
Visualización de residuos para diagnosticar errores del modelo.

---

## **Comandos Clave**

### **Ejecutar el Notebook**
```bash
cd proyecto
poetry run jupyter notebook usa_housing_analysis.ipynb
```

### **Explorar Notebooks Adicionales**
```bash
poetry run jupyter notebook
```

### **Iniciar MLFlow**
```bash
mlflow ui
```

### **Salir del Entorno Virtual**
```bash
exit
```

---

## **Dependencias**

Las dependencias del proyecto están definidas en `pyproject.toml`. Incluyen:

- `pandas`: Manipulación de datos.
- `numpy`: Operaciones numéricas.
- `matplotlib` y `seaborn`: Visualización.
- `scikit-learn`: Algoritmos de Machine Learning.
- `xgboost`: Modelo de boosting.
- `mlflow`: Gestión de experimentos y modelos.
- `notebook` y `ipykernel`: Para trabajar con Jupyter Notebooks.

---

## **Notas Finales**
- Asegúrate de ejecutar `mlflow ui` en una terminal separada para visualizar los resultados.
- Este proyecto está diseñado para ser fácilmente reproducible gracias a **Poetry** y **MLFlow**.

¡Explora los datos y crea modelos predictivos precisos con este proyecto de análisis de viviendas! 🚀
