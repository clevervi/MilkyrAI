# 🧠 Sistema de Clasificación de Imágenes con TensorFlow - MilkyrAI

## 📌 Descripción General
Este proyecto implementa un sistema robusto de clasificación de imágenes utilizando modelos preentrenados de TensorFlow. El sistema está diseñado para ser ejecutado en Google Colab y permite clasificar imágenes en diferentes categorías con análisis detallado de resultados.

**Versión:** 2.1.0  
**Autor:** Clevervi  
**Fecha:** 2025-01-05  

## 🎯 Objetivo del Proyecto
Crear una herramienta completa que permita:
- Clasificar imágenes en diferentes categorías
- Analizar las predicciones con métricas detalladas
- Visualizar resultados de manera profesional
- Manejar errores y logs sistemáticamente
- Funcionar tanto en Google Colab como localmente

## 🏗️ Estructura del Proyecto Recomendada

```
C:.
│   .gitignore                    # Archivos y carpetas a ignorar en Git
│   main.ipynb                    # Notebook principal (Colab)
│   README.md                     # Este archivo
│   requirements.txt              # Dependencias del proyecto
│
├───config
│       settings.yaml             # Configuraciones del sistema
│
├───data                          # Datos e imágenes para clasificación
│   └───images                   # Imágenes de prueba
│
├───models                        # Modelos entrenados
│       labels.txt               # Etiquetas de clasificación
│       model.h5                 # Modelo preentrenado
│
├───notebooks                     # Notebooks de desarrollo
│       main.ipynb               # Notebook principal (local)
│
└───src                          # Código fuente
        main.py                  # Script principal ejecutable
        image_processor.py       # Procesamiento de imágenes
        model_manager.py         # Gestión de modelos
        visualizer.py            # Visualizaciones
        utils.py                 # Funciones auxiliares
```

## 📦 Instalación y Configuración

### Para Usuarios Técnicos (Desarrolladores)

1. **Clonar el repositorio:**
```bash
git clone <url-del-repositorio>
cd <nombre-del-proyecto>
```

2. **Instalar dependencias:**
```bash
pip install -r requirements.txt
```

3. **Configurar rutas:**
   - Modificar `config/settings.yaml` según tu entorno
   - Asegurar que los archivos del modelo estén en `models/`

### Para Usuarios No Técnicos (Google Colab)

