<div align="center">
  <img src="assets/Parche_Zipa_Logo.png" alt="Parche Zipa" width="180">

  # Parche Zipa · Plan de Acción CCyD 2026

  **Tablero ejecutivo interactivo para el seguimiento del Plan de Acción 2026**
  de la Comisión de Concertación y Decisión Juvenil (CCyD) de Zipaquirá.

  Un solo archivo HTML autónomo · sin servidor · con análisis por IA.
</div>

---

## ¿Qué es esto?

Un dashboard de **6 páginas** que lee la matriz del Plan de Acción 2026 e interpreta automáticamente la columna *"Descripción de Acciones Realizadas"* para mostrar avances, riesgos y recomendaciones por objetivo, dependencia e indicador. Estética **Parche Zipa**: sticker callejero, amarillo intenso, verde neón, bordes negros gruesos. Nada institucional.

Todo vive en `index.html`: estilos, lógica y datos están embebidos. No necesita instalación, backend ni base de datos.

## Vistas

| Página | Contenido |
|--------|-----------|
| **Resumen Ejecutivo** | Panel IA, 6 KPIs animados, barra de estado, dona por dependencia, barras por objetivo, mini cronograma con marcador de HOY. |
| **Por Objetivos** | Acordeón ordenado por avance promedio, con dependencias, lectura IA y tabla de actividades. |
| **Por Dependencias** | Ranking horizontal + acordeón por dependencia con conclusión IA y tabla. |
| **Indicadores** | Una tarjeta por acción (25): métricas de cumplimiento/impacto/riesgo, semáforo, análisis IA y botón *Profundizar IA*. |
| **Cronograma** | Gantt con barras coloreadas por avance y línea de HOY. |
| **Narrativa IA** | Respuesta narrativa a las 8 preguntas clave de seguimiento. |

## Las dos capas de IA

1. **IA en vivo (⚡)** — Dentro del entorno de artefactos de **Claude.ai**, cada panel llama a Claude y reinterpreta *solo los datos filtrados* en cada cambio de filtro.
2. **Análisis automático (◆)** — Fuera de Claude (en GitHub Pages, tu PC o por correo) la IA en vivo no está disponible, así que entra un **motor heurístico** que clasifica cada acción en *Avance Alto / Medio / Bajo / Sin registro* usando la relación ejecución/meta, la densidad de palabras clave y la evidencia textual. **Siempre hay análisis, nunca queda vacío.**

> Al publicar en GitHub Pages funcionará en modo **Análisis automático (◆)**, que es completo y no requiere conexión a ninguna API.

## 🔒 Carga de Excel oculta (solo para la persona responsable)

La opción para actualizar los datos está oculta al público y se abre de dos formas:

- **Punto-rayo tenue** abajo del menú lateral (casi invisible) → clic.
- Atajo de teclado **`Ctrl + Shift + U`**.

Se arrastra el `.xlsx` actualizado; se lee con SheetJS (busca la hoja *"Plan"* y la fila de encabezado), y los datos se guardan en el navegador (`localStorage`) para que persistan. El botón **"Restaurar datos originales"** vuelve a la matriz de partida.

## Sobre los datos

La matriz original **no trae columna "Línea Estratégica" ni "Estado"** explícitas. Para no inventar dimensiones, se usa el **Objetivo como línea estratégica** (el filtro dice *"Objetivo / Línea"*) y el avance se calcula con la relación ejecución/meta más la evidencia del texto. Si más adelante agregas esas columnas al Excel, el tablero se puede ajustar.

El archivo fuente está en [`data/Plan_Accion_Juventud_2026.xlsx`](data/Plan_Accion_Juventud_2026.xlsx).

## Cómo verlo

- **En línea:** publícalo en GitHub Pages (ver [`docs/DESPLIEGUE.md`](docs/DESPLIEGUE.md)).
- **Local:** abre `index.html` con doble clic en cualquier navegador moderno.

## Tecnologías

HTML/CSS/JS puro · [Chart.js](https://www.chartjs.org/) · [SheetJS](https://sheetjs.com/) · [Poppins](https://fonts.google.com/specimen/Poppins) · API de Claude (capa IA en vivo, opcional).

## Estructura

```
parche-zipa-dashboard/
├── index.html                      # El tablero (archivo único autónomo)
├── assets/
│   └── Parche_Zipa_Logo.png        # Logo de marca
├── data/
│   └── Plan_Accion_Juventud_2026.xlsx   # Matriz fuente
├── docs/
│   ├── DESPLIEGUE.md               # Guía paso a paso de publicación
│   └── POWERBI.md                  # Complemento: medidas DAX + prompts Copilot
├── README.md
├── LICENSE
└── .nojekyll
```

## Licencia

Distribuido bajo licencia MIT. Ver [`LICENSE`](LICENSE).

---

<div align="center"><sub>Hecho para la CCyD de Zipaquirá · Plan de Acción Juventud 2026</sub></div>
