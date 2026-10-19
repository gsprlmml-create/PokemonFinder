# 🔴 PokéVGC Dashboard: Pokédex Inteligente con YOLOv8 e IA Generativa

Aplicación web interactiva desarrollada para el proyecto del módulo, la cual integra visión artificial, análisis de datos estadísticos y un modelo de lenguaje (LLM) para ofrecer un asistente táctico y de reconocimiento de especies Pokémon enfocado en combate competitivo (VGC).

---

## 👥 Integrantes del Grupo
* Gaspar Lämmel


---

## 📋 1. Problema y Motivación
La clasificación visual manual de especies y el análisis rápido de sus atributos en entornos dinámicos puede ser complejo. Este proyecto resuelve la necesidad de identificar automáticamente una especie a partir de una imagen mediante un modelo de aprendizaje profundo (**YOLOv8**), complementando la clasificación con un análisis estructurado de sus estadísticas base y generando recomendaciones tácticas automatizadas mediante Inteligencia Artificial Generativa (**Google Gemini**).

---

## 📊 2. Datos y Ficha Técnica
* **Origen del Dataset:** Combinación de datos tabulares de estadísticas base (`pokemon.csv`) y secuencias evolutivas, basados en registros oficiales de PokéAPI y datasets públicos de Kaggle.
* **Licencia:** Open Database License (ODbL) / Uso educativo.
* **Clasificación y Clases:** El modelo de visión está entrenado para clasificar un subconjunto de especies representativas de Pokémon.
* **División del Dataset:** El conjunto de datos se dividió en entrenamiento (70%), validación (15%) y prueba (15%).
* **Limitaciones y Sesgos:** El dataset puede presentar sesgos en las condiciones de iluminación o variaciones de estilo artístico de las imágenes de prueba frente a las fotos de entrenamiento.

---

## 🧠 3. Modelo y Justificación
* **Modelo Elegido:** **Ultralytics YOLOv8n-cls** (clasificación de imágenes).
* **Justificación:** Se seleccionó YOLO por su alta eficiencia, bajo peso en almacenamiento (pesos livianos de ~3 MB que caben perfectamente en GitHub) y rapidez de inferencia en tiempo real en comparación con redes convolucionales tradicionales más pesadas o modelos de visión más complejos sin GPU dedicada.
* **Métricas en Conjunto de Prueba:** El modelo fue evaluado obteniendo métricas de *Accuracy* y matriz de confusión en la fase de validación, priorizando minimizar los errores de clasificación en especies con estadísticas similares. El error más costoso en este contexto corresponde a confundir especies ofensivas clave con soportes de baja ofensiva, lo cual alteraría la recomendación táctica.

---

## 💻 4. Estructura del Repositorio
```text
mi-proyecto/
├── PokemonFinder.py          ← Aplicación principal en Streamlit
├── requirements.txt          ← Dependencias y librerías de Python
├── README.md                 ← Documentación completa del proyecto
├── notebooks/
│   └── entrenamiento.ipynb   ← Notebook de Colab con entrenamiento y métricas
├── modelo/
│   └── best.pt               ← Pesos entrenados del modelo YOLOv8
└── ejemplos/                 ← Imágenes de prueba para la demo