1. **Abrir Google Colab:**
   - Ve a [colab.research.google.com](https://colab.research.google.com)
   - Sube el archivo `main.ipynb`

2. **Ejecutar paso a paso:**
   - Ejecuta cada celda en orden
   - El sistema instalará automáticamente todo lo necesario
   - Monta tu Google Drive cuando se solicite

## 🚀 Características Principales

### ✅ Para Usuarios Técnicos
- **Arquitectura modular:** Código organizado en clases y funciones reutilizables
- **Manejo de errores:** Sistema robusto con logging profesional
- **Optimización:** Soporte para GPU/TPU con TensorFlow
- **Extensible:** Fácil de modificar y ampliar
- **Documentación:** Código bien comentado y tipado

### ✅ Para Usuarios No Técnicos
- **Interfaz simple:** Solo ejecutar celdas en orden
- **Visualizaciones claras:** Gráficos profesionales y fáciles de entender
- **Reportes detallados:** Resultados en lenguaje natural
- **Automatización:** No requiere conocimiento de programación
- **Guía paso a paso:** Instrucciones claras en cada celda

## 🔧 Componentes Técnicos Detallados

### 1. **Configuración del Sistema**
- Clase `Config` centralizada con parámetros ajustables
- Directorios automáticos para resultados y logs
- Reproducibilidad con semillas configurables

### 2. **Procesamiento de Imágenes**
- **ImageProcessor:** Carga y preprocesamiento de múltiples formatos
- **Análisis automático:** Dimensiones, intensidad, histogramas
- **Normalización:** Preparación para modelos TensorFlow

### 3. **Gestión de Modelos**
- **ModelManager:** Carga segura de modelos con compatibilidad
- **Predicciones con análisis:** Top-K, confianzas, tiempos
- **Metadatos:** Información completa del modelo

### 4. **Visualización**
- **VisualizationEngine:** Gráficos profesionales con matplotlib
- **Análisis completo:** Imágenes originales, heatmaps, distribuciones
- **Exportación:** Guardado automático en alta calidad

### 5. **Reportes**
- **Reportes detallados:** Explicaciones en lenguaje natural
- **Interpretación:** Niveles de confianza y recomendaciones
- **Exportación:** Resultados en múltiples formatos

## 📊 Categorías de Clasificación

El sistema está configurado para clasificar:
1. **Placas de licencia** (Categoría 0)
2. **Rostros humanos** (Categoría 1)

*(Nota: Estas categorías se pueden modificar editando `models/labels.txt`)*

## 🎮 Cómo Usar

### Paso 1: Preparación
1. Sube tus imágenes a la carpeta `data/images/`
2. Asegúrate de tener el modelo `model.h5` y `labels.txt`

### Paso 2: Clasificación
```python
# Ejemplo de uso programático
from src.main import ImageClassificationSystem

system = ImageClassificationSystem()
resultados = system.classify_image("ruta/de/tu/imagen.jpg")
```

### Paso 3: Análisis
- Revisa los gráficos generados
- Lee el reporte detallado
- Exporta resultados si es necesario

## 📈 Métricas y Análisis

El sistema proporciona:
- **Confianza por categoría:** 0-100% para cada predicción
- **Tiempo de inferencia:** Milisegundos por predicción
- **Análisis de decisión:** Gap entre categorías, márgenes
- **Estadísticas de imagen:** Tamaño, intensidad, colores

## 🔍 Ejemplo de Resultado

```
📋 REPORTE DETALLADO DE PREDICCIÓN
========================================
🎯 RESULTADO PRINCIPAL:
  🏷️  Etiqueta: 1 Faces
  🎯 Confianza: 99.99%
  📊 Estado: ✅ ACEPTADA

📈 ANÁLISIS DE DECISIÓN:
  📏 Gap con segunda opción: 0.9998
  🔢 Clases sobre umbral: 1/2

🏆 TOP PREDICCIONES:
  1. ✅ 1 Faces (99.99%)
  2. ⚠️  0 license plates (0.01%)
```

## ⚙️ Configuración Avanzada

### Parámetros Ajustables en `config/settings.yaml`:
```yaml
model:
  input_size: [224, 224]
  confidence_threshold: 0.5
  top_k_predictions: 5

visualization:
  plot_style: darkgrid
  figure_size: [12, 8]
  color_map: viridis

system:
  seed: 42
  device: auto  # auto, cpu, gpu
  verbose: 1
```

## 🐛 Solución de Problemas

### Problemas Comunes:

1. **"Modelo no encontrado"**
   - Verifica que `model.h5` esté en `models/`
   - Comprueba las rutas en la configuración

2. **"Error al cargar imagen"**
   - Formatos soportados: JPG, PNG, BMP, TIFF, WEBP
   - Verifica permisos y tamaño del archivo

3. **"GPU no disponible"**
   - En Colab: Activar GPU en Runtime → Change runtime type
   - Localmente: Instalar drivers CUDA si corresponde

### Logs y Depuración:
- Los logs se guardan en `logs/image_classification.log`
- Niveles: INFO, WARNING, ERROR
- Timestamps para seguimiento temporal

## 📚 Recursos y Referencias

### Documentación Técnica:
- [TensorFlow Documentation](https://www.tensorflow.org/)
- [OpenCV Documentation](https://docs.opencv.org/)
- [Matplotlib Documentation](https://matplotlib.org/)

### Para Aprender Más:
1. **Aprendizaje Automático:** Curso de Andrew Ng en Coursera
2. **Procesamiento de Imágenes:** OpenCV University
3. **Visualización de Datos:** Data Visualization with Python

## 🤝 Contribución

### Para Desarrolladores:
1. Fork el repositorio
2. Crea una rama para tu feature
3. Sigue las convenciones de código existentes
4. Añade tests para nuevas funcionalidades
5. Envía un Pull Request

### Guía de Estilo:
- Python: PEP 8
- Docstrings: Google style
- Commits: Conventional commits

## 📄 Licencia
MIT License - Ver archivo LICENSE para detalles

## 📞 Soporte y Contacto

### Para Problemas Técnicos:
- Abre un Issue en GitHub
- Incluye logs y pasos para reproducir

### Para Preguntas Generales:
- Revisa primero la documentación
- Consulta ejemplos en `notebooks/examples/`

## 🚀 Próximas Mejoras

### Planeado para v3.0:
- [ ] Soporte para video en tiempo real
- [ ] API REST para despliegue
- [ ] Más modelos preentrenados
- [ ] Interfaz web con Streamlit
- [ ] Análisis de batch automático
