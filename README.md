# 4-Coloreo Planar — Editor + log en tiempo real (v8)

> SPA en un solo archivo HTML para **dibujar grafos planares**, **colorearlos con 4 colores** mediante backtracking y **visualizar el log de búsqueda** del algoritmo en tiempo real.

![Estado](https://img.shields.io/badge/versión-v8-0ea5e9)
![Sin dependencias](https://img.shields.io/badge/dependencias-ninguna-16a34a)
![HTML5](https://img.shields.io/badge/stack-HTML5%20%2B%20Canvas%20%2B%20SVG-f59e0b)
![Licencia](https://img.shields.io/badge/licencia-PolyForm%20Noncommercial%201.0.0-blue)

---

## ¿Qué es?

Una aplicación de página única (Single Page Application) que integra tres sistemas en un mismo lienzo educativo, pensada para entender de forma visual e interactiva cómo funciona el **Teorema de los Cuatro Colores** y la **búsqueda con backtracking** en problemas de satisfacción de restricciones (CSP).

Todo corre en el navegador, sin servidor, sin build y sin librerías externas: basta abrir el archivo `.html`.

## Características principales

### 1. Editor de grafos planares
- Dibujo manual de vértices y aristas sobre un canvas HTML5.
- Ajuste (*snap*) a una cuadrícula de doble resolución (`GRID_SIZE` y `GRID_SIZE/2`).
- **Restricción de planaridad en tiempo real**: impide crear aristas que crucen a otras existentes.
- Arrastre de vértices conservando la planaridad del grafo.
- Importación y exportación del grafo en formato **JSON** por archivo.

### 2. Algoritmo de 4-coloreo con backtracking
- Cálculo de **capas** (*layers*) por eliminación iterativa de la cara exterior.
- Triangulación del grafo con aristas virtuales punteadas (*ear clipping*).
- Selección del triángulo más interno como núcleo inicial (colores 1, 2 y 3).
- Búsqueda en profundidad (DFS) con heurísticas y poda:
  - **MRV** (Minimum Remaining Values) para elegir el siguiente vértice.
  - **LCV** (Least Constraining Value) para ordenar los colores candidatos.
  - **Forward Checking** para detectar dominios vacíos antes de explorar.
- **Control manual paso a paso**: el usuario avanza y retrocede cada decisión.

## Cómo usarlo

No requiere instalación ni dependencias.

1. Clona o descarga el repositorio.
2. Abre `Planar_v8.html` directamente en cualquier navegador moderno (Chrome, Firefox, Edge, Safari).

```bash
git clone https://github.com/<usuario>/<repositorio>.git
cd <repositorio>
# Abre el archivo con tu navegador, por ejemplo:
xdg-open Planar_v8.html     # Linux
open Planar_v8.html         # macOS
start Planar_v8.html        # Windows
```

## Flujo de trabajo sugerido

1. **Modo: Vértices** → coloca los nodos en el lienzo.
2. **Modo: Aristas** → conecta nodos (las aristas que crucen serán rechazadas).
3. **Modo: Borrar** → elimina vértices o aristas; o usa **Borrar grafo** para empezar de cero.
4. **Calcular Layers** → genera las capas del grafo.
5. **Iniciar búsqueda** → arranca el backtracking.
6. **Siguiente paso / Paso anterior** → recorre cada decisión del algoritmo.
7. Haz clic en los nodos del **árbol de búsqueda** para inspeccionar cualquier estado.

Puedes guardar tu trabajo con **Exportar JSON** y recuperarlo con **Importar JSON**.

## Controles de la interfaz

| Botón | Función |
|-------|---------|
| Modo: Vértices | Añadir nodos al grafo |
| Modo: Aristas | Conectar nodos (con verificación de planaridad) |
| Modo: Borrar | Eliminar vértices o aristas |
| Borrar grafo | Vaciar el lienzo por completo |
| Importar / Exportar JSON | Cargar o guardar el grafo en archivo |
| Calcular Layers | Generar las capas por cara exterior |
| Iniciar búsqueda | Comenzar el coloreo con backtracking |
| Paso anterior / Siguiente paso | Avanzar y retroceder en la ejecución |

## Stack técnico

- **HTML5 + Canvas** para el editor de grafos.
- **SVG** para el árbol de búsqueda.
- **JavaScript** puro (*vanilla*), sin frameworks ni dependencias.
- Arquitectura de **variables CSS globales** (`:root`) leídas también desde JS con `getComputedStyle()`.
- Persistencia del grafo vía **JSON**.

## Conceptos que ilustra

- Teorema de los Cuatro Colores y coloreo de grafos planares.
- Problemas de satisfacción de restricciones (CSP).
- Backtracking, heurísticas MRV/LCV y forward checking.
- Triangulación de polígonos por *ear clipping*.

## Licencia

Distribuido bajo la licencia **PolyForm Noncommercial 1.0.0**. Su uso está permitido únicamente con **fines no comerciales** (por ejemplo, uso personal, educativo, académico o de investigación). Consulta el archivo `LICENSE` y el texto completo en [polyformproject.org/licenses/noncommercial/1.0.0](https://polyformproject.org/licenses/noncommercial/1.0.0/) para más detalles.
