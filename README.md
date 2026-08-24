# 🤝 Matriz Concurrente de Acuerdos

Una aplicación web interactiva diseñada para resolver desacuerdos y tomar decisiones complejas en pareja de forma objetiva, cuantitativa y empática, utilizando un modelo adaptado de la **Matriz de Decisión Ponderada**.

---

## 📌 Visión del Proyecto

En las relaciones de pareja, las decisiones importantes o los desacuerdos cotidianos suelen abordarse desde esquemas de discusión tradicionales donde una parte "gana" y la otra "cede", lo que puede generar desgaste o fricción acumulada. 

**Matriz Concurrente de Acuerdos** cambia el enfoque de un modelo *Ganar / Perder* a uno de **Optimización e Integración de Necesidades Mutuas**. La aplicación no busca determinar quién tiene "razón", sino calcular la alternativa que maximiza el bienestar común y minimiza la brecha de insatisfacción entre ambas partes.

---

## 🎯 Características Principales

* **Definición Neutral del Escenario:** Marco de trabajo para describir el problema de forma objetiva sin juicios de valor.
* **Evaluación Simultánea y Ponderada:** Cada integrante asigna un peso de importancia ($1$ a $5$) a los criterios relevantes desde su propia perspectiva.
* **Algoritmo de Minimización de Fricción:** Cálculo automático que evalúa las opciones considerando tanto la puntuación total como el índice de discrepancia ($\vert{}S_1 - S_2\vert{}$).
* **Análisis Estadístico e Visual:** Identificación clara del punto de equilibrio óptimo para ambas partes.
* **Historial de Acuerdos:** Registro de resoluciones pasadas para consulta y seguimiento de compromisos.

---

## 🧮 Funcionamiento del Algoritmo

Para cada alternativa $k$, el sistema calcula la puntuación ponderada individual para cada integrante ($S_1$ y $S_2$):

$$S_1^{(k)} = \sum_{i=1}^{n} (W_{1,i} \times P_{k,i})$$

$$S_2^{(k)} = \sum_{i=1}^{n} (W_{2,i} \times P_{k,i})$$

Donde:
* $W_{1,i}, W_{2,i}$: Peso asignado al criterio $i$ por cada integrante ($1$ a $5$).
* $P_{k,i}$: Calificación objetiva de la opción $k$ en el criterio $i$ ($1$ a $5$).

Posteriormente, se determina el **Índice de Balance Global ($B_k$)**:

$$B_k = (S_1^{(k)} + S_2^{(k)}) - \alpha \cdot \vert{}S_1^{(k)} - S_2^{(k)}\vert{}$$

* **Factor de Penalización de Fricción ($\alpha = 1.5$):** Penaliza las opciones donde una de las partes queda significativamente menos satisfecha que la otra, priorizando así el consenso sobre la imposición.

---

## 🚀 Estructura del Proyecto

```text
matriz-acuerdos-pareja/
├── .github/
│   └── workflows/          # Workflows para despliegue continuo (GitHub Actions)
├── public/                 # Archivos estáticos y favicon
├── src/
│   ├── components/         # Componentes de la UI (Formularios, Tablas, Gráficos)
│   ├── hooks/              # Hooks personalizados para gestión de estado
│   ├── utils/              # Motor de cálculo (decisionEngine.js)
│   ├── App.jsx             # Punto de entrada principal
│   └── main.jsx            # Renderizado React
├── .gitignore
├── package.json
└── README.md               # Documentación del repositorio
