# Planificación: Modelo Multiagente de Cruce Semafórico

## Descripción del Problema

Implementar un pequeño modelo multiagente que simule un cruce semafórico asignado al equipo.
Los agentes son vehículos que entran por al menos dos entradas del cruce, avanzan paso a paso y desaparecen al salir. Por ahora **no se consideran semáforos**.

---

## Estructura del Entorno

### Representación del Cruce
- Cuadrícula bidimensional (grid) que modela el cruce asignado al equipo.
- Se distinguen dos zonas:
  - **Calles**: carriles de entrada y salida al cruce.
  - **Zona de intersección**: área central donde convergen los carriles.

### Entradas y Salidas
- Al menos **dos entradas** por donde aparecen vehículos.
- Salidas correspondientes por donde los vehículos desaparecen del modelo.

---

## Agentes (Vehículos)

### Atributos
| Atributo | Tipo | Descripción |
|---|---|---|
| `pos` | `(int, int)` | Posición bidimensional en el grid |
| `direction` | `str` | Dirección de movimiento: `N`, `S`, `E`, `O` |
| `state` | `str` | Estado del agente: `moving` o `static` |

### Ciclo de Vida
1. **Aparición**: se genera en una celda de entrada con dirección asignada.
2. **Avance**: se mueve paso a paso una celda por turno en su dirección.
3. **Desaparición**: al llegar a una celda de salida, el agente se elimina del modelo.

---

## Reglas de Movimiento y Colisión

1. Un vehículo en estado `moving` avanza una celda por paso de simulación.
2. Si la celda destino está ocupada por otro vehículo, el agente cambia a estado `static` (espera).
3. Un agente `static` pasa a `moving` en cuanto la celda destino quede libre.
4. No pueden existir dos vehículos en la misma celda simultáneamente.
5. Dentro de la zona de intersección se aplican las mismas reglas de colisión.

---

## Plan de Implementación

### Fase 1 — Entorno
- [ ] Definir la clase `Cruce` (grid + zonas).
- [ ] Marcar celdas de entrada, salida e intersección.
- [ ] Método de visualización básica (texto o matplotlib).

### Fase 2 — Agentes
- [ ] Definir la clase `Vehiculo` con atributos `pos`, `direction`, `state`.
- [ ] Implementar método `step()`: lógica de avance y detección de colisión.
- [ ] Lógica de aparición en entradas y desaparición en salidas.

### Fase 3 — Simulación
- [ ] Bucle principal que avanza el tiempo (ticks).
- [ ] Generación aleatoria de vehículos en las entradas cada N pasos.
- [ ] Registro de métricas básicas (número de vehículos activos, ticks totales).

### Fase 4 — Validación y Ajuste
- [ ] Verificar que no hay colisiones simultáneas.
- [ ] Ajustar la representación del cruce al cruce específico asignado al equipo.
- [ ] Documentar el notebook con markdown explicativo.

---

## Tecnologías Sugeridas
- **Python** con `mesa` (framework multiagente) o implementación propia con clases.
- `matplotlib` para visualización del grid.
- Jupyter Notebook como entorno de desarrollo y presentación.

---

## Notas
- Los semáforos **no** se implementan en esta fase.
- El cruce concreto se adaptará según la asignación del equipo.
- El código de producción deberá refactorizarse a `src/` una vez estabilizado.
