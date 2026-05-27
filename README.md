# Motor de Búsqueda Semántica con FAISS y Análisis PCA

## Descripción

Este proyecto implementa un motor de búsqueda semántica sobre reseñas de películas de Rotten Tomatoes. Utiliza dos modelos de embeddings (`all-MiniLM-L6-v2` y `all-mpnet-base-v2`), índices FAISS para búsqueda eficiente y un análisis de reducción de dimensionalidad (PCA) para visualizar los embeddings coloreados por sentimiento (Fresh/Rotten).
Instalar dependencias del documento txt

## Requisitos previos

- Python 3.8 o superior
- Jupyter Notebook / JupyterLab / Google Colab
- Conexión a internet (para descargar el dataset y los modelos)

# Autor

Andrés Pérez

## Instalación y ejecución

1. **Clona este repositorio** o descarga el archivo `perezandres_ex1bim_ir26a.ipynb`.

2. **Abre el notebook** en Jupyter, VSCode o súbelo a Google Colab.

3. **Ejecuta todas las celdas en orden**. La primera celda instalará automáticamente las librerías necesarias:
   - `kagglehub` (descarga del dataset)
   - `sentence-transformers` (embeddings)
   - `faiss-cpu` (búsqueda vectorial)
   - `pandas`, `matplotlib`, `scikit-learn`, `spacy`

   También descargará el modelo de spaCy `en_core_web_sm` para el preprocesamiento de texto.

4. **Sigue la salida en cada celda**:
   - Se descargará el dataset de Kaggle (Rotten Tomatoes).
   - Se preprocesarán 5000 reseñas (limpieza, lematización, eliminación de stopwords).
   - Se generarán embeddings con ambos modelos (puede tomar unos minutos).
   - Se construirán los índices FAISS.
   - Se ejecutarán automáticamente **8 consultas predefinidas**, mostrando tablas de resultados (Top-5) para cada modelo, más un resumen general (Top-1).
   - Aparecerá una **interfaz interactiva** donde puedes escribir tus propias consultas (escribe `salir` para terminar).
   - Finalmente, se mostrará un **gráfico PCA** de los embeddings del modelo `all-mpnet-base-v2`, coloreado por tipo de reseña (Fresh = verde, Rotten = rojo).

## Interfaz de consulta

Escribe una frase en inglés (por ejemplo, `"intense action thriller full of explosions"`) y presiona Enter. El sistema te mostrará los 5 documentos más relevantes para cada modelo, junto con su puntuación de similitud y el tiempo de respuesta.

## Personalización

- Puedes cambiar el número de resultados modificando el parámetro `top_k` en la celda de la interfaz.
- Para usar más documentos, ajusta el `head(5000)` en la carga de datos (ten en cuenta los recursos de memoria).

## Resultados esperados

- Tablas comparativas de ambos modelos de embeddings.
- Tiempos de generación y búsqueda.
- Gráfico de dispersión 2D con los embeddings proyectados.

## Solución de problemas

- Si la descarga del dataset falla, verifica tu conexión a internet y que `kagglehub` esté actualizado.
- Si el notebook se ejecuta en local y no tienes GPU, la generación de embeddings será más lenta pero igualmente funcional.
- Para salir de la interfaz interactiva, escribe `salir`, `exit` o `quit`.
