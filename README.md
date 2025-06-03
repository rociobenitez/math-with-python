# Ejercicios de Álgebra, Cálculo y Geometría con Python

## Introducción

Este repositorio agrupa una serie de ejercicios en Python centrados en **Álgebra, Cálculo y Geometría**, con el objetivo de aplicar conceptos teóricos a problemas prácticos mediante programación. Aquí encontrarás un cuaderno de Jupyter donde se desarrollan cinco bloques de trabajo, cada uno enfocado en un área específica de matemáticas aplicadas, así como los datos y las imágenes asociados.

## Índice

1. [Estructura del Repositorio](#estructura-del-repositorio)
2. [Requisitos y Configuración](#requisitos-y-configuración)
3. [Descripción de cada sección](#descripción-de-cada-sección)
   1. [Manipulación de Multiconjuntos](#manipulación-de-multiconjuntos)
   2. [Compresión de Imágenes mediante SVD](#compresión-de-imágenes-mediante-svd)
   3. [Regresión Lineal por Mínimos Cuadrados](#regresión-lineal-por-mínimos-cuadrados)
   4. [Regresión Lineal mediante Gradient Descent](#regresión-lineal-mediante-gradient-descent)
   5. [Similitud entre Páginas Web](#similitud-entre-páginas-web)
4. [Documentación de Funciones](#documentación-de-funciones)
5. [Resultados y Visualizaciones](#resultados-y-visualizaciones)
6. [Aprendizaje y Reflexión Personal](#aprendizaje-y-reflexión-personal)
7. [Ejecución y Reproducción](#ejecución-y-reproducción)

## Estructura del repositorio

```
.
├── data/
│   └── train.csv
├── images/
├── math_applications_with_python.ipynb
└── README.md
```

- `datatrain.csv`: Conjunto de datos utilizado en los ejercicios de regresión lineal (House Prices de Kaggle).
- `math_applications_with_python.ipynb`: Notebook principal con todas las secciones de desarrollo.
- `images/`: Carpeta que contiene las imágenes originales y las generadas durante la práctica.
- `README.md`: Documentación detallada de cada apartado, instrucciones de uso y recomendaciones.

## Requisitos y Configuración

1. **Entorno de Python**

   - Python 3.8+
   - Recomendada la creación de un entorno virtual con `venv` o `conda`.

2. **Dependencias**
   Se incluyen en un archivo `requirements.txt`, que puedes instalar mediante:

   ```bash
   pip install -r requirements.txt
   ```

   Al menos se requieren:

   - `numpy`
   - `pandas`
   - `matplotlib`
   - `scikit-learn` (opcional, para comparaciones rápidas)
   - `requests`
   - `beautifulsoup4`

3. **Ejecución**

   - Abre `math_applications_with_python.ipynb` en tu entorno (Jupyter Notebook o JupyterLab).
   - Ejecuta las celdas de cada sección en orden, asegurándote de tener la carpeta `data/` y `images/` en la misma ruta que el cuaderno.
   - Para la sección de regresión, la columna objetivo en `train.csv` es `SalePrice`, y el resto de columnas de interés pueden ajustarse según la disponibilidad de datos.

## Descripción de cada sección

Cada sección del cuaderno está diseñada para ilustrar tanto los fundamentos matemáticos como su implementación en Python. A continuación se describen los cinco bloques de trabajo:

### 1. Manipulación de Multiconjuntos

**Objetivo general**
Implementar las operaciones fundamentales sobre multiconjuntos (bags) en Python, usando estructuras de datos nativas (listas, diccionarios) y la clase `collections.Counter`.

**Conceptos Matemáticos**

- Definición de multiconjunto y cardinalidad.
- Relaciones de pertenencia, inclusión y comparación entre multiconjuntos.
- Operaciones de unión, intersección y diferencia.

**Desarrollo en Python**

- Funciones básicas:

  - `multiconjunto(iterable) → Counter`
  - `cardinalidad(c: Counter) → int`
  - `inserta(c: Counter, elemento) → None`
  - `elimina(c: Counter, elemento) → None`
  - `pertenece(c: Counter, elemento) → bool`
  - `subconjunto(c1: Counter, c2: Counter) → bool`
  - `iguales(c1: Counter, c2: Counter) → bool`

- Operaciones entre multiconjuntos:

  - `union(c1: Counter, c2: Counter) → Counter`
  - `interseccion(c1: Counter, c2: Counter) → Counter`
  - `diferencia(c1: Counter, c2: Counter) → Counter`

Cada función incluye:

1. Documentación con especificación de parámetros y valor de retorno.
2. Ejemplos de uso.
3. Pruebas rápidas con casos sencillos para validar el correcto funcionamiento.

### 2. Compresión de Imágenes mediante SVD

**Objetivo general**
Aplicar la **descomposición en valores singulares** a una imagen en escala de grises, comprimiéndola sin perder demasiada información visual.

**Conceptos Matemáticos**

- Descomposición SVD:

  $$
    A = U \, \Sigma \, V^\top
  $$

  donde $A$ es la matriz de píxeles de la imagen.

- Principios de compresión: conservar solo los primeros $k$ valores singulares.
- Error de reconstrucción y calidad percibida según el número de componentes retenidos.

**Desarrollo en Python**

1. Lectura y conversión de la imagen a una matriz numérica (usando `matplotlib.image` o `PIL`).
2. Cálculo de la SVD con `numpy.linalg.svd`.
3. Función `comprimir_svd(imagen: np.ndarray, k: int) → np.ndarray` que:

   - Selecciona los primeros $k$ valores singulares y vectores asociados.
   - Reconstruye la imagen aproximada.
   - Muestra comparativas (imagen original vs. comprimida) y calcula el error relativo (por ejemplo, norma Frobenius).

4. Ejemplos para distintos valores de $k$ (por ej., 10, 50, 100), incluyendo visualización con `matplotlib.pyplot`.

### 3. Regresión Lineal por Mínimos Cuadrados

**Objetivo general**
Implementar desde cero el método de mínimos cuadrados para regresión lineal y aplicarlo al conjunto de datos `train.csv` de precios de viviendas.

**Conceptos Matemáticos**

- Formulación matricial de la regresión lineal:

  $$
    \mathbf{y} = X \, \beta + \epsilon, \quad \beta = (X^\top X)^{-1} X^\top \mathbf{y}
  $$

- Pseudoinversa en caso de colinealidad.
- Interpretación de los coeficientes obtenidos, error cuadrático medio (MSE) y evaluación sobre subconjunto de datos.

**Desarrollo en Python**

1. Lectura y preprocesamiento de `train.csv` usando `pandas`:

   - `read_to_df(ruta: str) → pd.DataFrame`
   - Selección de variables relevantes: `select_columns(df, columnas: List[str]) → pd.DataFrame`
   - Función `column_cutoff(df: pd.DataFrame, umbral: float) → pd.DataFrame` para eliminar variables con baja varianza o muchos valores nulos.

2. Construcción de la matriz de diseño $X$ y vector objetivo $\mathbf{y}$.
3. Función `inverse_of_matrix(A: np.ndarray) → np.ndarray` (con chequeo de determinante para evitar singularidad).
4. Función `least_squares_weights(X: np.ndarray, y: np.ndarray) → np.ndarray` que calcula $\beta$.
5. Cálculo de predicciones y métricas de desempeño:

   - Error cuadrático medio (MSE).
   - Coeficiente de determinación $R^2$.

6. Visualización de resultados (por ejemplo, dispersión vs. predicciones).

### 4. Regresión Lineal mediante Gradient Descent

**Objetivo general**
Implementar el algoritmo de Gradient Descent para encontrar los coeficientes de regresión lineal y comparar convergencia y resultados con mínimos cuadrados.

**Conceptos Matemáticos**

- Definición de la función de costo:

  $$
    J(\beta) = \frac{1}{2m} \sum_{i=1}^{m} \bigl(X_i^\top \beta - y_i \bigr)^2.
  $$

- Derivada parcial con respecto a $\beta$.
- Regla de actualización:

  $$
    \beta \leftarrow \beta - \eta \, \nabla J(\beta).
  $$

**Desarrollo en Python**

1. Función `gradient_descent(X: np.ndarray, y: np.ndarray, w_init: np.ndarray, iterations: int, eta: float) → np.ndarray`:

   - `X`: matriz de diseño (incluye columna de 1s para el término independiente).
   - `y`: vector de valores.
   - `w_init`: vector de pesos iniciales (por ejemplo, ceros o valores pequeños aleatorios).
   - `iterations`: número de iteraciones a ejecutar.
   - `eta`: tasa de aprendizaje (learning rate).

2. Monitorización de la función de costo en cada iteración para graficar la convergencia.
3. Comparación entre los pesos obtenidos por descenso de gradiente y los obtenidos por mínimos cuadrados (porcentajes de error relativos).
4. Visualización de la curva de aprendizaje y análisis del efecto de $\eta$ y el número de iteraciones.

### 5. Similitud entre Páginas Web

**Objetivo general**
Extraer contenido textual de páginas web mediante web scraping, procesar el texto para generar vectores de características y calcular la similitud de cosenos entre ellos.

**Conceptos Matemáticos**

- Representación de documentos como vectores de frecuencia de términos (bag of words).
- Cálculo de la similitud de cosenos:

  $$
    \text{sim}(D_i, D_j) = \frac{\vec{v}_i \cdot \vec{v}_j}{\|\vec{v}_i\| \, \|\vec{v}_j\|}.
  $$

**Desarrollo en Python**

1. Web scraping con `requests` y `BeautifulSoup`:

   - `parse_from_url(html_content: str) → str` para limpiar etiquetas HTML y extraer texto básico.
   - `get_content(url_list: List[str]) → Dict[str, str]` que devuelve un diccionario URL → texto plano.

2. Procesamiento de texto:

   - Tokenización con función `tokeniser(texto: str) → List[str]` (eliminar stopwords, normalizar a minúsculas, remover puntuación).
   - Generación de vocabulario conjunto (`union(vocab1, vocab2) → Set[str]`) y construcción de vectores de frecuencia:

     - `set2vector(vocab: List[str], tokens: List[str]) → List[int]`.

3. Cálculo de similitud:

   - Función `cosine_similarity(v1: List[int], v2: List[int]) → float`.
   - Pruebas entre distintos pares de URLs y visualización de la matriz de similitud (heatmap con `matplotlib`).

## Documentación de Funciones

En cada bloque de código, las funciones vienen documentadas en formato de docstring estándar:

```python
def nombre_de_funcion(param1: Tipo, param2: Tipo) -> TipoDevuelto:
    """
    Descripción breve de la función.

    Parámetros:
    ----------
    param1 : Tipo
        Explicación de param1.
    param2 : Tipo
        Explicación de param2.

    Retorna:
    -------
    TipoDevuelto
        Descripción del valor de retorno.
    """
    # Implementación
```

Estos docstrings permiten:

- Comprender rápidamente qué hace cada función.
- Saber los tipos esperados y lo que devuelven.
- Facilitar la generación automática de documentación si se desea exportar a formato HTML o PDF.

## Resultados y Visualizaciones

- **Sección SVD**:

  - Gráficos comparativos entre la imagen original y las aproximaciones con distintos valores de $k$.
  - Cálculo del error relativo en norma Frobenius para cada $k$.

- **Secciones de Regresión**:

  - Dispersión de las predicciones frente a los valores reales.
  - Curva de aprendizaje (función de costo vs. iteraciones) para Gradient Descent.
  - Tabla resumen de métricas (MSE, $R^2$) comparando métodos.

- **Sección de Similitud Web**:

  - Heatmap de la matriz de similitud entre URLs evaluadas.
  - Ejemplos de pares de páginas con similitud alta/baja.

Las imágenes generadas se almacenan automáticamente en la carpeta `images/` y están comentadas en el cuaderno para facilitar su seguimiento.

## Aprendizaje y Reflexión personal

> A lo largo de este trabajo, he podido profundizar en la relación entre teoría matemática (álgebra lineal, cálculo de errores y medidas de similitud) y su aplicación programática en Python.
>
> Si bien los conceptos teóricos son complejos, la implementación paso a paso me ha ayudado a reforzar la comprensión de temas como:
>
> - Procesamiento de datos matriciales (SVD).
> - Formulación de problemas de optimización (método de mínimos cuadrados vs. Gradient Descent).
> - Técnicas de web scraping y procesamiento de texto para comparar documentos.
>
> Además, la documentación cuidadosa de cada función y la presentación de resultados visuales ha mejorado mi capacidad para estructurar proyectos de forma profesional y reproducible.

## Ejecución y Reproducción

1. Clonar el repositorio:

   ```bash
   git clone https://github.com/tu-usuario/nombre-repositorio.git
   cd nombre-repositorio
   ```

2. Crear e instalar dependencias:

   ```bash
   python -m venv venv
   source venv/bin/activate      # En Linux/macOS
   # venv\Scripts\activate.bat   # En Windows
   pip install -r requirements.txt
   ```

3. Abrir el cuaderno:

   ```bash
   jupyter notebook math_applications_with_python.ipynb
   ```

4. Seguir las instrucciones dentro del notebook.
