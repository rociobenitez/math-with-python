Práctica Final de Álgebra, Cálculo y Geometría con Python
=========================================================

Descripción
-----------

Este repositorio contiene la práctica final del módulo de Álgebra, Cálculo y Geometría, donde se aplican conceptos matemáticos y habilidades de programación en Python para resolver problemas complejos. La práctica se divide en cinco ejercicios principales, cada uno enfocado en un tema específico.

Archivo Principal
-----------------

*   `Practica.ipynb`: Jupyter Notebook que contiene todos los ejercicios y su desarrollo.

Carpetas Adicionales
--------------------

*   `images/`: Contiene imágenes utilizadas o generadas durante la práctica.
*   `data/`: Incluye el archivo CSV utilizado para los ejercicios de análisis de datos.

Contenido Detallado de `Practica.ipynb`
---------------------------------------

### 1\. Multiconjuntos

**Objetivos:**

*   Utilizar Python para manipular conjuntos.
*   Asegurar la comprensión de los fundamentos matemáticos de las operaciones con conjuntos.

**Problema:** Implementar operaciones con multiconjuntos utilizando diferentes estructuras de datos como diccionarios y listas, y la clase `Counter` de Python.

**Ejercicios:** Creación de funciones para operaciones básicas de multiconjuntos: `multiconjunto()`, `cardinalidad()`, `inserta()`, `elimina()`, `pertenece()`, `subconjunto()`, `iguales()`, `union()`, `interseccion()`, `diferencia()`.

### 2\. Singular Value Decomposition (SVD)

**Objetivos:**

*   Aplicar SVD para comprimir imágenes.
*   Entender los principios de SVD.

**Problema:** Usar SVD para la compresión de una imagen en blanco y negro.

**Ejercicios:** Uso de SVD en Python para la compresión de imágenes.

### 3\. Regresión Lineal - Mínimos Cuadrados

**Objetivos:**

*   Utilizar Python y Pandas para análisis de datos.
*   Comprender y aplicar el método de mínimos cuadrados.

**Problema:** Predicción del precio de viviendas usando el conjunto de datos de Kaggle's House Prices, aplicando mínimos cuadrados.

**Ejercicios:**

*   Creación de funciones para análisis y manipulación de datos: `inverse_of_matrix()`, `read_to_df(file_path)`, `select_columns(data_frame, column_names)`, `column_cutoff()`.
*   Implementación del método de mínimos cuadrados: `least_squares_weights(input_x, target_y)`.

### 4\. Regresión Lineal - Gradient Descent

**Objetivos:**

*   Comprender los fundamentos del Gradient Descent.

**Problema:** Predicción de precios de viviendas utilizando Gradient Descent.

**Ejercicios:** Implementación de Gradient Descent: `gradient_descent(x, y, w, iterations, eta)`.

### 5\. Similitud entre Páginas Web

**Objetivos:**

*   Usar Python y BeautifulSoup para web scraping.
*   Entender y aplicar cosine similarity para encontrar similitudes entre vectores.

**Problema:** Determinar la similitud entre diferentes páginas web extrayendo su contenido y calculando la cosine similarity.

**Ejercicios:**
*   Extracción de texto de páginas web: `parse_from_url()`, `get_content(url_ls)`.
*   Procesamiento de texto y cálculo de similitudes: `tokeniser()`, `combinations()`, `union()`, `set2vector()`, `cosine_similarity()`.


Aprendizajes y Reflexiones
--------------------------

Este reciente módulo ha sido una experiencia integral abarcando desde teoría y práctica con conjuntos hasta conceptos como eigenvectores y tensores. La combinación de temas clave como funciones, límites, derivadas, espacios vectoriales, matrices y regresión lineal, complementada con ejercicios prácticos en Python, ha ofrecido una visión completa y aplicada de las matemáticas.

A lo largo del curso, he apreciado la oportunidad de aplicar teorías matemáticas en contextos prácticos. Este enfoque ha reforzado mi comprensión teórica y ha mejorado mis habilidades de análisis y programación.
Mirando hacia adelante, estoy motivada para continuar explorando y aplicando lo aprendido en este módulo. La experiencia ha fortalecido mi interés en las matemáticas y la programación, y estoy deseosa de enfrentar los desafíos de los próximos módulos.