# Análisis Vial — Simulación de Cruce Intersección 03

Simulación multiagente del cruce vial **Av. Fernando García Roel / Ahuehuetes / Nogales** (Intersección 03, Monterrey). El proyecto modela el flujo vehicular y el control semafórico usando programación orientada a agentes con datos de campo reales.

## Descripción

La intersección modelada tiene forma de Y: una vía diagonal (Fernando García Roel) que se bifurca en dos ramales (Ahuehuetes al NW y Nogales al NE). Los accesos modelados son W, E, NW y NE.

El proyecto tiene dos versiones de simulación:

- **Cruce Básico** — Intersección sin semáforos. Modela llegadas de vehículos con distribución de Poisson, geometría real del cruce con splines cúbicos, y detección de colisiones con polígonos cápsula.
- **Cruce Semafórico v1** — Agrega control de semáforo de 4 fases con tiempos configurables. Incluye recolección de métricas: throughput, longitudes de cola, tiempos de espera y eficiencia por fase.

## Estructura

```
analisis-vial/
├── data/raw/          # Aforos vehiculares reales (mañana, mediodía, tarde)
├── docs/              # Croquis de la intersección (PDF y DOCX)
├── notebooks/         # Simulaciones en Jupyter
├── src/               # Código fuente (en desarrollo)
└── tests/             # Pruebas (en desarrollo)
```

## Requisitos

```bash
pip install agentpy numpy scipy matplotlib seaborn pandas networkx
```

## Uso

```bash
source venv/bin/activate
jupyter notebook notebooks/
```

Abrir el notebook correspondiente:
- `Tarea_Cruce_Basico_CORREGIDO.ipynb` — modelo sin semáforo
- `Cruce_Semafórico_Version_1.ipynb` — modelo con control semafórico

## Datos

`data/raw/` contiene aforos vehiculares de la Intersección 03 en tres periodos del día (Excel). Estos datos empíricos se usan para calibrar y validar las tasas de llegada del modelo.

## Contribución

Ver [CONTRIBUTING.md](CONTRIBUTING.md) para el flujo de trabajo con Git, convenciones de commits y proceso de pull requests.
