# ED-Alert: Detección temprana del riesgo de abandono escolar

Análisis del riesgo de abandono escolar temprano en España a partir de los datos de PISA 2022, combinando técnicas de análisis exploratorio, reducción de dimensionalidad y modelos de clasificación supervisada.

## Estructura del proyecto

```
ED-Alert/
├── data/                          # Datos procesados
│   ├── 01_pisa_preprocessed.csv   # Dataset PISA preprocesado
│   ├── 01_pisa_mca.csv            # Coordenadas MCA por alumno
│   ├── 01_pisa_importancia_rf.csv # Importancia de variables (Random Forest)
│   ├── 02_ministerio_abandono_fp_ccaa.csv
│   ├── 03_elet.csv                # Datos ELET por comunidad autónoma
│   └── rend_2_*.csv               # Rendimiento por centro
└── src/                           # Notebooks de análisis
    ├── 00_pisa_preprocess.ipynb   # Preprocesado del dataset PISA 2022
    ├── 00_ministerio_preprocessed.ipynb
    ├── 00_elet_preprocessed.ipynb
    └── 01_pisa_ml.ipynb           # MCA + Regresión Logística + Random Forest
```

## Datos

El archivo fuente de PISA 2022 (`CY08MSP_STU_QQQ.SAV`, ~2GB) no está incluido en el repositorio por su tamaño. Puede descargarse desde el sitio oficial de la OCDE:
[https://www.oecd.org/pisa/data/2022database/](https://www.oecd.org/pisa/data/2022database/)

## Análisis

- **Preprocesado**: limpieza, selección de variables y construcción de la variable objetivo `en_riesgo` a partir del rendimiento académico en las tres competencias PISA.
- **MCA** (Análisis de Correspondencias Múltiples): reducción de dimensionalidad sobre variables categóricas de contexto socioeconómico y escolar.
- **Regresión Logística**: modelo interpretable con recall del 60% en la clase de riesgo.
- **Random Forest**: modelo con accuracy global del 81% y recall del 64% en la clase de riesgo.

## Requisitos

```bash
pip install pandas numpy matplotlib seaborn scikit-learn prince sidetable
```

## Autor

Jordi Sanjuán Jover — jsanjuanj@uoc.edu  
Universitat Oberta de Catalunya (UOC)
