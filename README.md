# Arquitectura Escalable para el Análisis Climático en Python 

Este proyecto es una aplicación web interactiva desarrollada con **Shiny for Python** diseñada para el análisis y visualización eficiente de datos climáticos multidimensionales (formato ERA5 `.nc`). La arquitectura está pensada para ser modular, escalable y capaz de soportar múltiples usuarios simultáneos mediante el procesamiento asíncrono y la carga perezosa de datos.

## Objetivo
Desarrollar una plataforma web interactiva capaz de visualizar variables climáticas (temperatura, radiación, etc.) mediante mapas, métricas y series temporales utilizando datos ERA5. El proyecto inicia con notebooks en Jupyter y evoluciona hacia una Web-app modular preparada para ejecutarse en producción.

## Características Principales
- **Interconectividad de componentes**: Selección de una región en el mapa para cambiar los gráficos automáticamente (asíncrono).
- **Procesamiento optimizado**: Uso de `xarray` y `pandas` para consultas eficientes.
- **Separación de responsabilidades**: Separar los cálculos matemáticos pesados de la parte visual de la pantalla.

---

## *Plan a seguir*

### Bloque 1: Pizarra Inicial & Configuración
- [ ] **Configurar el entorno de desarrollo y estructura**
  - [ ] Diseñar y crear la estructura de carpetas del proyecto.
  - [ ] Configurar el entorno virtual e instalar dependencias (`shiny`, `xarray`, `pandas`, `matplotlib`/`plotly`).

---

### Paso 1: Validación y Lógica en Notebooks
*Objetivo: Validar los datos climáticos crudos de forma iterativa antes de construir la aplicación.*

- [ ] **Exploración e Investigación de Datos (ERA5)**
  - [ ] Leer archivos NetCDF (`.nc`).
  - [ ] Explorar variables disponibles y analizar dimensiones del dataset.
  - [ ] Validar unidades y limpiar datos crudos.
  - [ ] Diseñar y probar algoritmos independientes para conversión de variables (temperatura y radiación) y zonas horarias.
- [ ] **Prototipado Local**
  - [ ] Construir prototipos visuales en gráficas para validación matemática y coherente inmediata.
  - [ ] Documentar hallazgos sobre elcomportamiento.

---

### Paso 2: Abstracción y Creación de Funciones Puras
*Objetivo: Romper funciones mixtas en componentes reutilizables e implementar la abstracción espacial.*

- [ ] **Capa de Datos y Abstracción Espacial**
  - [ ] Implementar la transición de municipios/estados a mallas continuas utilizando `xarray` (interactivo).
  - [ ] Indexar el dataset por coordenadas geoespaciales para consultas regionales eficientes con interpolación (si es la mejor opción).
- [ ] **Funciones de Procesamiento**
  - [ ] Crear función base parametrizada de carga, filtros y conversión de datos como: (`cargar_datos()`, `seleccionar_variable()...`).
  - [ ] Desarrollar funciones para resumir datos por dia, mes o año:
    - [ ] `temperatura_promedio_anual()`
    - [ ] `temperatura_promedio_maxima_diaria()`
    - [ ] `temperatura_promedio_minima_diaria()`
- [ ] **Funciones de Visualización**
  - [ ] Diseñar la función de mapa de forma modular, asegurando que escale desde municipios hasta estados y el nivel nacional
  - [ ] Crear gráficos dinámicos que se adapten automáticamente según la escala seleccionada (municipio, estado o país).

---

### Paso 3: Ensamble en Shiny for Python
*Objetivo: Construir la aplicación web interactiva utilizando una arquitectura reactiva, modular y optimizada para producción.*

- [ ] **Diseño de la interfaz de usuario (UI) y distribución de componentes.**
  - [ ] Diseñar la barra lateral (Sidebar) con selectores dinámicos (año, variable, municipio/estado).
  - [ ] Diseñar el panel principal (Layout para mapa y sección de gráficos).
- [ ] **Desarrollo de Módulos Independientes**
  - [ ] Desarrollar el componente de la barra lateral para el control de parámetros dinámicos.
  - [ ] Separar la lógica del mapa para que solo se encargue de detectar el lugar seleccionado.
  - [ ] Hacer que los gráficos y las estadísticas se actualicen automáticamente al cambiar de zona o escala.
- [ ] **Interactividad Reactiva y Optimización Web**
  - [ ] Hacer que el mapa envíe los datos a las gráficas en el fondo para evitar que el sistema se trabe.
  - [ ] Configurar renderizado del lado del cliente para gráficos ligeros.
  - [ ] Implementar mecanismos de caché y consultas optimizadas para reducir uso de memoria.

---

### Paso 4: Infraestructura y Persistencia de Datos
*Objetivo: Unificar el backend en una base de datos estable con mecanismos automáticos de importación y actualización de datos*

- [ ] **Actualización Automática de Datos**
  - [ ] Programar un script automático que reciba, valide y anexe nuevos archivos NetCDF.
  - [ ] Implementar lógica de detección para anexado temporal (nuevas fechas) o extensión de malla (nuevas coordenadas).
- [ ] **Preparación de Servidor y Despliegue**
  - [ ] Preparar los archivos finales para que la pantalla los cargue rápido y solo lea los datos necesarios en cada clic (Lazy Loading).
  - [ ] Implementar un panel de control para registrar fallas, vigilar la velocidad y gestionar el acceso simultáneo de múltiples usuarios.
- [ ] **Aseguramiento de Calidad y Cierre**
  - [ ] Escribir pruebas unitarias (Tests) para las funciones puras de procesamiento.
---
> **Nota de Cierre de Proyecto**
> - [ ] Redactar la documentación técnica del repositorio y ejecutar el Deploy.

## Tecnologías Utilizadas
- **Lenguaje:** Python
- **Framework Web:** Shiny for Python
- **Procesamiento de Datos:** Xarray, Pandas
- **Visualización:** Matplotlib/Plotly
- **Formatos de Datos:** NetCDF (.nc) / Datos Climáticos ERA5

## Autor
- **Esmeralda Morales Martínez** 
