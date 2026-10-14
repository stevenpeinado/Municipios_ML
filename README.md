# Análisis de similitud entre municipios colombianos 🇨🇴

Proyecto desarrollado para la asignatura **Fundamentos de Machine Learning**, enfocado en representación de datos, espacios métricos y técnicas de aprendizaje no supervisado.

El objetivo es representar municipios colombianos mediante diferentes características demográficas, socioeconómicas, educativas, ambientales, turísticas, institucionales y de seguridad, con el fin de identificar municipios similares y explorar agrupaciones con características comunes.

## Objetivo

Responder a la pregunta:

> **¿Qué municipios presentan condiciones similares para vivir y desarrollarse, considerando conjuntamente diferentes dimensiones territoriales?**

Para ello, cada municipio se representa mediante un conjunto de variables numéricas y se utilizan distancias y técnicas de clustering para estudiar su similitud.

## Datos

El análisis parte de una base con **200 municipios colombianos** y diferentes indicadores municipales.

La base de datos incluida en este repositorio **no corresponde a una base oficial consolidada publicada por una única entidad**.

Fue construida específicamente para este proyecto mediante la integración y procesamiento de información proveniente de diferentes fuentes institucionales y públicas.

Entre las fuentes utilizadas se encuentran entidades y sistemas de información relacionados con:

- Departamento Nacional de Planeación (DNP)
- Ministerio de Educación Nacional
- Ministerio TIC
- Policía Nacional
- Ministerio de Comercio, Industria y Turismo
- Información climática de NASA POWER

El archivo `base_municipios_colombia_ml.xlsx` incluye hojas adicionales con:

- diccionario de variables;
- fuentes utilizadas;
- información sobre calidad de los datos;
- base final integrada.

### Diferentes períodos de referencia

Los indicadores no pertenecen todos al mismo año debido a que la disponibilidad de información municipal varía según la fuente.

Por esta razón, el proyecto **no busca representar una fotografía exacta de Colombia en un único año**, sino construir un perfil multidimensional reciente de los municipios utilizando la información disponible.

Esta diferencia temporal debe considerarse como una limitación del análisis y los resultados no deben interpretarse como relaciones causales entre las variables.

## Metodología

Para el análisis se seleccionaron **18 variables** relacionadas con diferentes dimensiones territoriales.

El flujo general del proyecto es:

1. Integración y revisión de los datos.
2. Análisis exploratorio.
3. Selección de variables para representar cada municipio.
4. Estandarización mediante `StandardScaler`.
5. Construcción del espacio de características.
6. Cálculo de similitud mediante distancias Euclidiana y Manhattan.
7. Identificación de municipios vecinos.
8. Clustering jerárquico.
9. K-Means.
10. Evaluación mediante silhouette y análisis de los grupos obtenidos.
11. PCA como herramienta de visualización.
12. Explorador interactivo de municipios.

La posición geográfica (latitud y longitud) no se utiliza para determinar la similitud. Por lo tanto, dos municipios pueden considerarse cercanos dentro del espacio de características aunque estén geográficamente alejados.

## Espacios métricos

Cada municipio se representa como un vector de características:

\[
x = (x_1, x_2, \dots, x_{18})
\]

Después de estandarizar las variables, se utilizan principalmente dos métricas.

### Distancia Euclidiana

\[
d(x,y)=\sqrt{\sum_{i=1}^{n}(x_i-y_i)^2}
\]

### Distancia Manhattan

\[
d(x,y)=\sum_{i=1}^{n}|x_i-y_i|
\]

Los municipios con menor distancia presentan perfiles más similares considerando conjuntamente las variables seleccionadas.

## Clustering

Además de buscar municipios similares individualmente, se utilizan dos métodos de agrupamiento:

- **Clustering jerárquico**, acompañado de dendrogramas para estudiar la estructura de agrupación.
- **K-Means**, utilizando criterios como el método del codo y el coeficiente silhouette para analizar el número de grupos.

Los clusters obtenidos son descriptivos y dependen de las variables, transformaciones y métricas utilizadas.

## Explorador interactivo

El notebook incluye una interfaz desarrollada con **Gradio** que permite seleccionar un municipio y explorar:

- municipios más similares;
- distancia entre municipios;
- comparación de características;
- variables que explican principalmente la distancia;
- cluster al que pertenece el municipio.

La interfaz funciona como una capa de exploración sobre los resultados del análisis y no modifica los modelos utilizados.

## Reproducibilidad

La base utilizada por el notebook se encuentra en este mismo repositorio.

El notebook puede cargarla directamente desde GitHub, evitando que sea necesario subir archivos manualmente al entorno de ejecución.

Esto permite reproducir el análisis ejecutando las celdas del notebook en orden.

## Tecnologías

El proyecto utiliza principalmente:

- Python
- Pandas
- NumPy
- Scikit-learn
- SciPy
- Matplotlib
- Seaborn
- Gradio
- Google Colab

## Limitaciones

Los resultados deben interpretarse teniendo en cuenta que:

- los indicadores provienen de diferentes años;
- algunas variables pueden estar correlacionadas;
- la selección de variables determina qué significa que dos municipios sean "similares";
- la estandarización reduce los problemas asociados a diferentes escalas, pero los valores extremos siguen teniendo influencia;
- los clusters representan patrones estadísticos y no categorías oficiales de municipios;
- el análisis es exploratorio y no busca establecer relaciones causales.

## Estructura del repositorio

```text
Municipios_ML/
│
├── base_municipios_colombia_ml.xlsx
├── Taller_municipios_espacios_metricos_clustering_GRADIO.ipynb
└── README.md
```

## Uso académico

Este repositorio contiene el desarrollo de un proyecto académico de **Fundamentos de Machine Learning**.

La integración de los datos, las decisiones metodológicas y las interpretaciones realizadas corresponden al contexto y objetivos de este proyecto. Para utilizar los datos fuera de este contexto se recomienda consultar las fuentes originales documentadas dentro del archivo de datos.

---

**Autor:** Steven Peinado  
**Proyecto académico — Fundamentos de Machine Learning**
