```{image} chd_logo.png
:width: 400px
:align: center
```

# Ciencia de Datos Hidrometeorológicos con Python

[![nightly-build](https://github.com/ProjectPythia/AtmosCol-2023/actions/workflows/nightly-build.yaml/badge.svg)](https://github.com/ProjectPythia/AtmosCol-2023/actions/workflows/nightly-build.yaml)
[![Binder](https://binder.projectpythia.org/badge_logo.svg)](https://binder.projectpythia.org/v2/gh/ProjectPythia/AtmosCol-2023/main?labpath=notebooks)
[![DOI](https://zenodo.org/badge/686482876.svg)](https://zenodo.org/doi/10.5281/zenodo.8316796)

---

Este libro interactivo forma parte del ecosistema de Pythia Cookbooks, y está orientado a la enseñanza, exploración y divulgación del análisis de datos hidrometeorológicos mediante Python.

El contenido nace a partir del taller AtmosCol 2023, pero ha sido reorganizado como un recurso didáctico, abierto y reproducible que puede ser consultado y reutilizado por estudiantes, docentes, investigadores y cualquier persona interesada en los datos del clima y el ambiente.

Este libro refleja los principios de la ciencia abierta, promoviendo:

- 📖 Accesibilidad al conocimiento: todo el contenido es libre, interactivo y ejecutable en la nube o localmente.
- 🧪 Reproducibilidad científica: los ejemplos están basados en datos reales y pueden ser replicados paso a paso.
- 🤝 Inclusión y equidad: dirigido a públicos diversos, con énfasis en el contexto de América Latina y el acceso a datos locales.
- 🌐 Colaboración abierta: el código y los notebooks pueden ser adaptados, reutilizados o ampliados por la comunidad.


---

## 🎯 Objetivos

- Introducir al lector en el análisis de datos climáticos e hidrometeorológicos usando Python
- Usar herramientas de código abierto como `xarray`, `pyart`, `pandas`, `cartopy`, `hvplot` y más
- Acceder a datos reales de estaciones IDEAM, radares meteorológicos, GFS, OPENDAP y modelos CMIP
- Aplicar conceptos de ciencia abierta y reproducibilidad
- Analizar fenómenos climáticos como El ENOS (El Niño-Oscilación del Sur, o ENSO en sus siglas en inglés) y visualizar escenarios de cambio climático

---

## 📚 Estructura del libro

El contenido está organizado en capítulos temáticos, cada uno representado por notebooks interactivos:

1. **Fundamentos**  
   Introducción al ecosistema científico de Python, estructuras de datos, visualización, y herramientas para trabajar con datos multidimensionales.

2. **Aplicaciones regionales**  
   Casos de estudio con datos hidrometeorológicos de Colombia: estaciones del IDEAM, radares meteorológicos, y uso de modelos globales (GFS).

3. **Fenómenos climáticos**  
   Cálculo de anomalías relacionadas con el fenómeno ENOS en el Pacífico Tropical.

4. **Cambio climático**
   Visualización de datos de modelos climáticos globales (CMIP) y reproducción de gráficas del IPCC sobre aumento de temperatura.

---

## 🧑‍🏫 Público objetivo

- Estudiantes de pregrado o posgrado en ciencias ambientales, físicas o computacionales
- Docentes y educadores que deseen introducir análisis de datos climáticos en sus cursos
- Investigadores interesados en reproducibilidad y ciencia abierta
- Profesionales de instituciones ambientales o meteorológicas en América Latina

---

## 🚀 Cómo ejecutar los notebooks

### 🔗 En Binder (recomendado)

Haz clic en el ícono de Binder arriba o visita:

👉 [Ejecutar en Binder](https://binder.projectpythia.org/v2/gh/ProjectPythia/AtmosCol-2023/main?labpath=notebooks)

Esto abrirá una versión ejecutable del libro en la nube (Jupyter Lab).

---

### 🖥️ Ejecutar este libro localmente

Si estás interesado en ejecutar este material en tu computadora, sigue el siguiente flujo de trabajo:

1. Clona el repositorio desde GitHub:

   ```bash
    git clone https://github.com/ProjectPythia/AtmosCol-2023
   ```

1. Entra en la carpeta del proyecto:
   ```bash
   cd Atmoscol2023
   ```
1. Crea y activa tu ambiente de desarrollo usando el archivo environment.yml:
   ```bash
   conda env create -f environment.yml
   conda activate cdh-python
   ```
1. Vaya a la carpeta `notebooks` y comience una sesión de `Jupyterlab`
   ```bash
   cd notebooks/
   jupyter lab
   ```
